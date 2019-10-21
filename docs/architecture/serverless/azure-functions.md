---
title: Aplicativos Azure Functions-sem servidor
description: O Azure Functions fornece recursos sem servidor em váriosC#idiomas (, JavaScript, Java) e plataformas para fornecer código de escala instantânea controlado por eventos.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5e8187b3752a0f0d0bcf8e15f2ce440dc5a64e45
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522874"
---
# <a name="azure-functions"></a>Verificação de

O Azure Functions fornece uma experiência de computação sem servidor. Uma função é invocada por um *gatilho* (como o acesso a um ponto de extremidade http ou um temporizador) e executa um bloco de código ou lógica de negócios. As funções também dão suporte a *associações* especializadas que se conectam a recursos como armazenamento e filas.

![Logotipo do Azure Functions](./media/azure-functions-logo.png)

Há duas versões do Azure Functions Framework. A versão herdada dá suporte ao .NET Framework completo e o novo tempo de execução dá suporte a aplicativos .NET Core de plataforma cruzada. Há suporte para C# idiomas adicionais, além F#de JavaScript, e Java. As funções criadas no portal fornecem uma sintaxe de script avançada. As funções criadas como projetos autônomos podem ser implantadas com recursos e suporte completos à plataforma.

Para obter mais informações, consulte a [documentação do Azure Functions](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funções V1 versus V2

Há duas versões do tempo de execução de Azure Functions: 1. x e 2. x. A versão 1. x está disponível para o público geral (GA). Ele dá suporte ao desenvolvimento .NET do portal ou de máquinas Windows e usa o .NET Framework. 1. x dá C#suporte a, JavaScript F#e, com suporte experimental para Python, PHP, TypeScript, lote, bash e PowerShell.

A [versão 2. x também está geralmente disponível agora](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Ele aproveita o .NET Core e dá suporte ao desenvolvimento de plataforma cruzada em computadores Windows, macOS e Linux. 2. x adiciona o suporte de primeira classe para Java, mas ainda não dá suporte diretamente a qualquer uma das linguagens experimentais. A versão 2. x usa um novo modelo de extensibilidade de associação que permite extensões de terceiros para a plataforma, controle de versão independente de associações e um ambiente de execução mais simplificado.

> **Há um problema conhecido em 1. x com [suporte para redirecionamento de associação](https://github.com/Azure/azure-functions-host/issues/992).** O problema é específico do desenvolvimento do .NET. Os projetos com dependências em bibliotecas que são uma versão diferente das bibliotecas incluídas no tempo de execução são afetados. A equipe de funções se comprometeu a fazer o progresso concreto do problema. A equipe abordará redirecionamentos de associação em 2. x antes de entrar em disponibilidade geral. A declaração de equipe oficial com correções e soluções alternativas sugeridas está disponível aqui: [resolução de assembly em Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Para obter mais informações, consulte [comparar 1. x e 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Suporte à linguagem de programação

Os idiomas a seguir têm suporte em disponibilidade geral (GA), visualização ou experimental.

|Linguagem      |1.x         |2.x      |
|--------------|------------|---------|
|**C#**        |3º          |Visualizar  |
|**JavaScript**|3º          |Visualizar  |
|**F#**        |3º          |         |
|**Java**      |            |Visualizar  |
|**Python**    |Habilitação|         |
|**DESTINADOS**       |Habilitação|         |
|**TypeScript**|Habilitação|         |
|**Lote**     |Habilitação|         |
|**Raso**      |Habilitação|         |
|**PowerShell**|Habilitação|         |

Para obter mais informações, consulte [idiomas com suporte](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Planos do serviço de aplicativo

As funções são apoiadas por um *plano do serviço de aplicativo*. O plano define os recursos usados pelo aplicativo de funções. Você pode atribuir planos a uma região, determinar o tamanho e o número de máquinas virtuais que serão usadas e escolher um tipo de preço. Para uma abordagem verdadeira sem servidor, os aplicativos de função podem usar o plano de **consumo** . O plano de consumo dimensionará o back-end automaticamente com base na carga.

Para obter mais informações, consulte [planos do serviço de aplicativo](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Criar sua primeira função

Há três maneiras comuns de criar aplicativos de funções.

- Funções de script no Portal.
- Crie os recursos necessários usando a CLI (interface de linha de comando) do Azure.
- Crie funções localmente usando seu IDE favorito e publique-as no Azure.

Para obter mais informações sobre como criar uma função com script no portal, consulte [criar sua primeira função no portal do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Para criar a partir do CLI do Azure, consulte [criar sua primeira função usando o CLI do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Para criar uma função do Visual Studio, consulte [criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Entender gatilhos e associações

As funções são invocadas por um *gatilho* e podem ter exatamente uma. Além de invocar a função, determinados gatilhos também servem como associações. Você também pode definir várias associações além do gatilho. As *associações* fornecem uma maneira declarativa de conectar dados ao seu código. Eles podem ser passados (entrada) ou receber dados (saída). Os gatilhos e as associações facilitam o trabalho com as funções. As associações removem a sobrecarga de criar manualmente as conexões do banco de dados ou do sistema de arquivos. Todas as informações necessárias para as associações estão contidas em um arquivo *functions. JSON* especial para scripts ou declarados com atributos no código.

Alguns gatilhos comuns incluem:

- Armazenamento de BLOBs: invoque sua função quando um arquivo ou pasta for carregado ou alterado no armazenamento.
- HTTP: invoque sua função como uma API REST.
- Fila: invoque sua função quando houver itens em uma fila.
- Temporizador: invocar sua função em uma cadência regular.

Exemplos de associações incluem:

- CosmosDB: Conecte-se facilmente ao banco de dados para carregar ou salvar arquivos.
- Armazenamento de tabelas: trabalhe com o armazenamento de chave/valor do seu aplicativo de funções.
- Armazenamento de filas: recuperar facilmente itens de uma fila ou colocar novos itens na fila.

O arquivo *functions. JSON* de exemplo a seguir define um gatilho e uma associação:

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

Neste exemplo, a função é disparada por uma alteração no armazenamento de BLOBs no contêiner de `images`. As informações para o arquivo são passadas para que o gatilho também atue como uma associação. Existe outra associação para colocar informações em uma fila chamada `images`.

Este é o C# script para a função:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

O exemplo é uma função simples que usa o nome do arquivo que foi modificado ou carregado no armazenamento de BLOBs e o coloca em uma fila para processamento posterior.

Para obter uma lista completa de gatilhos e associações, consulte [Azure Functions os conceitos de gatilhos e associações](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxies

Os proxies fornecem funcionalidade de redirecionamento para seu aplicativo. Os proxies expõem um ponto de extremidade e mapeiam esse ponto de extremidade para outro recurso. Com proxies, você pode:

- Redirecionar uma solicitação de entrada para outro ponto de extremidade.
- Modifique a solicitação de entrada antes de ela ser passada.
- Modifique ou forneça uma resposta.

Os proxies são usados para cenários como:

- Simplificando, reduzindo ou alterando a URL.
- Fornecer um prefixo de API consistente para vários serviços de back-end.
- Simulação de uma resposta a um ponto de extremidade que está sendo desenvolvido.
- Fornecer uma resposta estática para um ponto de extremidade bem conhecido.
- Manter um ponto de extremidade de API consistente enquanto o back-end é movido ou migrado.

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

O proxy de `Domain Redirect` usa uma rota reduzida e a mapeia para o recurso de função mais longo. A transformação é semelhante a:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

O proxy de `Root` faz algo enviado para a URL raiz (`https://--shorturl--/`) e o redireciona para o site de documentação.

Um exemplo de uso de proxies é mostrado no vídeo [Azure: Traga seu aplicativo para a nuvem com Azure Functions sem servidor](https://channel9.msdn.com/events/Connect/2017/E102). Em tempo real, um aplicativo ASP.NET Core em execução no SQL Server local é migrado para a nuvem do Azure. Os proxies são usados para ajudar a refatorar um projeto de API Web tradicional para usar funções.

Para obter mais informações sobre proxies, consulte [trabalhar com proxies do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Anterior](azure-serverless-platform.md)
>[Próximo](application-insights.md)
