<template>
  <div class="app-container">
    <header class="header">
      <h1 class="title">
        <span class="title-icon">✏️</span>
        Format Text
      </h1>
    </header>

    <main class="content">
      <div class="toolbar">
        <div class="toolbar-section">
          <h3 class="toolbar-title">Formatação</h3>
          <div class="button-group">
            <button 
              @click="negrito()" 
              :class="['toolbar-btn', 'format-btn', { active: negritoAtivo }]"
              title="Negrito"
            >
              <span class="btn-icon">B</span>
            </button>
            <button 
              @click="italico()" 
              :class="['toolbar-btn', 'format-btn', { active: italicoAtivo }]"
              title="Itálico"
            >
              <span class="btn-icon">I</span>
            </button>
            <button 
              @click="sublinhado()" 
              :class="['toolbar-btn', 'format-btn', { active: sublinhadoAtivo }]"
              title="Sublinhado"
            >
              <span class="btn-icon">S</span>
            </button>
          </div>
        </div>

        <div class="toolbar-section">
          <h3 class="toolbar-title">Capitalização</h3>
          <div class="button-group">
            <button 
              @click="primeiraMaiuscula()" 
              :class="['toolbar-btn', 'case-btn', { active: primeiraMaiusAativo }]"
              title="Primeira Maiúscula"
            >
              <span class="btn-icon">Aa</span>
            </button>
            <button 
              @click="maiuscula()" 
              :class="['toolbar-btn', 'case-btn', { active: maiusculaAtivo }]"
              title="MAIÚSCULA"
            >
              <span class="btn-icon">AA</span>
            </button>
            <button 
              @click="minuscula()" 
              :class="['toolbar-btn', 'case-btn', { active: minusculaAtivo }]"
              title="minúscula"
            >
              <span class="btn-icon">aa</span>
            </button>
          </div>
        </div>

        <div class="toolbar-section">
          <button 
            @click="darkSelector()" 
            :class="['toolbar-btn', 'theme-btn', { active: darkBgAtivo }]"
            title="Alternar Tema"
          >
            <span class="btn-icon">{{ themeIcon }}</span>
          </button>
        </div>
    </div>

      <div class="text-container">
        <div class="text-input-section">
          <label for="text" class="section-label">
            <span class="label-icon">📝</span>
            Digite seu texto
          </label>
        <textarea
          name="text"
          id="text"
          v-model="text"
            :style="{backgroundColor: darkBg, color: darkColor}"
            placeholder="Digite aqui o texto que deseja formatar..."
            class="text-input"
        ></textarea>
          <div class="char-counter">{{ text.length }}/700</div>
      </div>

        <div class="text-output-section">
          <label class="section-label">
            <span class="label-icon">👁️</span>
            Preview
          </label>
          <div
            class="text-output"
            :style="{
              backgroundColor: darkBg,
              color: darkColor,
              fontWeight: pesoFonte,
              fontStyle: italicoFonte,
              textDecoration: sublinhadoFonte,
              textTransform: transformFonte,
            }"
          >
            {{ text || 'Seu texto formatado aparecerá aqui...' }}
          </div>
        </div>
    </div>
  </main>

    <footer class="footer">
      <p class="footer-text">
        Criado por 
        <span class="author-name">Axel Rammon</span>
      </p>
  </footer> 
  </div>
</template>

<script>

