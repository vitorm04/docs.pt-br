---
title: Usando o Microsoft XML Serializer Generator no .NET Core
description: "Uma visão geral sobre o Microsoft XML Serializer Generator."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2017
ms.topic: tutorial
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: 4b838cafe1f4835c1c5aa6086c0997a4a9e39a9e
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2018
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="f1cd5-103">Usando o Microsoft XML Serializer Generator no .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1cd5-103">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="f1cd5-104">Este tutorial ensina como usar o Microsoft XML Serializer Generator em um aplicativo do .NET Core em C#.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-104">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="f1cd5-105">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="f1cd5-106">Como criar um aplicativo do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1cd5-106">How to create a .NET Core app</span></span>
> * <span data-ttu-id="f1cd5-107">Como adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="f1cd5-107">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="f1cd5-108">Como editar o MyApp.csproj para adicionar dependências</span><span class="sxs-lookup"><span data-stu-id="f1cd5-108">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="f1cd5-109">Como adicionar uma classe e um XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="f1cd5-109">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="f1cd5-110">Como compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1cd5-110">How to build and run the application</span></span> 

<span data-ttu-id="f1cd5-111">Como o [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) para o .NET Framework, o [pacote NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) é o equivalente para projetos do .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-111">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="f1cd5-112">Ele cria um assembly de serialização de XML para tipos contidos em um assembly a fim de melhorar o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos usando <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-112">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1cd5-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="f1cd5-113">Prerequisites</span></span>

<span data-ttu-id="f1cd5-114">Para concluir este tutorial:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-114">To complete this tutorial:</span></span>

