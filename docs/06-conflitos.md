# Estratégias de Resolução de Conflitos

Em merges complexos, podemos usar: 
* **-Xours**: Prioriza nossa versão.
* **-Xtheirs**: Prioriza a versão deles.

## Comandos de Controle
* **git merge --abort**: Cancela o processo de merge e restaura o estado anterior.
* **git merge --no-commit**: Realiza o merge mas não cria o commit automaticamente.

## Ferramentas Visuais
* Use **git mergetool** para abrir ferramentas gráficas como VS Code ou Meld para resolver conflitos.
* A comunicação direta entre desenvolvedores é a melhor forma de evitar perda de dados.
