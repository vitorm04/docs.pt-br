---
title: Visão geral da ferramenta svcutil do WCF – .NET Core
description: Uma visão geral da ferramenta Microsoft WCF dotnet-svcutil que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta WCF svcutil para projetos do .NET Framework.
author: mlacouture
ms.author: jralexander
ms.date: 08/20/2018
ms.custom: seodec18
ms.openlocfilehash: 7372d88a9c1d77ec0b77e9d82fe5b24ebc357a74
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126010"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="4df2d-103">Ferramenta dotnet-svcutil do WCF para .NET Core</span><span class="sxs-lookup"><span data-stu-id="4df2d-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="4df2d-104">A ferramenta **dotnet-svcutil** do Windows Communication Foundation (WCF) é uma ferramenta da CLI do .NET Core que recupera metadados de um serviço Web em um local de rede ou de um arquivo WSDL e gera uma classe do WCF que contém métodos de proxy cliente que acessam as operações do serviço Web.</span><span class="sxs-lookup"><span data-stu-id="4df2d-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="4df2d-105">Semelhante à ferramenta [**Metadados de Modelo de Serviço - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para projetos .NET Framework, o **dotnet-svcutil** é uma ferramenta de linha de comando para gerar uma referência de serviço Web compatível com projetos .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4df2d-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="4df2d-106">A ferramenta **dotnet-svcutil** é uma opção alternativa ao provedor de serviços conectados do Visual Studio [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) que foi primeiramente fornecido com o Visual Studio 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="4df2d-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="4df2d-107">A ferramenta **dotnet-svcutil**, como uma ferramenta da CLI do .NET Core, é a multiplataforma disponível no Linux, no macOS e no Windows.</span><span class="sxs-lookup"><span data-stu-id="4df2d-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4df2d-108">Você só deve fazer referência a serviços de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="4df2d-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="4df2d-109">A adição de referências de uma fonte não confiável pode comprometer a segurança.</span><span class="sxs-lookup"><span data-stu-id="4df2d-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4df2d-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4df2d-110">Prerequisites</span></span>

* <span data-ttu-id="4df2d-111">[.NET Core SDK](https://dotnet.microsoft.com/download) v1.0.4 ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="4df2d-111">[.NET Core SDK](https://dotnet.microsoft.com/download) v1.0.4 or later versions</span></span>
* <span data-ttu-id="4df2d-112">Seu editor de código favorito</span><span class="sxs-lookup"><span data-stu-id="4df2d-112">Your favorite code editor</span></span>

## <a name="getting-started"></a><span data-ttu-id="4df2d-113">Introdução</span><span class="sxs-lookup"><span data-stu-id="4df2d-113">Getting started</span></span>

<span data-ttu-id="4df2d-114">O exemplo a seguir orienta você pelas etapas necessárias para adicionar uma referência de serviço Web a um projeto de console .NET Core e chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="4df2d-114">The following example walks you through the steps required to add a web service reference to a .NET Core console project and invoke the service.</span></span> <span data-ttu-id="4df2d-115">Você criará um aplicativo de console .NET Core denominado _HelloSvcutil_ e adicionará uma referência a um serviço Web que implementa o seguinte contrato:</span><span class="sxs-lookup"><span data-stu-id="4df2d-115">You will create a .NET Core console application named _HelloSvcutil_ and will add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="4df2d-116">Neste exemplo, considera-se que o serviço Web será hospedado no seguinte endereço: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="4df2d-116">For this example, the web service will be assumed to be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="4df2d-117">Em uma janela de comandos do Windows, macOS ou Linux, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="4df2d-117">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="4df2d-118">Crie um diretório chamado _HelloSvcutil_ para seu projeto e torne-o seu diretório atual, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4df2d-118">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="4df2d-119">Crie um novo projeto do console C# nesse diretório usando o comando [`dotnet new`](../tools/dotnet-new.md) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4df2d-119">Create a new C# console project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new console
```

3. <span data-ttu-id="4df2d-120">Abra o arquivo de projeto `HelloSvcutil.csproj` em seu editor, edite o elemento `Project` e adicione o pacote [`dotnet-svcutil` do NuGet ](https://nuget.org/packages/dotnet-svcutil) como uma referência à ferramenta da CLI, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="4df2d-120">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

4. <span data-ttu-id="4df2d-121">Restaure o pacote _dotnet-svcutil_ usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4df2d-121">Restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

5. <span data-ttu-id="4df2d-122">Execute _dotnet_ com o comando _svcutil_ para gerar o arquivo de referência de serviço Web da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4df2d-122">Run _dotnet_ with the _svcutil_ command to generate the web service reference file as follows:</span></span>

```console
dotnet svcutil http://contoso.com/SayHello.svc
```
<span data-ttu-id="4df2d-123">O arquivo gerado é salvo como _HelloSvcutil/ServiceReference1/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="4df2d-123">The generated file is saved as _HelloSvcutil/ServiceReference1/Reference.cs_.</span></span> <span data-ttu-id="4df2d-124">A ferramenta _dotnet_svcutil_ também adiciona ao projeto os pacotes WCF apropriados exigidos pelo código proxy como referências de pacotes.</span><span class="sxs-lookup"><span data-stu-id="4df2d-124">The _dotnet_svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

6. <span data-ttu-id="4df2d-125">Restaure os pacotes do WCF usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4df2d-125">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

7. <span data-ttu-id="4df2d-126">Abra o arquivo `Program.cs` em seu editor, edite o método `Main()` e substitua o código gerado automaticamente pelo código a seguir para chamar o serviço Web:</span><span class="sxs-lookup"><span data-stu-id="4df2d-126">Open the `Program.cs` file in your editor, edit the `Main()` method, and replace the auto-generated code with the following code to invoke the web service:</span></span>

```csharp
static void Main(string[] args)
{
    var client = new SayHelloClient();
    Console.WriteLine(client.HelloAsync("dotnet-svcutil").Result);
}
```

8. <span data-ttu-id="4df2d-127">Execute o aplicativo usando o comando [`dotnet run`](../tools/dotnet-run.md) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4df2d-127">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```
<span data-ttu-id="4df2d-128">Você deverá ver a seguinte saída: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="4df2d-128">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="4df2d-129">Para ver uma descrição detalhada dos parâmetros da ferramenta `dotnet-svcutil`, chame a ferramenta passando o parâmetro de ajuda da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="4df2d-129">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>

```console
dotnet svcutil --help
```

## <a name="next-steps"></a><span data-ttu-id="4df2d-130">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4df2d-130">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="4df2d-131">Perguntas e comentários</span><span class="sxs-lookup"><span data-stu-id="4df2d-131">Feedback & questions</span></span>

<span data-ttu-id="4df2d-132">Se tiver perguntas ou comentários, [abra um problema no GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="4df2d-132">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="4df2d-133">Você também pode examinar as perguntas ou os problemas existentes [no repositório do WCF no GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="4df2d-133">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="4df2d-134">Notas de Versão</span><span class="sxs-lookup"><span data-stu-id="4df2d-134">Release notes</span></span>

* <span data-ttu-id="4df2d-135">Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="4df2d-135">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

### <a name="information"></a><span data-ttu-id="4df2d-136">Informações</span><span class="sxs-lookup"><span data-stu-id="4df2d-136">Information</span></span>

* [<span data-ttu-id="4df2d-137">Pacote do NuGet dotnet-svcutil</span><span class="sxs-lookup"><span data-stu-id="4df2d-137">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