* <span data-ttu-id="f1cd5-115">Instale o [SDK do .NET Core 2.1.3 ou posterior](https://www.microsoft.com/net/download)</span><span class="sxs-lookup"><span data-stu-id="f1cd5-115">Install [.NET Core SDK 2.1.3 or later](https://www.microsoft.com/net/download)</span></span>
* <span data-ttu-id="f1cd5-116">Instale seu editor de código favorito, caso ainda não tenha um.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-116">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="f1cd5-117">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="f1cd5-117">Need to install a code editor?</span></span> <span data-ttu-id="f1cd5-118">Experimente o [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="f1cd5-118">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>
  
## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="f1cd5-119">Usar o Microsoft XML Serializer Generator em um aplicativo de console do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1cd5-119">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span> 

<span data-ttu-id="f1cd5-120">As instruções a seguir mostram como usar o XML Serializer Generator em um aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-120">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="f1cd5-121">Criar um aplicativo de console do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1cd5-121">Create a .NET Core console application</span></span>

<span data-ttu-id="f1cd5-122">Abra um prompt de comando e crie uma pasta chamada *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-122">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="f1cd5-123">Navegue até a pasta criada e digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-123">Navigate to the folder you created and type the following command:</span></span>

```console
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="f1cd5-124">Adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator no projeto MyApp</span><span class="sxs-lookup"><span data-stu-id="f1cd5-124">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="f1cd5-125">Use o comando [`dotnet add package`](../tools//dotnet-add-package.md) para adicionar a referência em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-125">Use the [`dotnet add package`](../tools//dotnet-add-package.md) command to add the reference in your project.</span></span> 

<span data-ttu-id="f1cd5-126">Tipo:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-126">Type:</span></span>
 
 ```console
 dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
 ```
 
### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="f1cd5-127">Verificar alterações ao MyApp.csproj depois de adicionar o pacote</span><span class="sxs-lookup"><span data-stu-id="f1cd5-127">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="f1cd5-128">Abra o editor de código e vamos começar!</span><span class="sxs-lookup"><span data-stu-id="f1cd5-128">Open your code editor and let's get started!</span></span> <span data-ttu-id="f1cd5-129">Ainda estamos trabalhando no diretório *MyApp* no qual criamos o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-129">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="f1cd5-130">Abra o *MyApp.csproj* em seu editor de texto.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-130">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="f1cd5-131">Depois de executar o comando [`dotnet add package`](../tools//dotnet-add-package.md), as seguintes linhas são adicionadas ao seu arquivo de projeto *MyApp.csproj*:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-131">After running the [`dotnet add package`](../tools//dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="f1cd5-132">Adicionar outra seção ItemGroup para compatibilidade com a ferramenta de CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1cd5-132">Add another ItemGroup section for .NET Core CLI Tool support</span></span>
 
 <span data-ttu-id="f1cd5-133">Adicione as seguintes linhas depois da seção `ItemGroup` que inspecionamos:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-133">Add the following lines after the `ItemGroup` section that we inspected:</span></span>
 
 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```
 
### <a name="add-a-class-in-the-application"></a><span data-ttu-id="f1cd5-134">Adicionar uma classe no aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1cd5-134">Add a class in the application</span></span>

<span data-ttu-id="f1cd5-135">Abra o *Program.cs* em seu editor de texto.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-135">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="f1cd5-136">Adicionar a classe denominada *MyClass* no *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-136">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="f1cd5-137">Criar um `XmlSerializer` para MyClass</span><span class="sxs-lookup"><span data-stu-id="f1cd5-137">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="f1cd5-138">Adicione a seguinte linha dentro de *Main* para criar um `XmlSerializer` para MyClass:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-138">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="f1cd5-139">Compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="f1cd5-139">Build and run the application</span></span>

<span data-ttu-id="f1cd5-140">Ainda dentro da pasta *MyApp*, execute o aplicativo por meio do comando [`dotnet run`](../tools/dotnet-run.md) e ele carregará e usará automaticamente os serializadores pré-gerados em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-140">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="f1cd5-141">Digite o seguinte comando na janela do console:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-141">Type the following command in your console window:</span></span>

 ```console
 $ dotnet run
 ```
> [!NOTE]
> <span data-ttu-id="f1cd5-142">[`dotnet run`](../tools/dotnet-run.md) chama [`dotnet build`](../tools/dotnet-build.md) para garantir que os destinos de build foram criados e então chama `dotnet <assembly.dll>` para executar o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-142">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1cd5-143">Os comandos e as etapas mostradas neste tutorial para executar o aplicativo são usadas somente durante o tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-143">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="f1cd5-144">Quando estiver pronto para implantar o aplicativo, dê uma olhada nas diferentes [estratégias de implantação](../deploying/index.md) para aplicativos do .NET Core e no comando [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="f1cd5-144">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="f1cd5-145">Se tudo for bem-sucedido, um assembly chamado *MyApp.XmlSerializers.dll* será gerado na pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-145">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span> 



<span data-ttu-id="f1cd5-146">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="f1cd5-146">Congratulations!</span></span> <span data-ttu-id="f1cd5-147">Você acabou de:</span><span class="sxs-lookup"><span data-stu-id="f1cd5-147">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f1cd5-148">Criar um aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-148">Created a .NET Core app.</span></span>
> * <span data-ttu-id="f1cd5-149">Adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-149">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> * <span data-ttu-id="f1cd5-150">Editar o MyApp.csproj para adicionar dependências.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-150">Edited your MyApp.csproj to add dependencies.</span></span>
> * <span data-ttu-id="f1cd5-151">Adicionar uma classe e um XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-151">Added a class and an XmlSerializer.</span></span>
> * <span data-ttu-id="f1cd5-152">Compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f1cd5-152">Built and ran the application.</span></span> 

## <a name="related-resources"></a><span data-ttu-id="f1cd5-153">Recursos relacionados</span><span class="sxs-lookup"><span data-stu-id="f1cd5-153">Related Resources</span></span>

* [<span data-ttu-id="f1cd5-154">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="f1cd5-154">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
* [<span data-ttu-id="f1cd5-155">Como serializar usando XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="f1cd5-155">How to: Serialize Using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)
* [<span data-ttu-id="f1cd5-156">Como serializar usando XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1cd5-156">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer)