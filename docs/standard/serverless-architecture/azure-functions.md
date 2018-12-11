---
title: Funções do Azure – aplicativos sem servidor
description: O Azure functions fornece funcionalidades sem servidor em vários idiomas (c#, JavaScript, Java) e plataformas para fornecer controlada por evento instantâneas dimensionar o código.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 2d8729276a5797bd8b89c39d8fb03c6f20646ea0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145157"
---
# <a name="azure-functions"></a>Verificação de

O Azure functions fornece uma experiência de computação sem servidor. Uma função é invocada por um *disparador* (como acesso a um ponto de extremidade HTTP ou um temporizador) e executa um bloco de código ou a lógica comercial. Funções também suporte especializado *associações* que se conectam a recursos como armazenamento e filas.

![Logotipo do Azure functions](./media/azure-functions-logo.png)

Há duas versões do framework do Azure Functions. A versão herdada dá suporte ao .NET Framework completo e o novo tempo de execução dá suporte a aplicativos do .NET Core de plataforma cruzada. Idiomas adicionais além do C# , como JavaScript, F#, e Java são suportados. As funções criadas no portal do fornecem uma sintaxe de script avançada. Funções criadas como projetos autônomos podem ser implantadas com os recursos e suporte de plataforma completo.

Para obter mais informações, consulte [documentação do Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funções v1 e v2

Há duas versões do tempo de execução do Azure Functions: 1.x e 2.x. Versão 1.x já está disponível (GA). Ele dá suporte ao desenvolvimento de .NET do portal ou as máquinas do Windows e usa o .NET Framework. 1.x dá suporte ao C#, JavaScript, e F#, com o suporte experimental para Python, PHP, TypeScript, Batch, Bash e PowerShell.

Versão 2.x está em versão prévia. Ele aproveita o .NET Core e dá suporte ao desenvolvimento de plataforma cruzada em máquinas Linux, macOS e Windows. 2.x adiciona suporte de primeira classe para Java, mas não ainda suporta diretamente qualquer uma das linguagens experimentais. Versão 2.x usa um novo modelo de extensibilidade de associação que permite que extensões de terceiros para a plataforma, o controle de versão independente de associações, e uma mais simples de ambiente de execução.

> **Há um problema conhecido no 1.x com [suporte de redirecionamento de associação](https://github.com/Azure/azure-functions-host/issues/992).** O problema é específico para o desenvolvimento de .NET. Projetos com dependências em bibliotecas que são uma versão diferente do que as bibliotecas incluídas no tempo de execução são afetados. A equipe de funções se comprometeu a progredindo concretas sobre o problema. A equipe abordará os redirecionamentos de associação no 2.x antes que ele fique em disponibilidade geral. A declaração oficial da equipe com correções sugeridas e soluções alternativas está disponível aqui: [Resolução de assembly no Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Para obter mais informações, consulte [comparar 1.x e 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Suporte de linguagem de programação

Os idiomas a seguir têm suporte em geral GA (disponibilidade), visualizar, ou experimental.

|Idioma      |1. x         |2. x      |
|--------------|------------|---------|
|**C#**        |GA          |Visualizar  |
|**JavaScript**|GA          |Visualizar  |
|**F#**        |GA          |         |
|**Java**      |            |Visualizar  |
|**Python**    |Habilitação|         |
|**PHP**       |Habilitação|         |
|**TypeScript**|Habilitação|         |
|**Lote**     |Habilitação|         |
|**Bash**      |Habilitação|         |
|**PowerShell**|Habilitação|         |

Para obter mais informações, consulte [idiomas com suporte](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Planos de serviço de aplicativo

Funções são apoiadas por um *plano do serviço de aplicativo*. O plano define os recursos usados pelo aplicativo de funções. Você pode atribuir os planos para uma região, determinar o tamanho e o número de máquinas virtuais que serão usadas e escolher um tipo de preço. Para uma verdadeira abordagem sem servidor, aplicativos de funções podem usar o **consumo** plano. O plano de consumo escala automaticamente com base na carga de back-end.

Para obter mais informações, consulte [planos de serviço de aplicativo](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Criar sua primeira função

Há três maneiras comuns que você pode criar aplicativos de funções.

* Funções de script no portal.
* Crie os recursos necessários usando a Interface de linha de comando (CLI) do Azure.
* Crie funções localmente usando seu IDE favorito e publicá-los para o Azure.

Para obter mais informações sobre como criar uma função de script no portal, consulte [criar sua primeira função no portal do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Para compilar a partir da CLI do Azure, consulte [criar sua primeira função usando a CLI do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Para criar uma função do Visual Studio, consulte [criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Entender os gatilhos e associações

As funções são chamadas por um *disparador* e pode ter exatamente um. Além de chamar a função, determinados disparadores também servem como associações. Você também pode definir várias associações, além de gatilho. *Associações* fornecem uma maneira declarativa para se conectar a dados ao seu código. Eles podem ser passados em (entrada) ou recebem dados (saída). Gatilhos e associações tornam fácil trabalhar com funções. Associações de remover a sobrecarga de criar manualmente banco de dados ou arquivo de conexões de sistema. Todas as informações necessárias para as ligações estão contidas em um especial *Functions* de arquivos para scripts ou declarados com atributos no código.

Alguns gatilhos comuns incluem:

* Armazenamento de BLOBs: chama sua função quando um arquivo ou pasta for carregada ou alterada no armazenamento.
* HTTP: chama sua função como uma API REST.
* Fila: chama sua função quando existem itens em uma fila.
* Temporizador: chama sua função em um ritmo regular.

Exemplos de associações:

* CosmosDB: facilmente se conecte ao banco de dados para carregar ou salvar arquivos.
* O armazenamento de tabela: trabalhar com o armazenamento de chave/valor de seu aplicativo de funções.
* O armazenamento de filas: facilmente recuperar itens de uma fila ou colocar novos itens na fila.

O exemplo a seguir *Functions* arquivo define um gatilho e uma associação:

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

Neste exemplo, a função é disparada por uma alteração no armazenamento de BLOBs no `images` contêiner. As informações para o arquivo são passadas, portanto, o gatilho também atua como uma associação. Outra associação existe para colocar as informações em uma fila denominada `images`.

Aqui está o script do c# para a função:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

O exemplo é uma função simples que usa o nome do arquivo que foi modificada ou carregados no armazenamento de BLOBs e coloca-o em uma fila para processamento posterior.

Para obter uma lista completa dos gatilhos e associações, consulte [conceitos de associações e gatilhos do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxies

Proxies fornecem a funcionalidade de redirecionamento para seu aplicativo. Proxies expõem um ponto de extremidade e mapeiam esse ponto de extremidade para outro recurso. Com proxies, você pode:

* Redirecionar uma solicitação de entrada para outro ponto de extremidade.
* Modificar a solicitação de entrada antes de ser passado ao longo.
* Modificar ou fornecer uma resposta.

Os proxies são usados para cenários como:

* Simplificando, encurtando ou alterar a URL.
* Fornecendo um prefixo de API consistente para vários serviços de back-end.
* Simulação de uma resposta a um ponto de extremidade que está sendo desenvolvido.
* Fornecendo uma resposta de estática para um ponto de extremidade conhecido.
* Mantendo um ponto de extremidade de API consistente enquanto o back-end é movido ou migrado.

Os proxies são armazenados como definições de JSON. Veja um exemplo:

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

O `Domain Redirect` proxy usa uma rota reduzida e mapeia-os para o recurso de função mais tempo. A transformação é semelhante a:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

O `Root` proxy usa qualquer coisa enviadas para a URL da raiz (`https://--shorturl--/`) e o redireciona para o site de documentação.

Um exemplo do uso de proxies é mostrado no vídeo [Azure: Traga o seu aplicativo para a nuvem com o Azure Functions sem servidor](https://channel9.msdn.com/events/Connect/2017/E102). Em tempo real, um aplicativo ASP.NET Core em execução no SQL Server local é migrado para a nuvem do Azure. Os proxies são usados para ajudar a refatorar um projeto de API da Web tradicional para usar funções.

Para obter mais informações sobre Proxies, consulte [trabalhar com Proxies do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Anterior](azure-serverless-platform.md)
>[Próximo](application-insights.md)