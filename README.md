Simulador de Busca em Redes P2P Não Estruturadas

## Autores
* Brenno Damiany Castro Vidal - 2315088
* Caio Victor Ferreira Da Silva - 2010224
* Diego Henrique Santos Queiroz - 2315108

Projeto desenvolvido para fins acadêmicos na disciplina de Redes de Computadores / Sistemas Distribuídos.

## Descrição

Este projeto implementa um simulador visual de redes P2P (Peer-to-Peer) não estruturadas, permitindo criar, validar, visualizar e testar diferentes topologias de rede através de quatro algoritmos de busca.

O simulador foi desenvolvido em HTML, CSS e JavaScript puro, funcionando diretamente no navegador sem necessidade de instalação de dependências ou servidores externos.

O objetivo é demonstrar o comportamento de diferentes estratégias de busca distribuída e comparar sua eficiência através de métricas como número de mensagens trocadas e quantidade de nós envolvidos na busca.

---

# Funcionalidades

## Configuração da Rede

O simulador permite criar uma rede P2P a partir de uma configuração em formato YAML simplificado contendo:

* Quantidade de nós (`num_nodes`)
* Número mínimo de vizinhos (`min_neighbors`)
* Número máximo de vizinhos (`max_neighbors`)
* Recursos armazenados em cada nó
* Conexões (arestas) entre os nós

Exemplo:

```yaml
num_nodes: 6
min_neighbors: 2
max_neighbors: 4

resources:
  n1: r1, r2
  n2: r3
  n3: r4, r5
  n4: r6
  n5: r7
  n6: r8, r9

edges:
  n1, n2
  n1, n3
  n2, n4
  n3, n5
  n4, n6
  n5, n6
```

---

## Exemplos Pré-Carregados

O simulador disponibiliza exemplos prontos para testes:

* Small Network
* Medium Network
* Large Network
* Ring Topology
* Star Topology

Esses exemplos permitem analisar o comportamento dos algoritmos em diferentes estruturas de rede.

---

# Validação da Rede

Após clicar em **Carregar e Validar Rede**, o sistema executa automaticamente as seguintes verificações:

| Validação     | Descrição                                                   |
| ------------- | ----------------------------------------------------------- |
| Conectividade | Verifica se a rede não está particionada                    |
| Grau mínimo   | Cada nó deve possuir pelo menos `min_neighbors` vizinhos    |
| Grau máximo   | Cada nó não pode exceder `max_neighbors` vizinhos           |
| Recursos      | Nenhum nó pode ficar sem recursos                           |
| Self-loop     | Não são permitidas arestas de um nó para ele mesmo          |
| Consistência  | `num_nodes` deve corresponder à quantidade de nós definidos |

Caso alguma regra seja violada, o sistema exibe mensagens detalhadas de erro.

---

# Algoritmos de Busca

O simulador implementa quatro algoritmos de busca distribuída.

Todos recebem os seguintes parâmetros:

* Nó de origem
* Recurso desejado
* TTL (Time To Live)
* Algoritmo

---

## Flooding

Propaga a busca para todos os vizinhos possíveis até o TTL ser esgotado.

Características:

* Alta cobertura da rede
* Grande quantidade de mensagens
* Alta probabilidade de localizar recursos

---

## Informed Flooding

Variação do Flooding que utiliza uma estratégia de ordenação dos vizinhos antes da propagação.

Características:

* Mantém ampla cobertura
* Exploração mais direcionada
* Menor redundância em determinadas topologias

---

## Random Walk

A busca segue apenas um caminho pela rede, escolhendo um vizinho por vez.

Características:

* Baixo custo de comunicação
* Poucas mensagens
* Pode não encontrar o recurso dentro do TTL

---

## Informed Random Walk

Versão otimizada do Random Walk.

Características:

* Prioriza vizinhos considerados mais promissores
* Mantém baixo custo de mensagens
* Geralmente visita menos nós que o Flooding

