---
title: Faça login com o Azure SDK para .NET
description: Saiba como ativar o registro com o Azure SDK para bibliotecas de clientes .NET
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071986"
---
# <a name="logging-with-the-azure-sdk-for-net"></a>Faça login com o Azure SDK para .NET

O [Azure SDK](https://azure.microsoft.com/downloads/) para bibliotecas de clientes .NET inclui a capacidade de registrar operações de biblioteca de clientes. Isso permite monitorar solicitações e respostas de I/O que as bibliotecas de clientes estão fazendo aos serviços do Azure. Normalmente, os registros são usados para depurar ou diagnosticar problemas de comunicação. Este artigo descreve três abordagens para permitir o registro com o Azure SDK para .NET:

- Faça login na janela do console
- Faça log a rastreamentos de diagnóstico .NET
- Configurar o registro personalizado

> [!IMPORTANT]
> Este artigo se aplica a bibliotecas de clientes que usam as versões mais recentes do Azure SDK para .NET. Para ver se uma biblioteca é suportada, consulte a lista de [versões mais recentes do Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html). Se o seu aplicativo estiver usando uma versão mais antiga das bibliotecas clientes Do Azure SDK, consulte instruções específicas na documentação de serviço aplicável.

## <a name="log-information"></a>Informações do log

O SDK registra as seguintes informações, higienizando a consulta do parâmetro e os valores do cabeçalho para remover dados pessoais.

Entrada de log de solicitação HTTP:

- ID Exclusiva
- Método HTTP
- URI
- Cabeçalhos de solicitação de saída

Entrada do registro de resposta HTTP:

- Duração da operação de I/O (tempo decorrido)
- ID de solicitação
- Código de status HTTP
- Frase de razão HTTP
- Cabeçalhos de resposta
- Informações de erro, quando aplicável

Para conteúdo de solicitação e resposta:

- Fluxo de conteúdo como texto ou bytes, dependendo do cabeçalho tipo de conteúdo.
     > [! NOTA} O registro de conteúdo é desativado por padrão. Para habilitá-lo, configurado `Diagnostics.IsLoggingContentEnabled` para `true` dentro `ClientOptions`.

Os registros de eventos são de saída geralmente em um desses três níveis:

- Informativo para eventos de solicitação e resposta
- Aviso para erros
- Verbose para mensagens detalhadas e registro de conteúdo

## <a name="enable-logging-with-built-in-methods"></a>Habilite o registro com métodos incorporados

O Azure SDK for .NET client libraryes registra eventos para ETW (Event Tracing for Windows) via [ `EventSource` classe](/dotnet/api/system.diagnostics.tracing.eventsource), o que é típico de .NET. As fontes de eventos permitem que você use login estruturado no código do aplicativo com uma sobrecarga mínima de desempenho. Para ter acesso a esses registros de eventos, você precisa registrar ouvintes de eventos.

O SDK inclui `Azure.Core.Diagnostics.AzureEventSourceListener` a classe (definida no pacote Azure.Core NuGet), que contém dois métodos `CreateConsoleLogger` `CreateTraceLogger`estáticos que simplificam o registro abrangente para o seu aplicativo .NET: e . Esses métodos tomam um parâmetro opcional que especifica um nível de registro.

### <a name="log-to-the-console-window"></a>Faça login na janela do console

Um princípio central do Azure SDK para bibliotecas de clientes .NET é simplificar a capacidade de visualizar logs abrangentes em tempo real. O `CreateConsoleLogger` método permite enviar logs para a janela do console com uma única linha de código:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a>Log para rastreamentos de diagnóstico

Se você implementar ouvintes de `CreateTraceLogger` rastreamento, poderá usar o método para[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)registrar o mecanismo padrão de rastreamento de eventos .NET (). Para obter mais informações sobre o rastreamento de eventos em .NET, consulte [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners). Este exemplo especifica um nível de log de verbose:

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a>Configurar o registro personalizado

Como mencionado acima, você precisa registrar ouvintes de eventos para receber mensagens de log do Azure SDK para .NET. Se você não quiser implementar um registro abrangente usando um dos métodos simplificados acima, você pode construir uma instância da classe e passar-lhe `AzureEventSourceListener` uma função de retorno de chamada que você escreve. Este método receberá mensagens de registro que você pode processar como for necessário. Além disso, ao construir a instância, você pode especificar os níveis de registro a serem incluemos.

O exemplo a seguir cria um ouvinte de eventos que faz logon no console com uma mensagem personalizada e é filtrado para eventos principais do Azure do verbose de nível.

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a>Próximas etapas

- [Habilite o registro de diagnósticos para aplicativos no Azure App Service](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- Revise as opções [de registro e auditoria de segurança do Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)
- Saiba como trabalhar com os logs da [plataforma Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)
- Leia mais sobre [o registro e rastreamento do .NET Core](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)
