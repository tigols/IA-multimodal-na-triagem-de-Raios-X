# IA-multimodal-na-triagem-de-Raios-X

Inicialmente eu ja tinha uma idéia do funcionamento de Docker mas nunca tinha trabalhado ativamente com ele. Aprendi os conceitos de imagens e o funcionamento delas. Em um primeiro momento rodei manualmente pelo WSL os comandos para rodar a imagem no localhost, dias depois aprendi a configurar um arquivo para que ele faça todos os passos em apenas um comando (Ver pasta `Docker`).

Em seguida, com a PACS OrthanC rodando no `localhost`, precisei criar um arquivo para enviar as imagens, primeiramente tive dificuldade com o request mas vom pouca pesquisa eu entendi como funcionava e saiu rápido o envio das imagens.

Uma das etapas mais demorada foi a classificação. Nos primeiros dias estava dando erro na biblioteca pois a ultima versão do "torch" estava aparentemente faltando um `.dll`, o problema é discutido nesse fórum (https://github.com/pytorch/pytorch/issues/131662#issuecomment-2252589253), após muito tempo baixando e excluindo bibliotecas, .dlls e usando versões antigas de bibliotecas, o script conseguiu importar as bibliotecas necessárias.

Após ler as imagens, ao colocá-las diretamente no objeto que carregava o modelo, percebi que as imagens precisavam de algum tratamento prévio, em questão de dimensões e valores da matriz da imagem. Pelo o que entendi as imagens apresentavam apenas 2 canais e o modelo pedia 4 (os 2 canais faltantes seriam o `batch` e o `chanel` pelo o que pesquisei), após tratar as imagens, o modelo rodou normalmente. A criação do arquivo `.json` com as saídas do modelo se encontra no arquivo `classificação.json`.

Outra etapa demorada foi a criação dos `DICOM Structured Report` pois é uma estrutura que nunca tinha visto e que tem uma maneira aparentemente única de ser escrita. Nessa etapa não achei muito conteúdo no YT que me ajudasse a fazer os reports em python, então usei bastante o ChatGPT para entender cada argumento do `DICOM SR`. Ainda não tenho certeza se está na formatação correta os reports mas os resultados estão corretos e correspondente a cada imagem de cada série/estudo/id.

Acredito que aprendi muito sobre conteiners e sua utilização, sobre upload de arquivos e trabalhar com caminhos no sistema operacional, mas acho que o que mais desenvolvi foi a habilidade de procurar por soluções para problemas se não idênticos, semelhantes, em fóruns na internet. Stackoverflow, GitHub e Youtube foram locais onde mais achei a solução para partes onde me senti travado.
