Para rodar em seu Docker use `touch docker-compose.yaml` para criar arquivo em seu diretório.

Após rode `vi docker-compose.yaml` para editar seu arquivo ".yaml"

Ao entrar na aba de edição, aperte `I` para editar e cole o conteudo de `docker-compose.yaml`, respeitando a identação.

Após colar, aperte `esc` e digite `:wq` + `enter` para salvar.

Agora configurado seu arquivo use `docker-compose up --build -d` para iniciar e `docker-compose down` para parar

Caso queira mudar usuário e senha mude em `docker-compose.yaml`.

Para abrir no navegador, digite "`localhost:80`" na barra de pesquisa.

Existem duas configurações do `Dockerfile` possiveis, uma delas permite que o conteiner seja reiniciado e o histórico de arquivos seja mantido, e outra cada vez que o conteiner é iniciado, é necessário enviar novamente todos os arquivos.
Nesse caso optei por ter que enviar toda vez que inicie o localhost mas deixarei a configuração em que não é necessário documentada em um arquivo `docker-reiniciavel.yaml`.

Configurações tiradas de (https://github.com/orthanc-server/orthanc-setup-samples)
