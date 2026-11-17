# 📷 Inventário de Ativos

Aplicação web leve e 100% client-side para **gestão de inventário de ativos** (máquinas fotográficas e equipamentos em geral). Funciona inteiramente no navegador, sem backend, salvando os dados localmente no dispositivo via `localStorage`. Pode ser **instalada como PWA** em computadores, celulares e tablets.

> 🔗 **Demonstração online:** `https://SEU-USUARIO.github.io/SEU-REPOSITORIO/`
> _(substitua pelo endereço real após publicar no GitHub Pages)_

---

## ✨ Funcionalidades

- **Cadastro de ativos** com marca, modelo, numeração automática (`0001`, `0002`, …), característica, estado e foto.
- **Redimensionamento automático de fotos** no cliente (máx. 800px, JPEG 75%) antes de salvar — evita estourar o `localStorage`.
- **Pesquisa em tempo real** por marca, modelo, numeração, característica ou estado.
- **Ordenação por coluna** (clique no cabeçalho; 3º clique limpa a ordenação).
- **Inserir linha abaixo** de um item existente (botão `＋↓` nas ações).
- **Mover itens** para cima/baixo manualmente.
- **Estatísticas** em tempo real: total, marcas distintas e contagem por estado.
- **Importar/Exportar JSON** (backup completo com fotos).
- **Importar/Exportar CSV** (compatível com Excel, LibreOffice e Google Sheets — BOM UTF-8).
- **Imprimir / Gerar PDF** com layout A4 paisagem e cabeçalho de relatório.
- **Cabeçalho fixo** na tabela e barra de rolagem vertical exclusiva da lista.
- **Armazenamento local** — nenhum dado sai do dispositivo.
- **Compatível com PWA** — instalável e com suporte a funcionamento offline (quando configurado).

---

## 🚀 Publicação no GitHub Pages

### Passo a passo

1. **Crie um repositório** no GitHub (público ou privado).

   ```bash
   git init
   git add index.html README.md
   git commit -m "feat: inventário de ativos"
   git branch -M main
   git remote add origin https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
   git push -u origin main
   ```

2. **Ative o GitHub Pages**
   - No repositório, vá em **Settings → Pages**.
   - Em **Source**, selecione **Deploy from a branch**.
   - Em **Branch**, escolha **`main`** e a pasta **`/ (root)`**.
   - Clique em **Save**.

3. **Aguarde o deploy** (1–2 minutos). O endereço ficará no formato:

   ```
   https://SEU-USUARIO.github.io/SEU-REPOSITORIO/
   ```

4. **Pronto!** Acesse o endereço pelo navegador. Para que o modo PWA funcione com todas as funcionalidades (instalação, service worker, offline), o GitHub Pages já fornece **HTTPS** automaticamente. ✅

### Estrutura recomendada do repositório

```
SEU-REPOSITORIO/
├── index.html            # Aplicação completa (HTML + CSS + JS)
├── manifest.json         # (Opcional) Manifesto PWA
├── service-worker.js     # (Opcional) Cache e funcionamento offline
├── icons/
│   ├── icon-192.png      # (Opcional) Ícone PWA 192x192
│   └── icon-512.png      # (Opcional) Ícone PWA 512x512
└── README.md             # Este arquivo
```

> O `index.html` é **autocontido** — contém todo o HTML, CSS e JavaScript necessários. Não há dependências externas nem chamadas de rede.

---

## 💻 Instalação no computador

### No Google Chrome ou Microsoft Edge

1. Abra o endereço publicado do projeto.
2. Aguarde o carregamento completo da página.
3. Clique no ícone de instalação exibido na barra de endereço ou abra o menu do navegador.
4. Selecione **Instalar aplicativo** ou **Instalar este site como aplicativo**.
5. Confirme a instalação.

Depois disso, o aplicativo poderá ser aberto pelo menu **Iniciar**, pela **área de trabalho** ou pelo **gerenciador de aplicativos** do sistema.

---

## 📱 Instalação no celular ou tablet

### Em navegadores compatíveis

