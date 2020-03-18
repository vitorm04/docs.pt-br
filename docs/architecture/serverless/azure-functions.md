---
title: Funções do Azure - Aplicativos sem servidor
description: As funções do Azure fornecem recursos sem servidor em vários idiomas (C#, JavaScript, Java) e plataformas para fornecer código de escala instantânea orientado a eventos.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401609"
---
# <a name="azure-functions"></a>Funções do Azure

As funções do Azure proporcionam uma experiência de computação sem servidor. Uma função é invocada por um *gatilho* (como acesso a um ponto final HTTP ou um temporizador) e executa um bloco de código ou lógica de negócios. As funções também suportam *vinculações especializadas* que se conectam a recursos como armazenamento e filas.

![Logotipo de funções do Azure](./media/azure-functions-logo.png)

Existem duas versões da estrutura de Funções do Azure. A versão herdada suporta o Framework .NET completo e o novo tempo de execução suporta aplicativos .NET Core multiplataforma. Linguagens adicionais além de C# como JavaScript, F#e Java são suportadas. As funções criadas no portal fornecem uma rica sintaxe de scripts. Funções criadas como projetos autônomos podem ser implantadas com suporte e recursos completos da plataforma.

Para obter mais informações, consulte [a documentação funções do Azure](https://docs.microsoft.com/azure/azure-functions).

## <a name="functions-v1-vs-v2"></a>Funções v1 vs. v2

Existem duas versões do tempo de execução das funções do Azure: 1.x e 2.x. A versão 1.x está geralmente disponível (GA). Ele suporta o desenvolvimento .NET a partir do portal ou máquinas Windows e usa o .NET Framework. O 1.x suporta C#, JavaScript e F#, com suporte experimental para Python, PHP, TypeScript, Batch, Bash e PowerShell.

[A versão 2.x também está geralmente disponível agora](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/). Ele aproveita o .NET Core e suporta o desenvolvimento entre plataformas em máquinas Windows, macOS e Linux. 2.x adiciona suporte de primeira classe para Java, mas ainda não suporta diretamente nenhuma das linguagens experimentais. A versão 2.x usa um novo modelo de extensibilidade de vinculação que permite extensões de terceiros à plataforma, versão independente de vinculações e um ambiente de execução mais simplificado.

> **Há um problema conhecido em 1.x com [suporte de redirecionamento de vinculação](https://github.com/Azure/azure-functions-host/issues/992).** O problema é específico para o desenvolvimento .NET. Projetos com dependências de bibliotecas que são uma versão diferente das bibliotecas incluídas no tempo de execução são impactados. A equipe de funções se comprometeu a fazer progressos concretos sobre o problema. A equipe abordará redirecionamentos de vinculação em 2.x antes de entrar em disponibilidade geral. A declaração oficial da equipe com correções e soluçãos sugeridas está disponível aqui: [Resolução da montagem em Funções Azure](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).

Para obter mais informações, consulte [Compare 1.x e 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).

## <a name="programming-language-support"></a>Suporte à linguagem de programação

Os idiomas a seguir são suportados em disponibilidade geral (GA), visualização ou experimental.

|Linguagem      |1.x         |2. x      |
|--------------|------------|---------|
|**C #**        |GA          |Visualização  |
|**Javascript**|GA          |Visualização  |
|**F #**        |GA          |         |
|**Java**      |            |Visualização  |
|**Python**    |Experimental|         |
|**Php**       |Experimental|         |
|**TypeScript**|Experimental|         |
|**Batch**     |Experimental|         |
|**Bash**      |Experimental|         |
|**Powershell**|Experimental|         |

Para obter mais informações, consulte [idiomas suportados](https://docs.microsoft.com/azure/azure-functions/supported-languages).

## <a name="app-service-plans"></a>Planos de serviço de aplicativos

As funções são apoiadas por um *plano de serviço de aplicativo.* O plano define os recursos utilizados pelo aplicativo de funções. Você pode atribuir planos a uma região, determinar o tamanho e o número de máquinas virtuais que serão usadas e escolher um nível de preço. Para uma abordagem sem servidor, os aplicativos de função podem usar o plano **de consumo.** O plano de consumo irá dimensionar o back-end automaticamente com base na carga.

Para obter mais informações, consulte [os planos de serviço do App](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).

## <a name="create-your-first-function"></a>Criar sua primeira função

Existem três maneiras comuns de criar aplicativos de função.

- O script funciona no portal.
- Crie os recursos necessários usando o Azure CLI.
- Crie funções localmente usando seu IDE favorito e publique-as no Azure.

Para obter mais informações sobre a criação de uma função de script no portal, consulte [Criar sua primeira função no portal Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).

Para construir a partir do Cli azure, consulte [Criar sua primeira função usando o Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).

Para criar uma função no Visual Studio, consulte [Criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).

## <a name="understand-triggers-and-bindings"></a>Entenda os gatilhos e ligações

As funções são invocadas por um *gatilho* e podem ter exatamente uma. Além de invocar a função, certos gatilhos também servem como ligações. Você também pode definir várias ligações além do gatilho. *As vinculações* fornecem uma maneira declarativa de conectar dados ao seu código. Eles podem ser passados (entrada) ou receber dados (saída). Gatilhos e amarras facilitam o trabalho. As vinculações removem a sobrecarga da criação manual de conexões de banco de dados ou sistema de arquivos. Todas as informações necessárias para as vinculações estão contidas em um arquivo *special functions.json* para scripts ou declaradas com atributos em código.

Alguns gatilhos comuns incluem:

- Blob Storage: invoque sua função quando um arquivo ou pasta for carregado ou alterado no armazenamento.
- HTTP: invoque sua função como uma API REST.
- Fila: invoque sua função quando os itens existirem em uma fila.
- Temporizador: invoque sua função em uma cadência regular.

Exemplos de vinculações incluem:

- CosmosDB: conecte-se facilmente ao banco de dados para carregar ou salvar arquivos.
- Armazenamento de tabela: trabalhe com armazenamento de chave/valor do seu aplicativo de função.
- Armazenamento na fila: recupere facilmente itens de uma fila ou coloque novos itens na fila.

O exemplo a seguir *funções.json* arquivo define um gatilho e uma vinculação:

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

Neste exemplo, a função é acionada por uma alteração `images` para o armazenamento de bolhas no recipiente. As informações para o arquivo são passadas, então o gatilho também age como uma vinculação. Existe outra vinculação para colocar informações `images`em uma fila chamada .

Aqui está o script C# para a função:

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

O exemplo é uma função simples que leva o nome do arquivo que foi modificado ou carregado para armazenamento blob, e coloca-o em uma fila para processamento posterior.

Para obter uma lista completa de gatilhos e vinculações, consulte [Os gatilhos e conceitos de vinculações do Azure](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).

## <a name="proxies"></a>Proxies

Os proxies fornecem funcionalidade de redirecionamento para o seu aplicativo. Proxies expõem um ponto final e mapeiam esse ponto final para outro recurso. Com proxies, você pode:

- Redirecione uma solicitação recebida para outro ponto final.
- Modifique a solicitação de entrada antes de ser transmitida.
- Modifique ou forneça uma resposta.

Proxies são usados para cenários como:

- Simplificando, encurtando ou alterando a URL.
- Fornecendo um prefixo de API consistente para vários serviços back-end.
- Zombando de uma resposta a um ponto final sendo desenvolvido.
- Fornecendo uma resposta estática a um ponto final bem conhecido.
- Manter um ponto final de API consistente enquanto a parte traseira é movida ou migrada.

Os proxies são armazenados como definições JSON. Veja um exemplo:

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

O `Domain Redirect` proxy pega uma rota encurtada e mapeia-a para o recurso de função mais longa. A transformação parece:

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

O `Root` proxy pega qualquer coisa`https://--shorturl--/`enviada para a URL raiz ( ) e redireciona-a para o site de documentação.

Um exemplo de uso de proxies é mostrado no vídeo [Azure: Traga seu aplicativo para a nuvem com funções azure sem servidor](https://channel9.msdn.com/events/Connect/2017/E102). Em tempo real, um aplicativo ASP.NET Core em execução no SQL Server local é migrado para a Nuvem Azure. Os proxies são usados para ajudar a refatorar um projeto de API web tradicional para usar funções.

Para obter mais informações sobre proxies, consulte [Trabalhe com Proxies de Funções Azure](https://docs.microsoft.com/azure/azure-functions/functions-proxies).

>[!div class="step-by-step"]
>[Próximo](azure-serverless-platform.md)
>[anterior](application-insights.md)
