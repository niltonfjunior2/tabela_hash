# 🔍 Laboratório de Tabela Hash Interativo

Uma aplicação web interativa desenvolvida para visualizar e compreender o funcionamento interno de **Tabelas Hash** (Tabelas de Dispersão). Este projeto tem fins educacionais, demonstrando visualmente como os elementos são inseridos, buscados e como o sistema lida com o problema comum das colisões em memória.

---

## ✨ Funcionalidades

* **Visualização em Tempo Real:** Acompanhe a alocação de memória e o percurso de busca no exato momento da operação.
* **Fator de Carga (α):** Monitoramento dinâmico da relação entre o número de elementos e o tamanho da tabela (`α = n/m`), com alertas visuais indicando sobrecarga.
* **Painel de Log Detalhado:** Um terminal integrado que explica, passo a passo, a matemática por trás dos cálculos de hash e das sondagens em caso de colisão.
* **Três Estratégias de Colisão Implementadas:**
* **Encadeamento Separado:** Utiliza listas em cada índice para armazenar múltiplos valores, permitindo que o Fator de Carga ultrapasse 1.0.
* **Endereçamento Aberto (Sondagem Linear):** Em caso de colisão, procura o próximo espaço livre sequencialmente.
* **Endereçamento Aberto (Duplo Hashing):** Aplica uma segunda função de hash para determinar o tamanho do salto iterativo, minimizando problemas de agrupamento primário.



---

## 🛠️ Tecnologias Utilizadas

O projeto foi construído exclusivamente com tecnologias web nativas, sendo leve e não dependendo de bibliotecas ou *frameworks* externos:

* **HTML5:** Estrutura e semântica da interface.
* **CSS3:** Estilização moderna utilizando Flexbox, painéis responsivos (Sticky) e animações (`@keyframes`) para fornecer *feedback* visual imediato sobre o status das operações (ex: nós chacoalhando em colisões).
* **JavaScript (Vanilla):** Lógica principal contendo o cálculo de *hash*, manipulação assíncrona (`Promises` e `setTimeout`) para gerar cadência nas animações, e o gerenciamento de estados no DOM.

---

## 🧠 Conceitos Técnicos Abordados

Para fins didáticos, a tabela possui um tamanho fixo em memória definido como **Tamanho (m) = 20**.

### Funções de Hash

O cálculo de índice inicial baseia-se na soma do valor na tabela ASCII de cada caractere da string fornecida.

* **Função Principal:** `h1(chave) = soma_ascii(chave) % 20`
* **Função Secundária (Passo):** `h2(chave) = 7 - (soma_ascii(chave) % 7)` *(Utilizada apenas na estratégia de Duplo Hashing)*

### Fórmulas de Resolução (Endereçamento Aberto)

Quando a posição original está ocupada, o algoritmo calcula o próximo índice com base na tentativa atual (`i`, iniciando em 0):

* **Sondagem Linear:** `Índice = (h1 + i) % 20`
* **Duplo Hashing:** `Índice = (h1 + i * h2) % 20`

---

## 🚀 Como Executar

Por ser uma aplicação *Client-side* estática, a execução é extremamente simples e não requer configurações complexas de ambiente:

1. Clone este repositório:
```bash
git clone https://github.com/seu-usuario/nome-do-repositorio.git

```


2. Navegue até a pasta do projeto.
3. Dê um duplo clique no arquivo `index.html` para abri-lo no seu navegador web padrão (Chrome, Firefox, Edge, etc).
4. *Opcional:* Você pode utilizar a extensão *Live Server* do VSCode para testar modificações no código em tempo real.

---

## 🕹️ Como Usar

1. Selecione a **Estratégia de Tratamento de Colisão** desejada no menu suspenso.
2. Digite qualquer texto no campo de entrada.
3. Clique em **Inserir** (ou pressione `Enter`) para calcular o hash e adicionar à tabela.
4. Clique em **Buscar** para procurar um elemento previamente inserido. Acompanhe a busca percorrendo os índices de acordo com a estratégia ativa.
5. Clique em **Limpar** para esvaziar a tabela, resetar os índices e restaurar o Fator de Carga a zero.