1. Abra o endereço do projeto.
2. Acesse o menu do navegador.
3. Selecione **Instalar aplicativo** ou **Adicionar à tela inicial**.
4. Confirme o nome e a instalação.

O ícone será adicionado à tela inicial do dispositivo.

---

## ⚠️ Observações sobre a instalação PWA

- A disponibilidade e o nome da opção de instalação podem variar conforme o navegador e o sistema operacional.
- Abrir somente o arquivo `index.html` pelo computador **não garante** a instalação como PWA.
- O projeto deve ser publicado em **HTTPS** para utilizar os recursos completos de instalação e service worker. O **GitHub Pages já fornece HTTPS automaticamente**.
- O funcionamento offline depende da configuração do `service-worker.js` e dos arquivos adicionados ao cache.
- Atualizações no projeto podem exigir a atualização da versão do cache do service worker.

---

## 📦 Importação e exportação

### JSON

Formato ideal para **backup completo** (inclui fotos em base64).

```json
[
  {
    "marca": "Canon",
    "modelo": "EOS 5D",
    "numeracao": "0001",
    "caracteristica": "Full frame, 30MP",
    "estado": "Seminova",
    "foto": "data:image/jpeg;base64,..."
  }
]
```

### CSV

Formato para planilhas. Separador detectado automaticamente (`;` ou `,`). Colunas aceitas (sem distinção de acento/maiúsculas):

| Marca | Modelo | Numeração | Característica | Estado |
|-------|--------|-----------|----------------|--------|

> ⚠️ **Atenção:** ao importar (JSON ou CSV), todos os registros atuais serão **substituídos**.

---

## 💾 Armazenamento local

Os dados são persistidos em:

| Chave | Conteúdo |
|---|---|
| `gestao_maquinas_v2` | Registros (array JSON) |
| `gestao_maquinas_v2_seq` | Controle do número sequencial |

Se o armazenamento estiver cheio, o sistema exibe um aviso e recomenda **exportar o JSON** e remover fotos grandes antes de continuar.

> 💡 **Backup recomendado:** use o botão **Exportar JSON** periodicamente para manter uma cópia de segurança dos dados fora do navegador.

---

## 🛠️ Tecnologias

- **HTML5** — estrutura semântica e elemento nativo `<dialog>`
- **CSS3** — Grid, Flexbox, `position: sticky`, `@media print`
- **JavaScript (ES6+)** — sem frameworks, sem dependências
- **APIs do navegador** — `localStorage`, `FileReader`, `Canvas`, `Blob`, `URL`

---

## ♿ Acessibilidade

- Ordenação por teclado nos cabeçalhos (`Enter` / `Espaço`).
- Atributos `aria-sort`, `aria-label` e `role="button"` aplicados corretamente.
- Foco visível (`:focus-visible`) em botões e cabeçalhos.
- Contraste de cores dentro das diretrizes WCAG AA no modo escuro.
- Layout responsivo e regras específicas para `@media print`.

---

## 📄 Licença

Nenhuma licença específica foi definida no arquivo fornecido. Antes de distribuir ou publicar o projeto, inclua uma licença compatível com a finalidade pretendida e verifique as licenças das bibliotecas externas utilizadas.

Sugestões de licença para projetos pessoais/educacionais: **MIT**, **Apache 2.0** ou **CC BY 4.0**.

---

## ⚖️ Aviso

> Este projeto é uma **demonstração educacional** desenvolvida para estudos de HTML, CSS e JavaScript. A empresa mencionada é **fictícia** e qualquer semelhança com empresas reais é mera coincidência.

---

## 🤝 Contribuindo

1. Faça um *fork* do projeto.
2. Crie uma *branch* para sua feature:

   ```bash
   git checkout -b feature/minha-feature
   ```

3. *Commit* suas alterações:

   ```bash
   git commit -m "feat: minha feature"
   ```

4. *Push* para a branch:

   ```bash
   git push origin feature/minha-feature
   ```

5. Abra um **Pull Request**.

---

## 📬 Suporte

Encontrou um problema ou tem uma sugestão? Abra uma **issue** no repositório do projeto.