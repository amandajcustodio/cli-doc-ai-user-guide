# 🤖 cli.doc.ai – Guia de Uso

**Versão atual:** `v1.0.0`
*(Atualize conforme a release vigente.)*

---

## 📖 Visão Geral

O **cli.doc.ai** é uma ferramenta interna destinada à geração e atualização automática de documentação técnica para projetos **Angular** e **NestJS**.

A ferramenta realiza análise estática do código-fonte e utiliza **IA local (via Ollama)** para produzir documentação estruturada em Markdown.

> O arquivo disponibilizado corresponde à aplicação compilada e pronta para uso.
> Não há processo tradicional de instalação.

---

## 📦 Distribuição dos Arquivos

Os executáveis são disponibilizados separadamente por sistema operacional:

* 🪟 **Windows:**
  [`doc-ai-win.exe`](https://drive.google.com/drive/folders/1de0tC1iElfa0CHJI6jMcu14biByDM2AL?usp=sharing)

* 🐧 **Linux:**
  [`doc-ai-linux`](https://drive.google.com/drive/folders/1H458a2wRaCQJ4jm52ylkfEZ_AhbX9E0r?usp=sharing)

* 🍎 **macOS:**
  [`doc-ai-macos`](https://drive.google.com/drive/folders/1sRabaOZeAx102N1VAieNtMPHhvsd9mrC?usp=sharing)

Cada desenvolvedor deve baixar exclusivamente o binário correspondente ao seu sistema operacional.

---

## 🧠 Funcionamento

O fluxo de execução é simples:

1. O comando é executado no terminal, dentro do diretório do projeto.
2. A ferramenta analisa o código-fonte.
3. A IA local gera ou atualiza automaticamente os arquivos de documentação.
4. A documentação é criada ou atualizada no próprio projeto.

Não é necessário:

* Instalar Node.js
* Executar `npm install`
* Realizar build da ferramenta

Basta executar o binário.

---

## ✅ Requisitos Obrigatórios

### 1️⃣ Ollama (IA Local)

A ferramenta depende da execução de IA local via **Ollama**.

É obrigatório que o Ollama esteja:

* Instalado
* Em execução

Download oficial:
[https://ollama.com/download](https://ollama.com/download)

Endpoint esperado:

```
http://127.0.0.1:11434
```

---

### 2️⃣ Modelo Obrigatório

Antes da primeira utilização do CLI, é necessário instalar o modelo:

```bash
ollama pull qwen2.5:3b
```

Sem o Ollama ativo **e** o modelo devidamente instalado, a ferramenta não funcionará.

---

## ⚙️ Configuração Inicial

*(Executar apenas uma vez por máquina)*

---

### 🪟 Windows

1. Baixe o arquivo `doc-ai-win.exe`
2. Armazene-o em um diretório de sua preferência, por exemplo:

```
C:\Users\SeuNome\Tools\doc-ai\
```

3. Adicione esse diretório à variável de ambiente **PATH**

Após essa configuração, o comando `doc-ai` poderá ser executado a partir de qualquer diretório.

> Observação:
> Na primeira execução, o Windows poderá exibir um aviso de segurança.
> Selecione **Mais informações → Executar mesmo assim**.

---

### 🐧 Linux / 🍎 macOS

1. Baixe o binário correspondente (`doc-ai-linux` ou `doc-ai-macos`)
2. Conceda permissão de execução:

```bash
chmod +x doc-ai-linux
```

ou

```bash
chmod +x doc-ai-macos
```

3. (Recomendado) Mova o executável para um diretório global:

```bash
sudo mv doc-ai-linux /usr/local/bin/doc-ai
```

ou

```bash
sudo mv doc-ai-macos /usr/local/bin/doc-ai
```

Após isso, o comando `doc-ai` estará disponível globalmente.

---

## 🚀 Utilização

Dentro do diretório do projeto, execute:

```bash
doc-ai g -c
```

---

## 📌 Comando Principal

### `generate` (ou `g`)

Responsável por gerar documentação técnica por meio da análise de código e processamento via IA local.

### Opções disponíveis

* `-a` → Processa todo o projeto
* `-c` → Processa apenas arquivos alterados
* `-d` → Remove documentação de arquivos deletados
* `-f <arquivo>` → Processa um arquivo específico
* `-p <diretório>` → Processa um diretório específico
* `-skip-ai` → Gera documentação sem uso de IA (template padrão)

---

## 💡 Exemplos de Uso

Gerar documentação completa do projeto:

```bash
doc-ai g -a
```

Gerar documentação apenas para arquivos alterados:

```bash
doc-ai g -c
```

Gerar documentação para um arquivo específico:

```bash
doc-ai g -f src/app/app.component.ts
```

---

## 🔎 Diagnóstico

Caso o seguinte erro seja exibido:

```
AI service not available
```

Verifique:

1. Se o Ollama está em execução
2. Se o modelo foi corretamente instalado

Comandos para validação:

```bash
ollama list
```

```bash
ollama run qwen2.5:3b
```

---

## 🎯 Diretriz no Fluxo de Desenvolvimento

Sempre após:

* Concluir a implementação da feature
* Garantir que os testes estejam passando
* Validar o lint do projeto

Execute:

```bash
doc-ai g -c
```