export default {
  data() {
    return {
      text: '',
      textEditar: '',

      // BACKGROUND ATIVO
      negritoAtivo: '',
      italicoAtivo: '',
      sublinhadoAtivo: '',
      primeiraMaiusAativo: '',
      maiusculaAtivo: '',
      minusculaAtivo: '',
      darkBgAtivo: '',
      themeIcon: '🌙',
      
      // CONFIGURAÇÕES 
      pesoFonte: '',
      italicoFonte: '',
      sublinhadoFonte: '',
      transformFonte: '',
      darkColor: '#1e293b',
      darkBg: '#ffffff',
    }
  },

  methods: {
    
    negrito: function() {
      if (this.pesoFonte === '') {
        this.pesoFonte = 'bold'
        this.negritoAtivo = '#667eea'
      } else {
        this.pesoFonte = ''
        this.negritoAtivo = ''
      }
    },
    
    italico: function() {
      if (this.italicoFonte === '') {
        this.italicoFonte = 'italic'
        this.italicoAtivo = '#667eea'
      } else {
        this.italicoFonte = ''
        this.italicoAtivo = ''
      }
    },

    sublinhado: function() {
      if (this.sublinhadoFonte === '') {
        this.sublinhadoFonte = 'underline'
        this.sublinhadoAtivo = '#667eea'
      } else {
        this.sublinhadoFonte = ''
        this.sublinhadoAtivo = ''
      }
    },

    primeiraMaiuscula: function() {
      if (this.transformFonte === '' || this.transformFonte === 'uppercase' || this.transformFonte === 'lowercase') {
        this.transformFonte = 'capitalize'
        this.primeiraMaiusAativo = '#667eea'
        this.maiusculaAtivo = ''
        this.minusculaAtivo = ''
      } else {
        this.transformFonte = ''
        this.primeiraMaiusAativo = ''
      }
    },

    maiuscula: function() {
      if (this.transformFonte === '' || this.transformFonte === 'capitalize' || this.transformFonte === 'lowercase') {
        this.transformFonte = 'uppercase'
        this.maiusculaAtivo = '#667eea'
        this.primeiraMaiusAativo = ''
        this.minusculaAtivo = ''
      } else {
        this.transformFonte = ''
        this.maiusculaAtivo = ''
      }
    },

    minuscula: function() {
      if (this.transformFonte === '' || this.transformFonte === 'uppercase' || this.transformFonte === 'capitalize') {
        this.transformFonte = 'lowercase'
        this.minusculaAtivo = '#667eea'
        this.primeiraMaiusAativo = ''
        this.maiusculaAtivo = ''
      } else {
        this.transformFonte = ''
        this.minusculaAtivo = ''
      }
    },

    darkSelector: function() {
      if (this.darkBg === '#ffffff') {
        // Mudar para modo escuro
        this.darkColor = '#e2e8f0'
        this.darkBg = '#1a1b23'
        this.darkBgAtivo = '#667eea'
        this.themeIcon = '☀️'
      } else {
        // Mudar para modo claro
        this.darkColor = '#1e293b'
        this.darkBg = '#ffffff'
        this.darkBgAtivo = ''
        this.themeIcon = '🌙'
      }
    }
    
  }
}

</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

