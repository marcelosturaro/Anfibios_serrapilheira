# 🐸 Ecologia de Anfíbios de Serrapilheira

Aplicativo PWA (Progressive Web App) para coleta de dados ecológicos de
anfíbios de serrapilheira em campo. Funciona **100% offline**, guarda os
dados no próprio aparelho e exporta em CSV para análise em planilhas ou
no R.

🔗 **App online:** https://marcelosturaro.github.io/Caderno_Herpetologico

---

## ✨ Recursos

- 📱 **Instalável** em Android, iOS e desktop (PWA)
- 📡 **Funciona offline** após o primeiro acesso
- 📍 **Captura GPS** automática (latitude, longitude, precisão)
- 🐸 **6 espécies-alvo** com autocomplete:
  - *Physalaemus olfersii*
  - *Physalaemus cuvieri*
  - *Physalaemus maculiventris*
  - *Physalaemus bokermanni*
  - *Adenomera marmorata*
  - *Paratelmatobius cardosoi*
- 🗺️ **Autocomplete de estados e municípios** (IBGE, com cache local)
- 🌿 **Variáveis ambientais**: temperatura do ar e do substrato,
  umidade relativa do ar, luminosidade
- 📏 **Serrapilheira**: 5 medidas (central + 4 radiais) com **média
  automática**
- 🌳 **Estrutura da vegetação**: número total de árvores/arvoretas,
  árvores grandes (DAP > 15 cm), médio porte (DAP 5–15 cm), pequenas
  (DAP < 5 cm) e cobertura do dossel (%)
- ☀️ **Produtividade** (luminosidade entre 7h e 10h)
- 🌱 **Matriz dominante** (Gramínea / Floresta / Pinus) e % de ocupação
- 💾 **Persistência** em `localStorage` do aparelho
- 📤 **Exportação CSV** com 33 colunas (separador vírgula, UTF-8)
- 🌙 **Tema claro/escuro** automático (segue o sistema)
- 🇧🇷 **Interface em português**

---

## 📲 Instalação

### Android (Chrome / Edge / Samsung Internet / Brave)
1. Abra o link do app
2. Toque no botão **"Instalar aplicativo"** no topo
   *(ou menu ⋮ → "Instalar aplicativo")*
3. Confirme em **Instalar**

### iPhone / iPad (Safari)
1. Abra o link **no Safari**
2. Toque em **Compartilhar** (quadrado com seta ↑)
3. Role a lista e toque em **Adicionar à Tela de Início**
4. Toque em **Adicionar**

> O botão "Instalar aplicativo" no topo abre automaticamente um modal
> com essas instruções quando detecta iOS.

### Desktop (Chrome / Edge / Brave)
1. Abra o link
2. Clique no ícone de instalação na barra de endereços
   *(ou no botão no topo da página)*

---

## 🧭 Como usar em campo

### Antes de sair
1. Abra o app **com internet** ao menos uma vez (para o Service Worker
   baixar tudo)
2. Se for trabalhar em um estado novo, digite a **UF** no formulário
   uma vez — o app baixa a lista de municípios e guarda no aparelho

### Durante a coleta
1. **Seção 1 — Espécime**
   - Preencha o **Nº de campo** (o app sugere o próximo)
   - Escolha a **espécie** (autocomplete entre as 6 do estudo)
   - **Estado** e **Município** (preenchidos automaticamente na
     próxima vez que o app for aberto)
   - **Data** e **Horário** (preenchidos com o horário atual)
   - Toque em **"Atualizar localização"** para capturar o GPS
   - Massa, SVL, tipo de tecido, coletores, observações

2. **Seção 2 — Variáveis de habitat**
   - Temperaturas (ar / substrato), umidade, luminosidade
   - **5 alturas de serrapilheira** (central + 4 radiais) → a **média
     aparece automaticamente** no campo "Altura média"
   - **Nº de árvores/arvoretas** total
   - **Árvores grandes** (DAP > 15 cm), **médio porte** (5–15 cm) e
     **pequenas** (< 5 cm)
   - **Cobertura do dossel (%)** — resultado da análise da fotografia
     hemisférica no ImageJ
   - **Produtividade** (lx entre 7h e 10h), matriz dominante e sua %

