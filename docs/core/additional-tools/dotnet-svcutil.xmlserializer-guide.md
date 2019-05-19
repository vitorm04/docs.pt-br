---
title: Usar o dotnet-svcutil.xmlserializer no .NET Core
description: Saiba como você pode usar o pacote NuGet `dotnet-svcutil.xmlserializer` para pré-gerar um assembly de serialização para projetos .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 375a5ad5660658431c0d327e55513024823a6eee
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632193"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="620f9-103">Usar o dotnet-svcutil.xmlserializer no .NET Core</span><span class="sxs-lookup"><span data-stu-id="620f9-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="620f9-104">O pacote NuGet `dotnet-svcutil.xmlserializer` pode pré-gerar um assembly de serialização para projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="620f9-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="620f9-105">Ele pré-gera o código de serialização C# para os tipos no aplicativo cliente que são usados pelo Contrato de Serviço do WCF e que podem ser serializados pelo XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="620f9-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="620f9-106">Isso melhora o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos.</span><span class="sxs-lookup"><span data-stu-id="620f9-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="620f9-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="620f9-107">Prerequisites</span></span>

* <span data-ttu-id="620f9-108">[SDK do .NET Core 2.1](https://www.microsoft.com/net/download) ou posterior</span><span class="sxs-lookup"><span data-stu-id="620f9-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="620f9-109">Seu editor de código favorito</span><span class="sxs-lookup"><span data-stu-id="620f9-109">Your favorite code editor</span></span>

<span data-ttu-id="620f9-110">Você pode usar o comando `dotnet --info` para verificar quais versões do SDK do .NET Core e do tempo de execução estão instaladas.</span><span class="sxs-lookup"><span data-stu-id="620f9-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="620f9-111">Introdução</span><span class="sxs-lookup"><span data-stu-id="620f9-111">Getting started</span></span>

<span data-ttu-id="620f9-112">Para usar `dotnet-svcutil.xmlserializer` em um aplicativo de console do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="620f9-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="620f9-113">Crie um serviço do WCF chamado “MeuServiçoWCF” usando o modelo padrão “Aplicativo de serviço WCF” no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="620f9-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="620f9-114">Adicione o atributo `[XmlSerializerFormat]` ao método de serviço desta forma:</span><span class="sxs-lookup"><span data-stu-id="620f9-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="620f9-115">Crie um aplicativo de console do .NET Core como um aplicativo cliente do WCF direcionado ao .NET Core 2.1 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="620f9-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="620f9-116">Por exemplo, crie um aplicativo chamado 'MyWCFClient' com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="620f9-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```console
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="620f9-117">Para garantir que o projeto seja direcionado ao .NET Core 2.1 ou posterior, inspecione o elemento XML `TargetFramework` no arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="620f9-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="620f9-118">Adicione uma referência de pacote a `System.ServiceModel.Http` executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="620f9-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="620f9-119">Adicione o código de cliente do WCF:</span><span class="sxs-lookup"><span data-stu-id="620f9-119">Add the WCF Client code:</span></span>

    ```csharp
    using System.ServiceModel;

        class Program
        {
            static void Main(string[] args)
            {
                var myBinding = new BasicHttpBinding();
                var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
                var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
                IService1 client = myChannelFactory.CreateChannel();
                string s = client.GetData(1);
                ((ICommunicationObject)client).Close();
            }
        }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

5. <span data-ttu-id="620f9-120">Adicione uma referência ao pacote `dotnet-svcutil.xmlserializer` executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="620f9-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="620f9-121">A execução do comando deverá adicionar uma entrada ao arquivo de projeto semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="620f9-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="620f9-122">Compile o aplicativo executando `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="620f9-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="620f9-123">Se tudo for bem-sucedido, um assembly chamado *MyWCFClient.XmlSerializers.dll* será gerado na pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="620f9-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="620f9-124">Se a ferramenta não puder gerar o assembly, você verá avisos na saída do build.</span><span class="sxs-lookup"><span data-stu-id="620f9-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="620f9-125">Inicie o serviço WCF, por exemplo, executando `http://localhost:2561/Service1.svc` no navegador.</span><span class="sxs-lookup"><span data-stu-id="620f9-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="620f9-126">Depois, inicie o aplicativo cliente, e ele será carregado automaticamente e usará os serializadores pré-gerados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="620f9-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
