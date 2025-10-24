# Desafio Colaborativo Git Flow


Todas as ações devem ser realizadas direto no GitHub Codespaces.

✅ O que você vai aprender na prática

✔ Criar fork e trabalhar com o Codespaces  
✔ Utilizar branches feature / hotfix / develop / main conforme o Git Flow  
✔ Criar histórico limpo e organizado com múltiplos commits  
✔ Sincronizar seu fork com o repositório central  
✔ Resolver conflitos e enviar correções urgentes  
✔ Criar e gerenciar Issues e Project Board (Kanban)  

## 💡 Cenário

Parabéns! Vocês são a nova equipe de desenvolvimento do projeto **"Web App de Citações Favoritas"** e acabaram de adotar o modelo **Git Flow** para gerenciar o versionamento do código.

O objetivo desta atividade é simular um ciclo completo de desenvolvimento: implementar novas funcionalidades, lançar uma nova versão e corrigir um bug crítico em produção.

A comunicação e a colaboração via **Pull Requests** serão essenciais neste processo!

#### 🧩 Estrutura Inicial do Projeto

O repositório já possui as branches:

main → código em produção

develop → próxima versão que será lançada

Você irá criar os arquivos iniciais:

📄 AUTORAS.md → Informações das contribuidoras
📃 citações.txt → 5 citações preferidas por participante

---

## 🛠 Repositório e configuração

- **Repositório central (Upstream):** https://github.com/instrutor-edmar/git-fluxo-de-trabalho-em-equipe
- **Ambiente:** GitHub Codespaces (aberto no seu fork)

---

## ✅ Passo 1: fork, codespace e sincronização

1. Cada jovem deve realizar o **fork** do repositório central.
2. Abrir o **codespace** no próprio fork.
3. Configurar o repositório central como `upstream`:

```sh
git remote add upstream https://github.com/instrutor-edmar/git-fluxo-de-trabalho-em-equipe.git
git fetch upstream
```
---


## ✅ Passo 2: inicialização do Git Flow (desenvolvimento base)

Criar a branch develop a partir da branch principal (main):

```sh
git checkout main
git pull upstream main
git checkout -b develop
git push origin develop
```

## 🎭 Funções (divisão de tarefas)
| Função                        | Responsabilidade                   | Origem da Branch | PR Destino     | Jovens                   |
| ----------------------------- | ---------------------------------- | ---------------- | -------------- | ------------------------ |
| Desenvolvedora Feature        | Implementar novas funcionalidades  | develop          | develop        | TODAS                    |
| Líder de Lançamento (Release) | Preparar a versão                  | develop          | main e develop | A critério do Instrutor  |
| Mantenedora Hotfix            | Corrigir bugs críticos em produção | main             | main e develop | A critério do Instrutor  |

## 🎯 Tarefas e fluxo de execução
🔹 FASE 1 — Desenvolvimento de Funcionalidades (TODAS as desenvolvedoras feature)
Vocês irão implementar a funcionalidade de adicionar seus perfis e citações favoritas.


#### 1. Criar a feature branch (a partir de develop):
```sh
# Exemplo: git flow feature start meu-perfil
git checkout develop
git checkout -b feature/sua-iniciativa
```

