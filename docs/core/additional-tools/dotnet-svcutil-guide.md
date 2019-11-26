---
title: Visão geral da ferramenta svcutil do WCF
description: Uma visão geral da ferramenta Microsoft WCF dotnet-svcutil que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta WCF svcutil para projetos do .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 89fe72c8116498ff60d439ce17ef2e857edf621e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771976"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>Ferramenta dotnet-svcutil do WCF para .NET Core

A ferramenta **dotnet-svcutil** do Windows Communication Foundation (WCF) é uma ferramenta da CLI do .NET Core que recupera metadados de um serviço Web em um local de rede ou de um arquivo WSDL e gera uma classe do WCF que contém métodos de proxy cliente que acessam as operações do serviço Web.

Semelhante à ferramenta [**Metadados de Modelo de Serviço - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para projetos .NET Framework, o **dotnet-svcutil** é uma ferramenta de linha de comando para gerar uma referência de serviço Web compatível com projetos .NET Core e .NET Standard.

A ferramenta **dotnet-SvcUtil** é uma opção alternativa para o provedor de serviços conectados do Visual Studio de [**referência do serviço Web WCF**](wcf-web-service-reference-guide.md) que foi fornecido pela primeira vez com o Visual Studio 2017 versão 15,5. A ferramenta **dotnet-svcutil**, como uma ferramenta da CLI do .NET Core, é a multiplataforma disponível no Linux, no macOS e no Windows.

> [!IMPORTANT]
> Você só deve fazer referência a serviços de uma fonte confiável. A adição de referências de uma fonte não confiável pode comprometer a segurança.

## <a name="prerequisites"></a>{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [SDK do .NET Core 2.1](https://dotnet.microsoft.com/download) ou versões posteriores
- Seu editor de código favorito

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [SDK do .NET Core 1.0.4](https://dotnet.microsoft.com/download) ou versões posteriores
- Seu editor de código favorito

---

## <a name="getting-started"></a>Introdução

O exemplo a seguir orienta você pelas etapas necessárias para adicionar uma referência de serviço Web a um projeto Web do .NET Core e chamar o serviço. Você criará um aplicativo Web do .NET Core denominado *HelloSvcutil* e adicionará uma referência a um serviço Web que implementa o seguinte contrato:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Neste exemplo, vamos assumir que o serviço Web será hospedado no seguinte endereço: `http://contoso.com/SayHello.svc`

Em uma janela de comandos do Windows, macOS ou Linux, execute as seguintes etapas:

1. Crie um diretório chamado _HelloSvcutil_ para seu projeto e torne-o seu diretório atual, como no exemplo a seguir:

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Crie um novo projeto Web em C# nesse diretório usando o comando [`dotnet new`](../tools/dotnet-new.md) da seguinte maneira:

    ```dotnetcli
    dotnet new web
    ```

3. Instalar o [pacote do NuGet `dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) como uma ferramenta da CLI:  <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Abra o arquivo de projeto `HelloSvcutil.csproj` em seu editor, edite o elemento `Project` e adicione o pacote [`dotnet-svcutil` do NuGet ](https://nuget.org/packages/dotnet-svcutil) como uma referência à ferramenta da CLI, usando o seguinte código:

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Depois, restaure o pacote _dotnet-svcutil_ usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Execute o comando _dotnet-svcutil_ para gerar o arquivo de referência do serviço Web da seguinte maneira:

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

O arquivo gerado é salvo como _HelloSvcutil/ServiceReference/Reference.cs_. A ferramenta _dotnet-svcutil_ também adiciona ao projeto os pacotes WCF apropriados exigidos pelo código proxy como referências de pacote.

## <a name="using-the-service-reference"></a>Usar a referência de serviço

1. Restaure os pacotes do WCF usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:

    ```dotnetcli
    dotnet restore
    ```

2. Localize o nome da classe do cliente e a operação que você deseja usar. `Reference.cs` conterá uma classe que herda de `System.ServiceModel.ClientBase`, com métodos que podem ser usados para chamar operações no serviço. Neste exemplo, você deseja chamar a operação _Hello_ do serviço _SayHello_. `ServiceReference.SayHelloClient` é o nome da classe do cliente e tem um método chamado `HelloAsync` que pode ser usado para chamar a operação.

3. Abra o arquivo `Startup.cs` em seu editor e adicione uma instrução using para o namespace de referência de serviço na parte superior:

    ```csharp
    using ServiceReference;
    ```

4. Edite o método `Configure` para invocar o serviço Web. Faça isso criando uma instância da classe que herda de `ClientBase` e chamando o método no objeto de cliente:

    ```csharp
    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. Execute o aplicativo usando o comando [`dotnet run`](../tools/dotnet-run.md) da seguinte forma:

    ```dotnetcli
    dotnet run
    ```

6. Navegue até a URL listada no console (por exemplo, `http://localhost:5000`) em seu navegador da Web.

Você deverá ver a seguinte saída: "Hello dotnet-svcutil!"

Para ver uma descrição detalhada dos parâmetros da ferramenta `dotnet-svcutil`, chame a ferramenta passando o parâmetro de ajuda da seguinte forma:
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Perguntas e comentários

Se tiver perguntas ou comentários, [abra um problema no GitHub](https://github.com/dotnet/wcf/issues/new). Você também pode examinar as perguntas ou os problemas existentes [no repositório do WCF no GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Notas de Versão

- Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.

## <a name="information"></a>{1&gt;Informações&lt;1}

- [Pacote do NuGet dotnet-svcutil](https://nuget.org/packages/dotnet-svcutil)