/* Variables CSS */
:root {
  --primary-color: #667eea;
  --primary-dark: #5a6fd8;
  --secondary-color: #764ba2;
  --success-color: #4ade80;
  --warning-color: #fbbf24;
  --error-color: #f87171;
  --dark-bg: #1a1b23;
  --dark-surface: #2d2e37;
  --dark-text: #e2e8f0;
  --light-bg: #ffffff;
  --light-surface: #f8fafc;
  --light-text: #1e293b;
  --border-color: #e2e8f0;
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --border-radius: 12px;
  --border-radius-sm: 8px;
  --transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Reset e Base */
* {
  box-sizing: border-box;
}

.app-container {
  min-height: 100vh;
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  display: flex;
  flex-direction: column;
}

/* Header */
.header {
  text-align: center;
  padding: 2rem 1rem;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
}

.title {
  font-size: 2.5rem;
  font-weight: 700;
  color: black;
  margin: 0 0 0.5rem 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
}

.title-icon {
  font-size: 2rem;
}

.subtitle {
  font-size: 1.1rem;
  color: rgba(255, 255, 255, 0.95);
  margin: 0;
  font-weight: 400;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

/* Content */
.content {
  flex: 1;
  padding: 2rem 1rem;
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

/* Toolbar */
.toolbar {
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  border-radius: var(--border-radius);
  padding: 1.5rem;
  margin-bottom: 2rem;
  box-shadow: var(--shadow-lg);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

.toolbar-section {
  margin-bottom: 1.5rem;
}

.toolbar-section:last-child {
  margin-bottom: 0;
}

.toolbar-title {
  font-size: 0.875rem;
  font-weight: 600;
  color: #374151;
  margin: 0 0 0.75rem 0;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.button-group {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.toolbar-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  border: 2px solid transparent;
  border-radius: var(--border-radius-sm);
  background: #e2e8f0;
  color: #1e293b;
  font-weight: 500;
  border-radius: 10px;
  cursor: pointer;
  transition: var(--transition);
  position: relative;
  overflow: hidden;
}

.toolbar-btn:hover {
  background: var(--primary-color);
  color: black;
  background: #e2e8f0;
  transform: translateY(-2px);
  box-shadow: var(--shadow-md);
}

.toolbar-btn.active {
  background: #c9ccd1;
  color: white;
  border-color: var(--primary-dark);
  box-shadow: var(--shadow-md);
}

.format-btn, .case-btn {
  min-width: 48px;
  justify-content: center;
}

.theme-btn {
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: black;
}

.theme-btn:hover {
  transform: translateY(-2px) scale(1.05);
}

.btn-icon {
  font-weight: 700;
  font-size: 1rem;
}

.btn-text {
  font-size: 0.875rem;
}

/* Text Container */
.text-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  align-items: start;
}

@media (max-width: 768px) {
  .text-container {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}

.text-input-section, .text-output-section {
  display: flex;
  flex-direction: column;
}

.section-label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-weight: 600;
  color: black;
  margin-bottom: 0.75rem;
  font-size: 1rem;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

.label-icon {
  font-size: 1.25rem;
}

/* Text Input */
.text-input {
  width: 100%;
  min-height: 300px;
  padding: 1rem;
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: var(--border-radius);
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  font-family: inherit;
  font-size: 1rem;
  line-height: 1.6;
  resize: vertical;
  transition: var(--transition);
  box-shadow: var(--shadow-sm);
}

.text-input:focus {
  outline: none;
  border-color: var(--primary-color);
  box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
  transform: translateY(-1px);
}

.text-input::placeholder {
  color: rgba(30, 41, 59, 0.5);
}

/* Text Output */
.text-output {
  width: 100%;
  min-height: 300px;
  padding: 1rem;
  border: 2px solid rgba(255, 255, 255, 0.2);
  border-radius: var(--border-radius);
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  font-family: inherit;
  font-size: 1rem;
  line-height: 1.6;
  word-break: break-word;
  overflow-wrap: break-word;
  box-shadow: var(--shadow-sm);
  transition: var(--transition);
}

/* Char Counter */
.char-counter {
  margin-top: 0.5rem;
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.8);
  text-align: right;
  font-weight: 500;
}

/* Footer */
.footer {
  padding: 1.5rem;
  text-align: center;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border-top: 1px solid rgba(255, 255, 255, 0.2);
}

.footer-text {
  color: black;
  margin: 0;
  font-size: 1rem;
  font-weight: 400;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

.author-name {
  font-weight: 600;
  color: black;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
}

/* Dark mode adjustments */
.app-container.dark {
  --light-bg: var(--dark-bg);
  --light-surface: var(--dark-surface);
  --light-text: var(--dark-text);
}

/* Animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.toolbar, .text-container {
  animation: fadeInUp 0.6s ease-out;
}

.text-container {
  animation-delay: 0.2s;
}

/* Responsive */
@media (max-width: 640px) {
  .title {
    font-size: 2rem;
  }
  
  .subtitle {
    font-size: 1rem;
  }
  
  .content {
    padding: 1rem;
  }
  
  .toolbar {
    padding: 1rem;
  }
  
  .button-group {
    justify-content: center;
  }
  
  .toolbar-btn {
    padding: 0.5rem 0.75rem;
    font-size: 0.875rem;
  }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* Focus styles for keyboard navigation */
.toolbar-btn:focus-visible,
.text-input:focus-visible {
  outline: 2px solid var(--primary-color);
  outline-offset: 2px;
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  .toolbar-btn {
    border: 2px solid currentColor;
  }
  
  .text-input,
  .text-output {
    border: 2px solid currentColor;
  }
}
</style>