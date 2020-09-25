---
title: Usar injeção de dependência no .NET
description: Saiba como usar a injeção de dependência em seus aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
ms.openlocfilehash: f2298cb0be6d555a7636903dc251f022a6a62a43
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247879"
---
# <a name="tutorial-use-dependency-injection-in-net"></a>Tutorial: usar injeção de dependência no .NET

Este tutorial mostra como usar [injeção de dependência (di) no .net](dependency-injection.md). Com *o Microsoft Extensions*, di é um cidadão de primeira classe onde os serviços são adicionados e configurados em um <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . A <xref:Microsoft.Extensions.Hosting.IHost> interface expõe a <xref:System.IServiceProvider> instância, que atua como um contêiner de todos os serviços registrados.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> - Criar um aplicativo de console .NET que usa injeção de dependência
> - Criar e configurar um [host genérico](generic-host.md)
> - Escrever várias interfaces e implementações correspondentes
> - Usar o tempo de vida do serviço e o escopo para DI

## <a name="prerequisites"></a>Pré-requisitos

- [SDK do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.
- Um ambiente de desenvolvimento integrado (IDE), [Visual Studio, Visual Studio Code ou Visual Studio para Mac](https://visualstudio.microsoft.com) são opções válidas.
- Familiaridade com a criação de novos aplicativos .NET e a instalação de pacotes NuGet.

## <a name="create-a-new-console-application"></a>Criar um novo aplicativo de console

Usando o comando [dotnet New](../tools/dotnet-new.md) ou um assistente de novo projeto do IDE, crie um novo aplicativo de console .NET chamado **ConsoleDI. example**. Adicione o pacote NuGet [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) ao projeto.

## <a name="add-interfaces"></a>Adicionar interfaces

Adicione as seguintes interfaces ao diretório raiz do projeto:

*IOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

A `IOperation` interface define uma única `OperationId` propriedade.

*ITransientOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

*IScopedOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

*ISingletonOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

Todas as subinterfaces de `IOperation` nome do seu tempo de vida de serviço pretendido. Por exemplo, "transitório" ou "singleton".

## <a name="add-default-implementation"></a>Adicionar implementação padrão

Adicione a seguinte implementação padrão para as várias operações:

*DefaultOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

O `DefaultOperation` implementa todas as interfaces nomeadas/de marcador e inicializa a `OperationId` propriedade para os últimos quatro caracteres de um novo GUID (identificador global exclusivo).

## <a name="add-service-that-requires-di"></a>Adicionar serviço que requer DI

Adicione o seguinte objeto de agente de operação, que atua como um serviço para o aplicativo de console:

*OperationLogger.cs*

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

O `OperationLogger` define um construtor que requer cada uma das interfaces de marcador mencionadas anteriormente, ou seja,, `ITransientOperation` `IScopedOperation` e `ISingletonOperation` . O objeto expõe um único método que permite ao consumidor registrar as operações com um determinado `scope` parâmetro. Quando invocado, o `LogOperations` método registrará em log o identificador exclusivo de cada operação com a cadeia de caracteres e a mensagem do escopo.

## <a name="register-services-for-di"></a>Registrar serviços para DI

Por fim, atualize o arquivo *Program.cs* para corresponder ao seguinte:

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

O aplicativo:

- Cria uma <xref:Microsoft.Extensions.Hosting.IHostBuilder> instância com as [configurações padrão do fichário](generic-host.md#default-builder-settings).
- Configura os serviços e os adiciona com o tempo de vida do serviço correspondente.
- Chama <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> e atribui uma instância do <xref:Microsoft.Extensions.Hosting.IHost> .
- Chamadas `ExemplifyScoping` , passando no <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .

## <a name="conclusion"></a>Conclusão

O aplicativo produz uma saída semelhante ao exemplo a seguir:

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

Na saída do aplicativo, você pode ver que:

- As operações transitórias são sempre diferentes, o que significa que uma nova instância é criada com cada recuperação do serviço.
- As operações com escopo são alteradas somente com um novo escopo, mas são a mesma instância dentro de um escopo.
- As operações singleton são sempre as mesmas, o que significa que uma nova instância é criada apenas uma vez.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Diretrizes de injeção de dependência](dependency-injection-guidelines.md)