3. Toque em **"Salvar espécime"**

### Ao final do dia
1. Toque em **"Exportar CSV"** — o arquivo vai para a pasta
   **Downloads** (`serrapilheira_AAAAMMDD.csv`)
2. Compartilhe por e-mail / Drive / WhatsApp Web

---

## 📂 Estrutura do projeto

| Arquivo | Função |
|---|---|
| `index.html` | Aplicativo completo (UI + lógica + lista de espécies) |
| `manifest.webmanifest` | Metadados do PWA (nome, ícones, cores, `id`) |
| `sw.js` | Service Worker — cache offline |
| `icon-192.png` | Ícone 192×192 (Android, favicon) |
| `icon-512.png` | Ícone 512×512 (splash, PWA store) |
| `icon-maskable-512.png` | Ícone adaptativo Android |
| `apple-touch-icon.png` | Ícone 180×180 para iOS |
| `.nojekyll` | Desativa Jekyll no GitHub Pages |
| `LICENSE` | Licença MIT |
| `README.md` | Este arquivo |

---

## 📊 Colunas exportadas no CSV

A planilha gerada tem **33 colunas**, na mesma ordem do formulário:

### Identificação e localidade
| # | Coluna | Unidade |
|---|---|---|
| 1 | Nº de campo | — |
| 2 | Sexo | — |
| 3 | Espécie | — |
| 4 | Estado | — |
| 5 | Município | — |
| 6 | Local | — |
| 7 | Data | AAAA-MM-DD |
| 8 | Horário | HH:MM |
| 9 | Latitude | graus decimais |
| 10 | Longitude | graus decimais |

### Dados do indivíduo
| # | Coluna | Unidade |
|---|---|---|
| 11 | Massa | g |
| 12 | SVL | mm |
| 13 | Tipo de tecido | — |
| 14 | Coletores | — |
| 15 | Observações | — |

### Variáveis ambientais
| # | Coluna | Unidade |
|---|---|---|
| 16 | Temp. ar | °C |
| 17 | Temp. substrato | °C |
| 18 | Umidade do ar | % |
| 19 | Luminosidade | lx |

### Serrapilheira (cm)
| # | Coluna |
|---|---|
| 20 | Serrapilheira central |
| 21 | Serrapilheira radial 1 |
| 22 | Serrapilheira radial 2 |
| 23 | Serrapilheira radial 3 |
| 24 | Serrapilheira radial 4 |
| 25 | **Serrapilheira média** (média automática das anteriores) |

### Estrutura da vegetação
| # | Coluna | Unidade |
|---|---|---|
| 26 | Nº árvores/arvoretas | — |
| 27 | Nº árvores grandes (DAP > 15 cm) | — |
| 28 | Nº árvores médio porte (DAP 5–15 cm) | — |
| 29 | Nº árvores pequenas (DAP < 5 cm) | — |
| 30 | Cobertura do dossel | % |

### Paisagem
| # | Coluna | Unidade |
|---|---|---|
| 31 | Produtividade 7–10h | lx |
| 32 | Matriz dominante | — |
| 33 | % matriz dominante | % |

> 💡 O CSV é gerado com **vírgula** como separador e **UTF-8**, e
> abre direto no Excel, LibreOffice, Google Sheets ou `read.csv()` no R.

---

## 🛠️ Tecnologias

- **HTML5 + CSS3 + JavaScript vanilla** (sem frameworks, sem build)
- **PWA**: Manifest + Service Worker
- **APIs nativas**:
  - `localStorage` para persistência
  - `navigator.geolocation` para GPS
  - `Blob` + `URL.createObjectURL` para download do CSV
  - `beforeinstallprompt` para instalação no Android
- **IBGE API** (`servicodados.ibge.gov.br`) para a lista de municípios
  (com cache no aparelho)

---

## 🚀 Publicar no GitHub Pages

```bash
git init
git add .
git commit -m "Versão inicial — Ecologia de Anfíbios de Serrapilheira"
git branch -M main
git remote add origin https://github.com/marcelosturaro/Caderno_Herpetologico.git
git push -u origin main