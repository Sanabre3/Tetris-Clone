# 🎮 Tetris Clone

Um clone clássico do jogo Tetris desenvolvido em JavaScript usando a biblioteca p5.js. O jogo apresenta todas as funcionalidades tradicionais do Tetris com uma interface moderna e responsiva.

## 📋 Índice

- [Demonstração](#demonstração)
- [Funcionalidades](#funcionalidades)
- [Tecnologias Utilizadas](#tecnologias-utilizadas)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Como Executar](#como-executar)
- [Controles](#controles)
- [Mecânicas do Jogo](#mecânicas-do-jogo)
- [Arquitetura do Código](#arquitetura-do-código)
- [Customização](#customização)
- [Contribuindo](#contribuindo)

## ⚡⚡ Demonstração

O jogo apresenta:
- **Área de jogo principal** (300x540 pixels)
- **Painel de informações** com pontuação, nível e linhas removidas
- **Preview da próxima peça**
- **Controles intuitivos** para movimento e rotação
- **Sistema de pontuação progressiva**

## ✨ Funcionalidades

### 🎮 Jogabilidade
- ✅ 7 tipos diferentes de peças (I, J, L, O, S, T, Z)
- ✅ Rotação completa das peças (4 orientações)
- ✅ Detecção de colisão precisa
- ✅ Remoção automática de linhas completas
- ✅ Aceleração da queda com tecla ↓
- ✅ Preview da próxima peça

### 📊 Sistema de Progressão
- ✅ Sistema de pontuação dinâmico
- ✅ Progressão de níveis a cada 10 linhas
- ✅ Aumento gradual da velocidade
- ✅ Contador de linhas removidas

### 🎨 Interface
- ✅ Design visual moderno
- ✅ Paleta de cores vibrante
- ✅ Efeitos visuais nas peças
- ✅ Layout responsivo e centralizado

## 🛠 Tecnologias Utilizadas

- **HTML5** - Estrutura da página
- **CSS3** - Estilização e layout
- **JavaScript (ES6+)** - Lógica do jogo
- **p5.js** - Biblioteca para renderização gráfica
- **Google Fonts** - Tipografia (Ubuntu)

## 📁 Estrutura do Projeto

```
tetris-clone/
│
├── index.html          # Página principal
├── style.css           # Estilos globais
├── script.js           # Lógica principal do jogo
└── pieces.js           # Definições das peças e rotações
```

### 📄 Detalhamento dos Arquivos

#### `index.html`
- Estrutura HTML básica
- Importação da biblioteca p5.js via CDN
- Carregamento dos scripts do jogo

#### `style.css`
- Importação da fonte Ubuntu
- Centralização do canvas na página
- Estilo de fundo global

#### `script.js`
- **Classes principais:**
  - `PlayPiece` - Gerencia a peça em queda
  - `Square` - Representa cada bloco individual
  - `Worker` - Controla animações de linha
- **Funções de controle:**
  - Loop principal do jogo
  - Detecção de colisões
  - Sistema de pontuação
  - Análise e remoção de linhas

#### `pieces.js`
- Função `orientPoints()` que define as coordenadas de cada peça
- 7 tipos de peças com 4 rotações cada
- Sistema de coordenadas relativas

## 🚀 Como Executar

### Pré-requisitos
- Navegador web moderno
- Servidor local (recomendado)

### Instalação

1. **Clone ou baixe o projeto**
```bash
git clone [url-do-repositorio]
cd tetris-clone
```

2. **Execute um servidor local**

**Opção 1: Python**
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

**Opção 2: Node.js (http-server)**
```bash
npm install -g http-server
http-server
```

## 🎮 Controles

| Tecla | Ação |
|-------|------|
| `←` | Mover peça para a esquerda |
| `→` | Mover peça para a direita |
| `↑` | Rotacionar peça |
| `↓` | Acelerar queda da peça |
| `R` | Reiniciar o jogo |

## 🤖🤖 Mecânicas do Jogo

### Sistema de Pontuação
- **100 pontos** por linha simples removida
- **200 pontos** por múltiplas linhas simultâneas
- Pontuação acumulativa durante o jogo

### Progressão de Níveis
- Nível aumenta a cada **10 linhas** removidas
- Velocidade de queda aumenta com o nível
- Velocidade mínima limitada para manter jogabilidade

### Tipos de Peças

| Tipo | Nome | Descrição |
|------|------|-----------|
| I | Linha | Peça reta de 4 blocos |
| J | Gancho | Peça em forma de L invertido |
| L | Gancho Invertido | Peça em forma de L |
| O | Quadrado | Bloco 2x2 |
| S | Zig-zag | Peça em S |
| T | T | Peça em formato de T |
| Z | Zig-zag Invertido | Peça em Z |

## 🏗 Arquitetura do Código

### Fluxo Principal

```javascript
setup() → draw() → keyPressed()
    ↓         ↓         ↓
Inicialização → Loop → Entrada
```

### Classes Principais

#### `PlayPiece`
```javascript
// Propriedades principais
- pos: Vector2D          // Posição atual
- rotation: Number       // Rotação (0-3)
- pieceType: Number      // Tipo da peça (0-6)
- pieces: Array<Square>  // Blocos da peça

// Métodos principais
- fall()                 // Movimento de queda
- input()               // Processamento de entrada
- futureCollision()     // Detecção de colisão
- commitShape()         // Fixar peça na grade
```

#### `Square`
```javascript
// Propriedades
- pos: Vector2D         // Posição do bloco
- type: Number          // Tipo para coloração

// Métodos
- show()                // Renderização visual
```

### Sistema de Coordenadas

- **Grade:** 10 colunas × 18 linhas
- **Tamanho do bloco:** 30×30 pixels
- **Área de jogo:** 300×540 pixels
- **Coordenadas:** Sistema cartesiano com origem no canto superior esquerdo

## 🎨 Customização

### Alterando Cores
```javascript
// Em script.js - linha ~25
const colors = [
  "#dca3ff",  // Peça I - Roxo claro
  "#ff90a0",  // Peça J - Rosa
  "#80ffb4",  // Peça L - Verde claro
  "#ff7666",  // Peça O - Laranja
  "#70b3f5",  // Peça S - Azul
  "#b2e77d",  // Peça T - Verde lima
  "#ffd700",  // Peça Z - Dourado
];
```

### Ajustando Velocidade
```javascript
// Em script.js - linha ~20
let updateEvery = 15;        // Ticks entre quedas (menor = mais rápido)
let fallSpeed = gridSpace * 0.5;  // Velocidade de queda em pixels
```

### Modificando Tamanho da Grade
```javascript
// Em script.js - linha ~3
const gridSpace = 30;        // Tamanho de cada célula
```

## 🤝 Contribuindo

Contribuições são bem-vindas! Para contribuir:

1. **Fork** o projeto
2. Crie uma **branch** para sua feature (`git checkout -b feature/nova-feature`)
3. **Commit** suas mudanças (`git commit -m 'Adiciona nova feature'`)
4. **Push** para a branch (`git push origin feature/nova-feature`)
5. Abra um **Pull Request**

### Ideias para Contribuições

- 🎵 Sistema de som e música
- 💾 Sistema de save/load de pontuação
- 🎮 Controles alternativos (mouse, touch)
- 🎨 Temas visuais customizáveis
- 📱 Responsividade para mobile
- 🏆 Sistema de conquistas
- 👻 Modo "ghost piece" (preview da posição)

## 📝 Notas Técnicas

### Dependências Externas
- **p5.js v1.9.2** - Carregada via CDN do Cloudflare

### Compatibilidade
- ✅ Chrome 60+
- ✅ Firefox 55+
- ✅ Safari 12+
- ✅ Edge 79+

### Performance
- **60 FPS** em dispositivos modernos
- **Otimizado** para renderização em tempo real
- **Baixo uso de memória** (~10MB)

---

**Desenvolvido usando p5.js**

*Divirta-se jogando e contribuindo para o projeto!* 🎮
