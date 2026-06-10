# Simulador de Busca em Redes P2P Não Estruturadas

## Descrição

Este projeto implementa um simulador visual de redes P2P (Peer-to-Peer) não estruturadas, permitindo a criação, validação e análise de diferentes topologias de rede e a execução de buscas por recursos utilizando múltiplos algoritmos.

O sistema foi desenvolvido como atividade acadêmica para estudo de algoritmos de busca distribuída em redes P2P, possibilitando comparar o desempenho de diferentes estratégias através de métricas como número de mensagens trocadas e quantidade de nós envolvidos na busca.

---

## Funcionalidades

### Criação de Redes P2P

* Leitura de arquivos de configuração em formato YAML simplificado.
* Construção automática da topologia da rede.
* Associação de recursos aos nós da rede.
* Suporte a diferentes topologias.

### Validação da Rede

O sistema realiza automaticamente as seguintes verificações:

* Rede não particionada (todos os nós devem ser alcançáveis).
* Respeito aos limites mínimo e máximo de vizinhos.
* Todos os nós devem possuir pelo menos um recurso.
* Não são permitidas arestas ligando um nó a ele mesmo.
* Consistência entre o valor de `num_nodes` e a quantidade de nós definidos.

### Algoritmos de Busca

O simulador implementa quatro algoritmos distintos:

#### Flooding

Propaga a busca para todos os vizinhos possíveis até que o TTL seja esgotado.

Características:

* Alta cobertura da rede.
* Grande quantidade de mensagens.
* Maior probabilidade de encontrar o recurso.

#### Informed Flooding

Versão otimizada do Flooding.

Características:

* Prioriza nós com maior quantidade de recursos.
* Mantém alta taxa de sucesso.
* Reduz buscas desnecessárias.

#### Random Walk

Encaminha a busca para apenas um vizinho por vez.

Características:

* Baixo custo em mensagens.
* Menor cobertura.
* Pode não encontrar o recurso dentro do TTL.

#### Informed Random Walk

Versão otimizada do Random Walk.

Características:

* Prioriza nós potencialmente mais relevantes.
* Menor custo de comunicação.
* Melhor eficiência que o Random Walk tradicional.

### Visualização Gráfica

* Representação visual da topologia da rede.
* Exibição dos nós e conexões.
* Destaque para nós visitados durante a busca.
* Identificação do nó onde o recurso foi encontrado.

### Animação das Buscas

* Exibição em tempo real da propagação das mensagens.
* Destaque dos caminhos percorridos.
* Visualização do processo de descoberta do recurso.

### Comparação de Algoritmos

Execução automática dos quatro algoritmos para o mesmo cenário de busca.

Métricas comparadas:

* Número de mensagens trocadas.
* Quantidade de nós visitados.
* Sucesso ou falha da busca.
* Nó onde o recurso foi localizado.

---

## Estrutura do Projeto

```text
p2p_simulator/
│
├── p2p_simulator.html
│
├── CSS
│   ├── Layout da aplicação
│   ├── Componentes visuais
│   └── Estilos da animação
│
├── JavaScript
│   ├── Parser YAML
│   ├── Validação da rede
│   ├── Algoritmos de busca
│   ├── Renderização do grafo
│   ├── Sistema de animação
│   └── Comparação de algoritmos
│
└── Exemplos de topologias
    ├── Small
    ├── Medium
    ├── Large
    ├── Ring
    └── Star
```

---

## Como Executar

### Método 1 (Recomendado)

Basta abrir o arquivo:

```text
p2p_simulator.html
```

em qualquer navegador moderno.

Exemplos:

* Google Chrome
* Mozilla Firefox
* Microsoft Edge
* Opera

Nenhuma instalação adicional é necessária.

---

## Arquivo de Configuração

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

## Fluxo de Utilização

### 1. Configuração

* Selecionar um exemplo pronto ou inserir uma configuração manualmente.
* Clicar em **Carregar e Validar Rede**.

### 2. Busca

Informar:

* Nó de origem.
* Recurso desejado.
* TTL.
* Algoritmo.

Em seguida clicar em:

```text
Executar Busca
```

### 3. Visualização

Acompanhar:

* Topologia da rede.
* Nós visitados.
* Caminhos percorridos.
* Resultado da busca.

### 4. Comparação

Executar os quatro algoritmos simultaneamente para comparar desempenho.

---

## Parâmetros da Busca

| Parâmetro   | Descrição               |
| ----------- | ----------------------- |
| node_id     | Nó que inicia a busca   |
| resource_id | Recurso procurado       |
| ttl         | Limite máximo de saltos |
| algo        | Algoritmo utilizado     |

Valores válidos para `algo`:

```text
flooding
informed_flooding
random_walk
informed_random_walk
```

---

## Métricas Coletadas

Ao final de cada execução são apresentados:

* Recurso encontrado ou não.
* Nó onde o recurso foi localizado.
* Número total de mensagens trocadas.
* Quantidade de nós envolvidos na busca.
* Registro detalhado das mensagens.

---

## Comparativo dos Algoritmos

| Algoritmo            | Mensagens | Cobertura | Eficiência |
| -------------------- | --------- | --------- | ---------- |
| Flooding             | Alta      | Alta      | Média      |
| Informed Flooding    | Média     | Alta      | Alta       |
| Random Walk          | Baixa     | Baixa     | Média      |
| Informed Random Walk | Baixa     | Média     | Alta       |

---

## Tecnologias Utilizadas

* HTML5
* CSS3
* JavaScript (ES6)
* Canvas API

---

## Objetivo Acadêmico

O projeto foi desenvolvido para demonstrar conceitos relacionados a:

* Redes Peer-to-Peer (P2P).
* Algoritmos distribuídos.
* Busca em redes não estruturadas.
* Flooding.
* Random Walk.
* Avaliação de desempenho de algoritmos distribuídos.

---

## Autores
Brenno Damiany Castro Vidal - 2315088
Caio Victor Ferreira Da Silva - 2010224
Diego Henrique Santos Queiroz - 2315108
Projeto desenvolvido para fins acadêmicos na disciplina de Redes de Computadores / Sistemas Distribuídos.
