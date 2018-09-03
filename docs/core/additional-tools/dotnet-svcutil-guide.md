---
title: Ferramenta Microsoft WCF dotnet-svcutil
description: Uma visão geral da ferramenta Microsoft WCF dotnet-svcutil que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta WCF svcutil para projetos do .NET Framework.
author: mlacouture
ms.author: jralexander
ms.date: 08/20/2018
ms.openlocfilehash: bb4d8e5f3997318b720535b0f1e07fc33d13338a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484115"
---
# <a name="microsoft-wcf-dotnet-svcutil-tool"></a>Ferramenta Microsoft WCF dotnet-svcutil

A ferramenta **dotnet-svcutil** do Windows Communication Foundation (WCF) é uma ferramenta da CLI do .NET Core que recupera metadados de um serviço Web em um local de rede ou de um arquivo WSDL e gera uma classe do WCF que contém métodos de proxy cliente que acessam as operações do serviço Web.

Semelhante à ferramenta [**Metadados de Modelo de Serviço - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para projetos .NET Framework, o **dotnet-svcutil** é uma ferramenta de linha de comando para gerar uma referência de serviço Web compatível com projetos .NET Core e .NET Standard.

A ferramenta **dotnet-svcutil** é uma opção alternativa ao provedor de serviços conectados do Visual Studio [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) que foi primeiramente fornecido com o Visual Studio 2017 v15.5. A ferramenta **dotnet-svcutil**, como uma ferramenta da CLI do .NET Core, é a multiplataforma disponível no Linux, no macOS e no Windows.

> [!IMPORTANT]
> Você só deve fazer referência a serviços de uma fonte confiável. A adição de referências de uma fonte não confiável pode comprometer a segurança.

## <a name="prerequisites"></a>Pré-requisitos

* [.NET Core SDK](https://www.microsoft.com/net/download) v1.0.4 ou versões posteriores
* Seu editor de código favorito

## <a name="getting-started"></a>Introdução

O exemplo a seguir orienta você pelas etapas necessárias para adicionar uma referência de serviço Web a um projeto de console .NET Core e chamar o serviço. Você criará um aplicativo de console .NET Core denominado _HelloSvcutil_ e adicionará uma referência a um serviço Web que implementa o seguinte contrato:

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Neste exemplo, considera-se que o serviço Web será hospedado no seguinte endereço: `http://contoso.com/SayHello.svc`

Em uma janela de comandos do Windows, macOS ou Linux, execute as seguintes etapas:

1. Crie um diretório chamado _HelloSvcutil_ para seu projeto e torne-o seu diretório atual, como no exemplo a seguir:

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. Crie um novo projeto do console C# nesse diretório usando o comando [`dotnet new`](../tools/dotnet-new.md) da seguinte maneira:

```console
dotnet new console
```

3. Abra o arquivo de projeto `HelloSvcutil.csproj` em seu editor, edite o elemento `Project` e adicione o pacote [`dotnet-svcutil` do NuGet ](https://nuget.org/packages/dotnet-svcutil) como uma referência à ferramenta da CLI, usando o seguinte código:

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. Restaure o pacote _dotnet-svcutil_ usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:

```console
dotnet restore
```

5. Execute _dotnet_ com o comando _svcutil_ para gerar o arquivo de referência de serviço Web da seguinte maneira:

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
O arquivo gerado é salvo como _HelloSvcutil/ServiceReference1/Reference.cs_. A ferramenta _dotnet_svcutil_ também adiciona ao projeto os pacotes WCF apropriados exigidos pelo código proxy como referências de pacotes.

6. Restaure os pacotes do WCF usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:

```console
dotnet restore
```

7. Abra o arquivo `Program.cs` em seu editor, edite o método `Main()` e substitua o código gerado automaticamente pelo código a seguir para chamar o serviço Web:

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. Execute o aplicativo usando o comando [`dotnet run`](../tools/dotnet-run.md) da seguinte forma:

```console
dotnet run
```
Você deverá ver a seguinte saída: "Hello dotnet-svcutil!"

Para ver uma descrição detalhada dos parâmetros da ferramenta `dotnet-svcutil`, chame a ferramenta passando o parâmetro de ajuda da seguinte forma:

```console
dotnet svcutil --help
```

## <a name="next-steps"></a>Próximas etapas

### <a name="feedback--questions"></a>Perguntas e comentários

Se tiver perguntas ou comentários, [abra um problema no GitHub](https://github.com/dotnet/wcf/issues/new). Você também pode examinar as perguntas ou os problemas existentes [no repositório do WCF no GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

### <a name="release-notes"></a>Notas de Versão

* Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.

### <a name="information"></a>Informações

* [Pacote do NuGet dotnet-svcutil](https://nuget.org/packages/dotnet-svcutil)
