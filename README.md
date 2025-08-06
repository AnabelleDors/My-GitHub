# My-GitHub 
**comandos-git.md** com tabela inicial:
   | Comando                     | Descrição                           |
   | --------------------------- | ----------------------------------- |
   | `git init`                  | Inicializa um repositório vazio     |
   | `git clone <url>`           | Clona repositório remoto            |
   | `git status`                | Mostra estado da árvore de trabalho |
   | `git add <arq>`             | Adiciona mudanças ao stage          |
   | `git commit -m "msg"`       | Registra snapshot                   |
   | `git push`                  | Envia commits ao GitHub             |
   | `git pull`                  | Sincroniza e integra mudanças       |
   | `git branch`                | Lista ou cria branches              |
   | `git merge`                 | Mescla branches                     |
   | `git log --oneline --graph` | Histórico compacto                  |

 Voltando a um commit (Revert / Reset)

| Método          | Quando usar                             | Comando principal                     |
| --------------- | --------------------------------------- | ------------------------------------- |
| **Nova branch** | Precisa testar mudança sem tocar `main` | `git checkout -b volta-commit <hash>` |
| **git revert**  | Quer preservar histórico (opção segura) | `git revert <hash>`                   |
| **git reset**   | Precisa reescrever histórico local      | `git reset --hard <hash>`             |

1. **Descobrir hash** do commit alvo:
   ```bash
   git log --oneline --graph --decorate -n 10
   ```
2. **Criar branch** (opcional, mas recomendado):
   ```bash
   git checkout -b hotfix/volta-commit <hash>
   ```
3. **Reverter (seguro):**
   ```bash
   git revert <hash>
   git push origin main
   ```
4. **Reset (perigoso):**
   ```bash
   # Desfaz commits locais e move ponteiro; use --soft para manter staging, --mixed (padrão) ou --hard.
   git reset --hard <hash>
   git push --force-with-lease
   ```
