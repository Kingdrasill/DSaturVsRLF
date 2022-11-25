# DSatur VS Recusive Largest First(RLF)

O objetivo da implementação desse algoritmo é de realizar a comparação de dois modos diferentes para se realizar a coloração de Grafos sendo esses dois algoritmos o DSatur e o RLF, e analisar se os mesmo sao bons algoritmos para resolver Sudokus.

# DSatur

DSatur é um algoritmo usado para a coloração de grafos que foi inicialmente apresentado por Daniel Brélaz em 1979, o DSatur é similiar ao algoritmo de coloração guloso, colorindo um vertice do grafo um após o outro, adicionando uma cor não usada anteriormente quando necessário. Uma vez que um novo vértice foi colorido, o algoritmo determina qual dos vértices não coloridos restantes tem o maior número de cores em sua vizinhança e colore esse vértice a seguir.

### Pseudocódigo DSatur
<ol>
<li>Deixar <i>V</i> ser o vértice não colorido em <i>G</i> com o maior grau de saturação. Em casos de empates, escolha o vértice dentre estes de maior grau no subgrafo induzido pelos vértices incolores.</l1>

<li>Atribuir <i>V</i> para o rótulo de cor mais baixo não sendo usado por nenhum de seus vizinhos.</l1>

<li>Se todos os vértices foram coloridos, end; caso contrário, retorne ao Passo 1.</l1>
</ol>

# Recursive Largest First (RLF)
O algoritmo Recursive Largest First é uma heurística para o problema de coloração de grafos NP-difícil . Foi originalmente proposto por Frank Leighton em 1979.

O algoritmo RLF atribui cores aos vértices de um grafo construindo cada classe de cor uma de cada vez. Ele faz isso identificando um conjunto independente máximo de vértices no gráfico, atribuindo-os à mesma cor e, em seguida, removendo esses vértices do gráfico. Essas ações são repetidas no subgrafo restante até que nenhum vértice permaneça.

### Pseudocódigo RLF
O algoritmo pode ser descrito pelas três etapas a seguir. Ao final desse processo, <i>S</i> dá uma partição dos vértices que representam um viável |<i>S</i>| -coloração do gráfico <i>G</i>.

<ol>
<li>Deixar <i>S = 0</i> ser uma solução vazia. Além disso, deixe <i>G=(V,E)</i> ser o grafo que desejamos colorir, compreendendo um conjunto de vértices <i>V</i> e um conjunto de arestas <i>E</i>.</li>

<li>Identifique um conjunto independente maximal <i> S ⊆ V</i>. Para fazer isso:
<ol>
<li>O primeiro vértice adicionado a <i>S</i> deve ser o vértice em <i>G</i> que tem o maior número de vizinhos.
</li>
<li>
Vértices subseqüentes adicionados a <i>S</i> devem ser escolhidos como aqueles que (a) não são atualmente adjacentes a nenhum vértice em <i>S</i> , e (b) ter um número máximo de vizinhos que são adjacentes aos vértices em <i>S</i>. Os empates na condição (b) podem ser quebrados selecionando o vértice com o número mínimo de vizinhos fora da <i>S</i>. Os vértices são adicionados a <i>S</i> desta forma até que seja impossível adicionar mais vértices.
</li>
</ol>

</li>

<li>Agora definido <i>S = S ∪ {S}</i> e remover os vértices de <i>S</i> a partir de <i>G</i> . Se <i>G</i> ainda contém vértices, então retorne ao Passo 2; caso contrário, terminar.</li>
</ol>

# Exemplo 
Tanto o gráfico DSatur e RLF são gráficos de rodas apresentados pela imagem abaixo
<img src="imgs/img1.jpg">

### Resolução DSatur
A execução do algoritmo resulta na seleção e coloração dos vértices da seguinte forma.

Vértice <i>G</i> (cor 1)
Vértice <i>A</i> (cor 2)
Vértice <i>B</i> (cor 3)
Vértice <i>C</i> (cor 2)
Vértice <i>D</i> (cor 3)
Vértice <i>E</i> (cor 2)
Vértice <i>F</i> (cor 3)

### Resolução RLF
A execução do algoritmo resulta na seleção e coloração dos vértices na seguinte ordem:

Vértice <i>G</i> (cor 1)
Vértice <i>A,C</i>, e depois <i>E</i> (cor 2)
Vértice <i>B,D</i>, e depois <i>F</i> (cor 3)

Isso dá a solução tricolor final <i>S= {{G},{A,C,E},{B,D,F}</i>

# Resultados
Com base na execução, com 100 grafos aleatórios com 30 vértices e 200 arestas, do algoritmo obtivemos os seguintes resultados:

<ol>
<li>O tempo médio na coloração de grafos por meio do algoritmo DSatur foi de 91.64 ms</li>
<li>O tempo médio na coloração de grafos por meio do algoritmo RLF foi de 744.51 ms</li>
</ol>

Tambem foram realizados os teste em resolução de problemas Sudokus 2x2, tanto 3x3, com ambos foram gerados 100 suokus em que no 2x2 havia 2 células com cores e no 3x3 havia 5 células com cores, e os resultados obtidos foram: 

<ol>

<li>Sudokus 2x2 <br>
Tempo medio em microsegundos do algoritmo DSatur: 52
Tempo medio em microsegundos do algoritmo RLF: 315.03

Porcentagem de sudokus resolvidos corretamente pelo DSatur: 73%
Porcentagem de sudokus resolvidos corretamente pelo RLF: 90%
</li>
<li>Sudokus 3x3 <br>
Tempo medio em microsegundos do algoritmo DSatur: 400.28 ms
Tempo medio em microsegundos do algoritmo RLF: 21116.1 ms

Porcentagem de sudokus resolvidos corretamente pelo DSatur: 0%
Porcentagem de sudokus resolvidos corretamente pelo RLF: 55%
</li>
</ol>

| Comando                |  Função                                                                                           |
| -----------------------| ------------------------------------------------------------------------------------------------- |
|  `make clean`          | Apaga a última compilação realizada contida na pasta build                                        |
|  `make`                | Executa a compilação do programa utilizando o gcc, e o resultado vai para a pasta build           |
|  `make run`            | Executa o programa da pasta build após a realização da compilação                                 |