---

# Execução da Busca

Na aba **Busca**, o usuário pode:

1. Selecionar o nó de origem.
2. Escolher o recurso desejado.
3. Definir o valor do TTL.
4. Selecionar o algoritmo.
5. Executar a busca.

---

# Resultados da Busca

Após a execução, o simulador apresenta:

* Algoritmo utilizado
* Recurso buscado
* Nó onde o recurso foi encontrado
* Quantidade total de mensagens trocadas
* Quantidade de nós envolvidos
* Status da busca (sucesso ou falha)

Também é exibido um log detalhado contendo todas as mensagens enviadas durante a execução.

---

# Visualização da Rede

A aba **Visualização** apresenta uma representação gráfica da rede através de um grafo desenhado em Canvas.

A visualização exibe:

* Nós da rede
* Conexões entre os nós
* Recursos armazenados
* Nós visitados durante a busca
* Caminhos percorridos
* Nó onde o recurso foi encontrado

---

# Animação das Buscas

Após executar uma busca, o simulador pode reproduzir visualmente o percurso realizado pelo algoritmo.

A animação mostra:

* Ordem de visita dos nós
* Mensagens enviadas
* Propagação da busca
* Momento em que o recurso é localizado

Isso facilita a compreensão do comportamento de cada algoritmo.

---

# Comparação de Algoritmos

A aba **Comparação** executa automaticamente os quatro algoritmos utilizando os mesmos parâmetros de busca.

Os resultados são exibidos lado a lado para facilitar a análise.

São comparados:

* Flooding
* Informed Flooding
* Random Walk
* Informed Random Walk


| Algoritmo | Mensagens | Cobertura da Rede | Eficiência Geral |
|------------|------------|------------------|------------------|
| Flooding | Alta | Alta | Média |
| Informed Flooding | Média | Alta | Alta |
| Random Walk | Baixa | Baixa | Média |
| Informed Random Walk | Baixa | Média | Alta |

---

# Métricas Comparadas

Para cada algoritmo são exibidos:

* Recurso encontrado ou não
* Número de mensagens trocadas
* Quantidade de nós visitados
* Nó onde o recurso foi localizado

Além disso, o simulador gera gráficos comparativos para facilitar a análise visual do desempenho.

---

# Como Executar

## Requisitos

Qualquer navegador moderno:

* Google Chrome
* Mozilla Firefox
* Microsoft Edge
* Opera

---

## Execução

Basta abrir o arquivo:

```text
p2p_simulator.html
```

Não é necessário instalar bibliotecas, dependências ou configurar servidor.

---

# Estrutura do Projeto

```text
p2p_simulator/
└── p2p_simulator.html
```

O arquivo contém:

* Interface gráfica (HTML)
* Estilos visuais (CSS)
* Parser YAML
* Validações da rede
* Implementação dos algoritmos
* Sistema de animação
* Visualização gráfica
* Comparação de desempenho

---

# Fluxo de Utilização

1. Escolher uma topologia de exemplo ou criar uma configuração própria.
2. Clicar em **Carregar e Validar Rede**.
3. Abrir a aba **Busca**.
4. Selecionar:

   * Nó de origem
   * Recurso
   * TTL
   * Algoritmo
5. Executar a busca.
6. Visualizar os resultados.
7. Utilizar as abas **Visualização** e **Comparação** para analisar o comportamento dos algoritmos.

---

# Tecnologias Utilizadas

* HTML5
* CSS3
* JavaScript (ES6)
* Canvas API

---

# Objetivo Acadêmico

Este projeto foi desenvolvido para demonstrar conceitos relacionados a:

* Redes Peer-to-Peer (P2P)
* Redes não estruturadas
* Algoritmos distribuídos
* Flooding
* Random Walk
* Avaliação de desempenho de algoritmos de busca
* Comparação de estratégias de comunicação em redes distribuídas


