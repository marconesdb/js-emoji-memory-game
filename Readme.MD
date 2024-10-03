# 🧠 Jogo da Memória com Emojis 🐱🐶🦊

Este projeto é um jogo da memória simples e divertido, desenvolvido em HTML, CSS e JavaScript, onde o objetivo é combinar pares de emojis. Cada carta contém um emoji escondido, e o jogador deve encontrar todas as combinações para vencer o jogo.

---

## 🚀 Funcionalidades

- Combinação de pares de cartas contendo emojis 🐱, 🦊, 🐶, entre outros.
- Interação visual com efeito de virar as cartas quando selecionadas.
- Reset do jogo ao clicar no botão "RESET GAME".
- Interface responsiva com um design colorido e interativo.

---

## 🛠️ Ferramentas Utilizadas

- **HTML5**: Estrutura do jogo.
- **CSS3**: Estilos e layout com animações de flip (virada das cartas) e design responsivo.
- **JavaScript (ES6)**: Lógica do jogo, manipulação do DOM e interatividade.

---

## 📦 Como Instalar e Usar

Siga os passos abaixo para rodar o projeto localmente:

### 1. Clone o Repositório

```bash
git clone https://github.com/marconesdb/js-emoji-memory-game
```

### 2. Acesse o Diretório do Projeto

```bash
cd NOME_DE_SUA_PASTA
```

### 3. Abra o Arquivo HTML no Navegador

Como este é um projeto simples de front-end, basta abrir o arquivo `index.html` em seu navegador preferido:

```bash
open index.html
```

Ou simplesmente arraste o arquivo `index.html` para uma nova aba no seu navegador.

---

## 📖 Como Jogar

1. Ao iniciar o jogo, você verá uma grade de cartas viradas para baixo.
2. Clique em uma carta para revelá-la. Ela mostrará um emoji 🎴.
3. Em seguida, clique em outra carta. Se os dois emojis forem iguais, as cartas permanecerão abertas 🎉.
4. Se os emojis forem diferentes, as cartas serão viradas de volta após 0,5 segundos ⏳.
5. Continue até encontrar todos os pares de cartas iguais e vencer o jogo! 🏆

---

## 📂 Estrutura do Projeto

- **`index.html`**: Arquivo principal que estrutura o jogo.
- **`/src/styles/main.css`**: Arquivo CSS que define os estilos e animações.
- **`/src/scripts/engine.js`**: Contém a lógica do jogo, como embaralhamento, comparações e eventos de clique.

---

## ✨ Estilos de Interface

- As cartas "viram" utilizando animações de rotação em 3D.
- Background com gradiente colorido vibrante 🌈, e botões de reinício com um design limpo e moderno.

---

## 🔍 Explicação do Código

### JavaScript:

1. **Array de Emojis**: Contém os pares de emojis que serão exibidos nas cartas.
   ```javascript
   const emojis = [ "🐱", "🐱", "🦝", "🦝", "🦊", "🦊", "🐶", "🐶", "🐵", "🐵", "🦁", "🦁", "🐯", "🐯", "🐮", "🐮"];
   ```

2. **Embaralhamento de Emojis**: O array de emojis é embaralhado usando o método `sort()`.
   ```javascript
   let shuffleEmojis = emojis.sort(() => (Math.random() > 0.5 ? 2 : -1));
   ```

3. **Criação das Cartas**: As cartas são criadas dinamicamente no DOM, e os emojis são adicionados a cada uma delas.
   ```javascript
   for (let i = 0; i < emojis.length; i++) {
     let box = document.createElement("div");
     box.className = "item";
     box.innerHTML = shuffleEmojis[i];
     box.onclick = handleClick;
     document.querySelector(".game").appendChild(box);
   }
   ```

4. **Manipulação dos Eventos de Clique**: Ao clicar nas cartas, elas "viram" e são comparadas. Se forem iguais, permanecem abertas; se não, voltam a se virar.
   ```javascript
   function handleClick() {
     if (openCards.length < 2) {
       this.classList.add("boxOpen");
       openCards.push(this);
     }
     if (openCards.length == 2) {
       setTimeout(checkMatch, 500);
     }
   }
   ```

5. **Verificação de Combinações**: Verifica se as duas cartas viradas são iguais.
   ```javascript
   function checkMatch() {
     if (openCards[0].innerHTML === openCards[1].innerHTML) {
       openCards[0].classList.add("boxMatch");
       openCards[1].classList.add("boxMatch");
     } else {
       openCards[0].classList.remove("boxOpen");
       openCards[1].classList.remove("boxOpen");
     }
     openCards = [];
     if (document.querySelectorAll(".boxMatch").length === emojis.length) {
       alert("Você venceu !");
     }
   }
   ```

---

## 🎮 Teste o Jogo

Abra o arquivo `index.html` no navegador e divirta-se encontrando os pares de emojis!

---

Divirta-se jogando o **Jogo da Memória com Emojis**! 🎉