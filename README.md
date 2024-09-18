# speech-to-fast-readme-pub

## Objetivo

Demonstrar o uso da transcrição na API speech-to-fast

## Pré-requisitos

1. Uma API Key válida (```X-API-KEY```). Solicitar para um contato da InfoPrise via e-mail, whats ou [abrindo uma issue](https://github.com/InfoPrise/speech-to-fast-readme-pub/issues/new).

## URL

https://api.speechtofast.com.br/speech-to-fast/swagger-ui/index.html

### Demonstração de transcrição

> Se preferir acesse uma demonstração por vídeo em [🚧 em gravação no momento 🚧](): 

![Screenshot 2024-09-18 at 14-06-18 Swagger UI](https://github.com/user-attachments/assets/b3e72b2d-873a-45b4-b59a-49f2eb34b15a)

#### Acessar o Swagger

1. Acessar o link do endpoint no Swagger https://api.speechtofast.com.br/speech-to-fast/swagger-ui/index.html#/Transcriptions/upload /v1/speech-to-fast

#### Configurar a API Key

1. Cadastrar no swagger a ```X-API-KEY``` fornecida pela InfoPrise
![00_auth_x-api-key_2024091814h02](https://github.com/user-attachments/assets/6e300541-351f-4bc6-85e5-7ffc2f202613)

#### Realizar um upload

1. Realizar o upload de uma mídia de aúdio/vídeo
>⚠️ Devido à um bug recente, enviar uma mídia sem acentos ou espaços. Exemplo: demo-midia-infoprise.mp3, 2024-09-18-CANAL-XPTO-Jornal-da-Madrugada.wmv, 20240918141053500.wma, 20240918141053500CANALXPTO.wma, etc
2. No Response Body, coletar o valor de fullFileName. Exemplo: ```Transcription created with ObjectId=66eb07d5aa5cd025e1f92e23 and fullFileName=demo-midia-infoprise.mp3```, coletar ```demo-midia-infoprise.mp3```

![01_demo-upload_2024091814h02](https://github.com/user-attachments/assets/3690d041-0f22-4ea0-acd4-a0d4602dc783)

#### Coletar manualmente a transcrição

> O uso de pooling para obtenção da transcrição é apenas para fins de demonstração. Para consumo de APIs externas, temos um webhook para retornar no término da transcrição o resultado dela. 

1. Com o fullFileName, consulte se a API terminou a transcrição
> Por esse método, um arquivo de vídeo .wmv de 10 minutos é convertido em cerca de 1m22s

![02_manual-get-transcription_2024091814h02](https://github.com/user-attachments/assets/7e61e304-1108-4074-83d5-8b4e57eef269)


### Uso para HML/PRD

> 🚧 Realizando tutorial para uso em HML/PRD.

O consumo indicado para HML/PRD muda somente na forma de upload e na não necessidade de pooling (devido o webhook)

A API speech-to-fast usa urls pré-assinadas para o envio da mídia a ser transcrita para tirar o máximo proveito do upload do lado do cliente que tem a possibilidade de paralelizar essa tarefa.
Assim que o upload finaliza, a fila de processamento é iniciada e ao término da transcrição, um POST Webhook é enviado para a URL e Headers que o cliente cadastrar na API