#### 2. Desenvolvimento:
- Crie os arquivos iniciais:
```sh
AUTORAS.md
citaçõess.txt
```
- Em `AUTORAS.md`: adicione sua seção de autora (usando ## [Seu Nome]), uma pequena biografia criativa e um link de imagem de perfil.
```sh
## Seu nome ompleto
- Estudante de tecnologia 👩‍💻
- Link da foto: ![](https://picsum.photos/120)
```

- No arquivo `citações.txt`: adicione cinco citações favoritas (uma por linha), com a fonte entre parênteses.

```sh
"citação 1" (referência)
"citação 2" (fonte)
"citação 3" (de quem é)
```

#### 3. Commits e mesclagem (apenas para develop):
```sh
git add .
git commit -m "feat: Adiciona perfil da autora e citações"
git push origin feature/minhas-citacoes
```

#### 4. Pull request (PR):

Abra um Pull Request do seu fork (feature/minhas-citacoes) para a branch develop do repositório central (instrutor-edmar/git-fluxo-de-trabalho-em-equipe).

Aguardem a aprovação e mesclagem pela Líder de Lançamento.


🔹 FASE 2: Preparação para Lançamento (APENAS Líderes de Lançamento)

Assim que todas as features forem mescladas em develop, é hora de preparar a versão v1.0.0.

#### 1. Criar a branch de release (a partir de develop):

Primeiro, sincronize sua branch develop com o upstream (repositório central) para garantir que todas as features das colegas estão incluídas:

```sh
git checkout develop
git pull upstream develop
```

Agora, inicie a Release Branch:

```sh
# Exemplo: git flow release start 1.0.0
git checkout -b release/1.0.0
```


#### 2. Ajustes finais:

No arquivo README.md, adicione no topo uma seção de "Próximo Lançamento" mencionando que a versão v1.0.0 está em preparação.

Comite a alteração:

```sh
git add README.md
git commit -m "chore(release): Prepara documentacao para v1.0.0"
git push origin release/1.0.0
```


#### 3. Pull request final (para main e develop):

- Abra um Pull Request do seu fork (release/1.0.0) para a branch main do repositório central.

- O Instrutor fará a mesclagem em main e develop e a criação da Tag.

- Após a mesclagem, a Release Branch pode ser excluída.



🔹 FASE 3: Correção de emergência (Hotfix) em Produção (APENAS Mantenedoras Hotfix)

📌 O instrutor fará um hotfix em produção (`main`)
Um bug crítico foi encontrado em produção (branch main)! A versão v1.0.0 está no ar, mas uma das citações está com erro de formatação. 
➡ sua branch ficará desatualizada

#### 1. Sincronizar main e criar Hotfix Branch:

- Sincronize sua branch main com o upstream para ter a versão v1.0.0:

```sh
git checkout main
git pull upstream main

ou

git remote add upstream https://github.com/instrutor-edmar/git-fluxo-de-trabalho-em-equipe
git fetch upstream
git rebase upstream/main
git push origin feature/minhas-citacoes --force
```
👀 Algumas colegas serão selecionadas para criar intencionalmente um conflito e resolver pelo Codespaces:

- Inicie o Hotfix Branch a partir de main:

```sh
# Exemplo: git flow hotfix start fix-formatacao-citacoes
git checkout -b hotfix/v1.0.1

ou

git pull upstream main
# corrigir conflitos manualmente
git add .
git commit -m "fix: resolve conflito em citas.txt"
git push origin feature/minhas-citacoes

```


#### 2. Correção:

#### ✅ Project Board + Issues (opcional)
Vincule PRs às Issues pelo GitHub 

📌 No seu fork, crie um Project (Kanban) com 3 colunas:

📌 A Fazer

👩‍💻 Em Progresso

✅ Concluído

Crie as seguintes Issues automáticas:

Issue	Descrição
Issue 1	Criar arquivos iniciais (AUTORES e Citações)
Issue 2	Criar Branch Feature e adicionar commits
Issue 3	Criar Pull Request para o repositório central
Issue 4	Sincronizar com upstream e resolver conflitos


- No arquivo `citações.txt` procure um erro de pontuação ou formatação em qualquer citação e corrija-o.

- Comite a correção:

```sh
git add citacoes.txt
git commit -m "fix(hotfix): Corrige erro de pontuacao no catalogo de citações"
git push origin hotfix/v1.0.1
```

#### 3. Pull request final (para main e develop):

- Abra um Pull Request do seu fork (hotfix/v1.0.1) para a branch main do repositório central.

- A Instrutora fará a mesclagem em main e develop e a criação da Tag v1.0.1.

- Após a mesclagem, o Hotfix Branch pode ser excluída.
