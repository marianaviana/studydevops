# DevOps Cloud Academy

Portal de estudos de DevOps e Cloud (teoria) e **CODE LAB** (análise de código e configurações, com riscos, segurança, custos e troubleshooting).

Site estático feito com HTML, CSS e JavaScript puros. Não há build nem dependências.

## Estrutura

```
devops-cloud-academy/
├── index.html      # Portal teórico: Início, Azure, Azure Policy, Terraform/IaC
├── code-lab.html   # CODE LAB: Terraform VM, Plan, CI/CD, Kubernetes, DevSecOps, Incidente
├── vercel.json     # Configuração de deploy na Vercel
├── package.json    # Script para rodar localmente
└── README.md
```

## Rodar localmente

**Opção 1 (recomendada):** requer Node.js 18+

```bash
npm run dev
```

Abra http://localhost:3000

**Opção 2, sem Node:** requer Python 3

```bash
python3 -m http.server 3000
```

**Opção 3:** dê dois cliques em `index.html`. Funciona, pois não há dependências.

## Subir no GitHub

Crie um repositório vazio em github.com (sem README e sem .gitignore, pois eles já existem aqui) e rode:

```bash
git init -b main
git add .
git commit -m "feat: portal DevOps Cloud Academy e CODE LAB"
git remote add origin https://github.com/SEU-USUARIO/devops-cloud-academy.git
git push -u origin main
```

Com o GitHub CLI, tudo em um comando:

```bash
gh repo create devops-cloud-academy --public --source=. --push
```

## Deploy na Vercel

1. Acesse vercel.com e clique em **Add New → Project**.
2. Importe o repositório `devops-cloud-academy`.
3. Em **Framework Preset**, escolha **Other**. Deixe **Build Command** e **Output Directory** vazios (a raiz do projeto é publicada).
4. Clique em **Deploy**.

A partir daí, cada push na branch `main` gera um novo deploy automaticamente.

Alternativa pelo terminal:

```bash
npx vercel          # primeiro deploy (preview)
npx vercel --prod   # publica em produção
```

## Como atualizar

Edite `index.html` ou `code-lab.html`, depois:

```bash
git add .
git commit -m "docs: descrição da mudança"
git push
```

## Como adicionar um exemplo ao CODE LAB

Cada página do CODE LAB é uma função que retorna HTML (por exemplo, `tfvm()`). Para criar uma nova:

1. Escreva a função `minhaPagina()` retornando um template string com o conteúdo.
2. Registre a rota no objeto `R`, com título, breadcrumb e função.
3. Adicione o link no `<header>` da página.

**Atenção:** dentro de template strings, escreva `\${` quando precisar do texto literal `${` (por exemplo, em YAML do GitHub Actions). Sem a barra, o script quebra inteiro.

## Pendências

- Terraform: 18 exemplos (Resource Group, VNet, Key Vault, AKS, Private Endpoint etc.).
- CODE LAB: Docker, Azure CLI, Linux, PowerShell, Git, GitHub Actions, GitLab CI, Azure DevOps, Ansible, Networking, Azure Policy e ARM/Bicep.
- Kubectl: 10 cenários com quiz.
- Portal: Kubernetes, CI/CD, Git, DevSecOps, Monitoramento, AWS, Google Cloud, IBM Cloud e Sistemas Operacionais.
- Modos entrevista e incidente real.
