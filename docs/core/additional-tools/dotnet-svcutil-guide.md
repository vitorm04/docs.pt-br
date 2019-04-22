---
title: Visão geral da ferramenta svcutil do WCF
description: Uma visão geral da ferramenta Microsoft WCF dotnet-svcutil que adiciona funcionalidade a projetos do .NET Core e ASP.NET Core, semelhante à ferramenta WCF svcutil para projetos do .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: b5dfb84f19c3748daa303c828cbe881f1582eb76
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612805"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="0327d-103">Ferramenta dotnet-svcutil do WCF para .NET Core</span><span class="sxs-lookup"><span data-stu-id="0327d-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="0327d-104">A ferramenta **dotnet-svcutil** do Windows Communication Foundation (WCF) é uma ferramenta da CLI do .NET Core que recupera metadados de um serviço Web em um local de rede ou de um arquivo WSDL e gera uma classe do WCF que contém métodos de proxy cliente que acessam as operações do serviço Web.</span><span class="sxs-lookup"><span data-stu-id="0327d-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="0327d-105">Semelhante à ferramenta [**Metadados de Modelo de Serviço - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para projetos .NET Framework, o **dotnet-svcutil** é uma ferramenta de linha de comando para gerar uma referência de serviço Web compatível com projetos .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0327d-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="0327d-106">A ferramenta **dotnet-svcutil** é uma opção alternativa ao provedor de serviços conectados do Visual Studio [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) que foi primeiramente fornecido com o Visual Studio 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="0327d-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="0327d-107">A ferramenta **dotnet-svcutil**, como uma ferramenta da CLI do .NET Core, é a multiplataforma disponível no Linux, no macOS e no Windows.</span><span class="sxs-lookup"><span data-stu-id="0327d-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0327d-108">Você só deve fazer referência a serviços de uma fonte confiável.</span><span class="sxs-lookup"><span data-stu-id="0327d-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="0327d-109">A adição de referências de uma fonte não confiável pode comprometer a segurança.</span><span class="sxs-lookup"><span data-stu-id="0327d-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0327d-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0327d-110">Prerequisites</span></span>

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="0327d-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="0327d-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)
* <span data-ttu-id="0327d-112">[SDK do .NET Core 2.1](https://dotnet.microsoft.com/download) ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="0327d-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="0327d-113">Seu editor de código favorito</span><span class="sxs-lookup"><span data-stu-id="0327d-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="0327d-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="0327d-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
* <span data-ttu-id="0327d-115">[SDK do .NET Core 1.0.4](https://dotnet.microsoft.com/download) ou versões posteriores</span><span class="sxs-lookup"><span data-stu-id="0327d-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="0327d-116">Seu editor de código favorito</span><span class="sxs-lookup"><span data-stu-id="0327d-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="0327d-117">Introdução</span><span class="sxs-lookup"><span data-stu-id="0327d-117">Getting started</span></span>

<span data-ttu-id="0327d-118">O exemplo a seguir orienta você pelas etapas necessárias para adicionar uma referência de serviço Web a um projeto Web do .NET Core e chamar o serviço.</span><span class="sxs-lookup"><span data-stu-id="0327d-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="0327d-119">Você criará um aplicativo Web do .NET Core denominado _HelloSvcutil_ e adicionará uma referência a um serviço Web que implementa o seguinte contrato:</span><span class="sxs-lookup"><span data-stu-id="0327d-119">You'll create a .NET Core web application named _HelloSvcutil_ and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="0327d-120">Neste exemplo, vamos assumir que o serviço Web será hospedado no seguinte endereço: `http://contoso.com/SayHello.svc`</span><span class="sxs-lookup"><span data-stu-id="0327d-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="0327d-121">Em uma janela de comandos do Windows, macOS ou Linux, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="0327d-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="0327d-122">Crie um diretório chamado _HelloSvcutil_ para seu projeto e torne-o seu diretório atual, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0327d-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

```console
mkdir HelloSvcutil
cd HelloSvcutil
```

2. <span data-ttu-id="0327d-123">Crie um novo projeto Web em C# nesse diretório usando o comando [`dotnet new`](../tools/dotnet-new.md) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0327d-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

```console
dotnet new web
```

3. <span data-ttu-id="0327d-124">Instale o [pacote do NuGet `dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) como uma ferramenta de CLI:</span><span class="sxs-lookup"><span data-stu-id="0327d-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="0327d-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="0327d-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet tool install --global dotnet-svcutil
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="0327d-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="0327d-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
<span data-ttu-id="0327d-127">Abra o arquivo de projeto `HelloSvcutil.csproj` em seu editor, edite o elemento `Project` e adicione o pacote [`dotnet-svcutil` do NuGet ](https://nuget.org/packages/dotnet-svcutil) como uma referência à ferramenta da CLI, usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="0327d-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

```xml
<ItemGroup>
  <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
</ItemGroup>
```

<span data-ttu-id="0327d-128">Depois, restaure o pacote _dotnet-svcutil_ usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0327d-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

---

4. <span data-ttu-id="0327d-129">Execute o comando _dotnet-svcutil_ para gerar o arquivo de referência do serviço Web da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0327d-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="0327d-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="0327d-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil http://contoso.com/SayHello.svc
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="0327d-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="0327d-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil http://contoso.com/SayHello.svc
```

---

<span data-ttu-id="0327d-132">O arquivo gerado é salvo como _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="0327d-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="0327d-133">A ferramenta _dotnet-svcutil_ também adiciona ao projeto os pacotes WCF apropriados exigidos pelo código proxy como referências de pacote.</span><span class="sxs-lookup"><span data-stu-id="0327d-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="0327d-134">Usar a referência de serviço</span><span class="sxs-lookup"><span data-stu-id="0327d-134">Using the Service Reference</span></span>

1. <span data-ttu-id="0327d-135">Restaure os pacotes do WCF usando o comando [`dotnet restore`](../tools/dotnet-restore.md) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0327d-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

```console
dotnet restore
```

2. <span data-ttu-id="0327d-136">Localize o nome da classe do cliente e a operação que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="0327d-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="0327d-137">`Reference.cs` conterá uma classe que herda de `System.ServiceModel.ClientBase`, com métodos que podem ser usados para chamar operações no serviço.</span><span class="sxs-lookup"><span data-stu-id="0327d-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="0327d-138">Neste exemplo, você deseja chamar a operação _Hello_ do serviço _SayHello_.</span><span class="sxs-lookup"><span data-stu-id="0327d-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="0327d-139">`ServiceReference.SayHelloClient` é o nome da classe do cliente e tem um método chamado `HelloAsync` que pode ser usado para chamar a operação.</span><span class="sxs-lookup"><span data-stu-id="0327d-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="0327d-140">Abra o arquivo `Startup.cs` em seu editor e adicione uma instrução using para o namespace de referência de serviço na parte superior:</span><span class="sxs-lookup"><span data-stu-id="0327d-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

```csharp
using ServiceReference;
```

 4. <span data-ttu-id="0327d-141">Edite o método `Configure` para invocar o serviço Web.</span><span class="sxs-lookup"><span data-stu-id="0327d-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="0327d-142">Faça isso criando uma instância da classe que herda de `ClientBase` e chamando o método no objeto de cliente:</span><span class="sxs-lookup"><span data-stu-id="0327d-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="0327d-143">Execute o aplicativo usando o comando [`dotnet run`](../tools/dotnet-run.md) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0327d-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

```console
dotnet run
```

6. <span data-ttu-id="0327d-144">Navegue até a URL listada no console (por exemplo, `http://localhost:5000`) em seu navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="0327d-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="0327d-145">Você deverá ver a seguinte saída: "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="0327d-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="0327d-146">Para ver uma descrição detalhada dos parâmetros da ferramenta `dotnet-svcutil`, chame a ferramenta passando o parâmetro de ajuda da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="0327d-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="0327d-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="0327d-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="0327d-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="0327d-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="0327d-149">Perguntas e comentários</span><span class="sxs-lookup"><span data-stu-id="0327d-149">Feedback & questions</span></span>

<span data-ttu-id="0327d-150">Se tiver perguntas ou comentários, [abra um problema no GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="0327d-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="0327d-151">Você também pode examinar as perguntas ou os problemas existentes [no repositório do WCF no GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="0327d-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="0327d-152">Notas de Versão</span><span class="sxs-lookup"><span data-stu-id="0327d-152">Release notes</span></span>

* <span data-ttu-id="0327d-153">Consulte as [Notas de versão](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) para obter informações de versão atualizadas, incluindo problemas conhecidos.</span><span class="sxs-lookup"><span data-stu-id="0327d-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="0327d-154">Informações</span><span class="sxs-lookup"><span data-stu-id="0327d-154">Information</span></span>

* [<span data-ttu-id="0327d-155">Pacote do NuGet dotnet-svcutil</span><span class="sxs-lookup"><span data-stu-id="0327d-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
