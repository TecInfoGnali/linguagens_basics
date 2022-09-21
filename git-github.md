# Git Github
### No Git bash

 - Selecione/Crie a pasta principal para comportar os arquivos do GitHub
 - abra a pasta no terminal git bash e execute o comando clone
    > $ git clone <endereçohttps> # o comando cria uma pasta com o nome da pasta no GitHub e importa as informações
 - Faça as alterações necessárias
 - Vá para a pasta onde foi feita a clonagem do repositório
    >$ git status #verifica o status atual das modificações.

    >$ git add . #inclui todas as alterações feitas na pasta local ao repositorio local.

    >$ git commit #Executa a inclusão das alterações (-m "texto" -> cria uma mensagem sobre a alteração executada).

    >$ git push origin main # encaminha as alterações feitas localmente ao endereço contido no origin para o main.

    >$ git pull origin main # pucha as alterações feitas no servidor para o repositorio local.

    >$ git remote -v # verifica a qual servidor remoto o Git esta ligado, informa o apelido desse servidor
