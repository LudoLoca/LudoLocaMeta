# Guia de Configuração e Versionamento - LudoLoca

## Clonar o Projeto com Submódulos

```bash
git clone --recurse-submodules https://github.com/LudoLoca/LudoLocaMeta.git
```

Se já tiver clonado sem submódulos:

```bash
git submodule update --init --recursive
```

## Abrir no Visual Studio

- Navegue até a pasta `LudoLocaMeta`
- Abra `LudoLoca.sln`

## Restaurar Pacotes NuGet

- O Visual Studio deve restaurar automaticamente
- Se precisar:

```powershell
Update-Package -reinstall
```

## Definir Vários Projetos de Inicialização

1. Clique com o botão direito na solução > Propriedades
2. Aba **Projetos de Inicialização**
3. Marque **Vários projetos de inicialização**
4. Configure `LudoLocaApi` e `LudoLocaClient` como **Iniciar**

## Aplicar Migrations

```bash
cd LudoLocaApi

dotnet ef database update
```

## Confiar no Certificado HTTPS

```bash
dotnet dev-certs https --trust
```

## Rodar a Solução

- Execute no Visual Studio (API + Client iniciando juntos)

---

## Git: Como Versionar Mudanças

### API ou Client (individualmente)

```bash
cd LudoLocaApi # ou LudoLocaClient
git checkout -b feat/nome-da-feature
git add .
git commit -m "feat: implementa funcionalidade X"
git push origin feat/nome-da-feature
```

### Projeto Principal (LudoLocaMeta)

```bash
cd LudoLocaMeta
git checkout -b feat/repo-integration
git add LudoLoca.sln LudoLocaApi LudoLocaClient
git commit -m "chore: atualiza submodules com novas features"
git push origin feat/repo-integration
```

---

Agora seu ambiente está pronto para desenvolvimento com a estrutura correta de versionamento.

