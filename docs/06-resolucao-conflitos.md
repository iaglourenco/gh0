# Resolução de Conflitos no Git

## Estratégias Automáticas
- **-Xours**: Prioriza as alterações da branch atual (nossa). Ideal quando temos certeza de que nossa lógica local está correta.
- **-Xtheirs**: Prioriza as alterações da branch que está sendo integrada (deles). Útil para absorver correções externas críticas.

## Ferramentas de Controle
- **git merge --abort**: Comando de segurança para desistir do merge e retornar ao estado anterior ao conflito.
- **git merge --no-commit**: Realiza o merge mas não cria o commit automático, permitindo uma inspeção manual antes da conclusão.

## Ferramentas Visuais
- **git difftool**: Permite a inspeção visual detalhada das diferenças antes de decidir qual versão manter.
- **git mergetool**: Lança uma interface gráfica (GUI) para facilitar a resolução das colisões de código.

## Comunicação com o Autor
Antes de escolher uma versão definitiva em conflitos complexos, o ideal é utilizar o `git blame` para identificar e conversar com o autor original da mudança. Entender a intenção por trás do código evita a perda de funcionalidades importantes.
