---
title: Microsoft XML Serializer Generator
description: Uma visão geral sobre o Microsoft XML Serializer Generator. Use o XML Serializer Generator para gerar um assembly de serialização XML para os tipos contidos em seu projeto.
author: mlacouture
ms.date: 01/19/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c3f1fcda8a8a6abc58d35bf37e51485bb3590fa3
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794631"
---
# <a name="using-microsoft-xml-serializer-generator-on-net-core"></a><span data-ttu-id="5e3c4-104">Usando o Microsoft XML Serializer Generator no .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e3c4-104">Using Microsoft XML Serializer Generator on .NET Core</span></span>

<span data-ttu-id="5e3c4-105">Este tutorial ensina como usar o Microsoft XML Serializer Generator em um aplicativo do .NET Core em C#.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-105">This tutorial teaches you how to use the Microsoft XML Serializer Generator in a C# .NET Core application.</span></span> <span data-ttu-id="5e3c4-106">Durante este tutorial, você aprenderá:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-106">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5e3c4-107">Como criar um aplicativo do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e3c4-107">How to create a .NET Core app</span></span>
> - <span data-ttu-id="5e3c4-108">Como adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="5e3c4-108">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> - <span data-ttu-id="5e3c4-109">Como editar o MyApp.csproj para adicionar dependências</span><span class="sxs-lookup"><span data-stu-id="5e3c4-109">How to edit your MyApp.csproj to add dependencies</span></span>
> - <span data-ttu-id="5e3c4-110">Como adicionar uma classe e um XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="5e3c4-110">How to add a class and an XmlSerializer</span></span>
> - <span data-ttu-id="5e3c4-111">Como compilar e executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e3c4-111">How to build and run the application</span></span>

<span data-ttu-id="5e3c4-112">Como o [XML Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) para o .NET Framework, o [pacote NuGet Microsoft.XmlSerializer.Generator](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) é o equivalente para projetos do .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-112">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the equivalent for .NET Core and .NET Standard projects.</span></span> <span data-ttu-id="5e3c4-113">Ele cria um assembly de serialização de XML para tipos contidos em um assembly a fim de melhorar o desempenho de inicialização da serialização de XML ao serializar ou desserializar objetos desses tipos usando <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-113">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e3c4-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5e3c4-114">Prerequisites</span></span>

<span data-ttu-id="5e3c4-115">Para concluir este tutorial:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-115">To complete this tutorial:</span></span>

- <span data-ttu-id="5e3c4-116">[SDK do .NET Core 2,1](https://dotnet.microsoft.com/download) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-116">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later.</span></span>
- <span data-ttu-id="5e3c4-117">Seu editor de códigos favorito.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-117">Your favorite code editor.</span></span>

> [!TIP]
> <span data-ttu-id="5e3c4-118">Precisa instalar um editor de código?</span><span class="sxs-lookup"><span data-stu-id="5e3c4-118">Need to install a code editor?</span></span> <span data-ttu-id="5e3c4-119">Experimente o [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span><span class="sxs-lookup"><span data-stu-id="5e3c4-119">Try [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)!</span></span>

## <a name="use-microsoft-xml-serializer-generator-in-a-net-core-console-application"></a><span data-ttu-id="5e3c4-120">Usar o Microsoft XML Serializer Generator em um aplicativo de console do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e3c4-120">Use Microsoft XML Serializer Generator in a .NET Core console application</span></span>

<span data-ttu-id="5e3c4-121">As instruções a seguir mostram como usar o XML Serializer Generator em um aplicativo de console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-121">The following instructions show you how to use XML Serializer Generator in a .NET Core console application.</span></span>

### <a name="create-a-net-core-console-application"></a><span data-ttu-id="5e3c4-122">Criar um aplicativo de console do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e3c4-122">Create a .NET Core console application</span></span>

<span data-ttu-id="5e3c4-123">Abra um prompt de comando e crie uma pasta chamada *MyApp*.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-123">Open a command prompt and create a folder named *MyApp*.</span></span> <span data-ttu-id="5e3c4-124">Navegue até a pasta criada e digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-124">Navigate to the folder you created and type the following command:</span></span>

```dotnetcli
dotnet new console
```

### <a name="add-a-reference-to-the-microsoftxmlserializergenerator-package-in-the-myapp-project"></a><span data-ttu-id="5e3c4-125">Adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator no projeto MyApp</span><span class="sxs-lookup"><span data-stu-id="5e3c4-125">Add a reference to the Microsoft.XmlSerializer.Generator package in the MyApp project</span></span>

<span data-ttu-id="5e3c4-126">Use o [`dotnet add package`](../tools/dotnet-add-package.md) comando para adicionar a referência em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-126">Use the [`dotnet add package`](../tools/dotnet-add-package.md) command to add the reference in your project.</span></span>

<span data-ttu-id="5e3c4-127">Tipo:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-127">Type:</span></span>

```dotnetcli
dotnet add package Microsoft.XmlSerializer.Generator -v 1.0.0
```

### <a name="verify-changes-to-myappcsproj-after-adding-the-package"></a><span data-ttu-id="5e3c4-128">Verificar alterações ao MyApp.csproj depois de adicionar o pacote</span><span class="sxs-lookup"><span data-stu-id="5e3c4-128">Verify changes to MyApp.csproj after adding the package</span></span>

<span data-ttu-id="5e3c4-129">Abra o editor de código e vamos começar!</span><span class="sxs-lookup"><span data-stu-id="5e3c4-129">Open your code editor and let's get started!</span></span> <span data-ttu-id="5e3c4-130">Ainda estamos trabalhando no diretório *MyApp* no qual criamos o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-130">We're still working from the *MyApp* directory we built the app in.</span></span>

<span data-ttu-id="5e3c4-131">Abra o *MyApp.csproj* em seu editor de texto.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-131">Open *MyApp.csproj* in your text editor.</span></span>

<span data-ttu-id="5e3c4-132">Depois de executar [`dotnet add package`](../tools/dotnet-add-package.md) o comando, as seguintes linhas são adicionadas ao seu arquivo de projeto *MyApp. csproj* :</span><span class="sxs-lookup"><span data-stu-id="5e3c4-132">After running the [`dotnet add package`](../tools/dotnet-add-package.md) command, the following lines are added to your *MyApp.csproj* project file:</span></span>

 ```xml
 <ItemGroup>
    <PackageReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-another-itemgroup-section-for-net-core-cli-tool-support"></a><span data-ttu-id="5e3c4-133">Adicionar outra seção ItemGroup para compatibilidade com a ferramenta de CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5e3c4-133">Add another ItemGroup section for .NET Core CLI Tool support</span></span>

<span data-ttu-id="5e3c4-134">Adicione as seguintes linhas depois da seção `ItemGroup` que inspecionamos:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-134">Add the following lines after the `ItemGroup` section that we inspected:</span></span>

 ```xml
 <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.XmlSerializer.Generator" Version="1.0.0" />
 </ItemGroup>
 ```

### <a name="add-a-class-in-the-application"></a><span data-ttu-id="5e3c4-135">Adicionar uma classe no aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e3c4-135">Add a class in the application</span></span>

<span data-ttu-id="5e3c4-136">Abra o *Program.cs* em seu editor de texto.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-136">Open *Program.cs* in your text editor.</span></span> <span data-ttu-id="5e3c4-137">Adicionar a classe denominada *MyClass* no *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-137">Add the class named *MyClass* in *Program.cs*.</span></span>

```csharp
public class MyClass
{
   public int Value;
}
```

### <a name="create-an-xmlserializer-for-myclass"></a><span data-ttu-id="5e3c4-138">Criar um `XmlSerializer` para MyClass</span><span class="sxs-lookup"><span data-stu-id="5e3c4-138">Create an `XmlSerializer` for MyClass</span></span>

<span data-ttu-id="5e3c4-139">Adicione a seguinte linha dentro de *Main* para criar um `XmlSerializer` para MyClass:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-139">Add the following line inside *Main* to create an `XmlSerializer` for MyClass:</span></span>

```csharp
var serializer = new System.Xml.Serialization.XmlSerializer(typeof(MyClass));
```

### <a name="build-and-run-the-application"></a><span data-ttu-id="5e3c4-140">Compile e execute o aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e3c4-140">Build and run the application</span></span>

<span data-ttu-id="5e3c4-141">Ainda dentro da pasta *MyApp*, execute o aplicativo por meio do comando [`dotnet run`](../tools/dotnet-run.md) e ele carregará e usará automaticamente os serializadores pré-gerados em runtime.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-141">Still within the *MyApp* folder, run the application via [`dotnet run`](../tools/dotnet-run.md) and it automatically loads and uses the pre-generated serializers at runtime.</span></span>

<span data-ttu-id="5e3c4-142">Digite o seguinte comando na janela do console:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-142">Type the following command in your console window:</span></span>

```dotnetcli
dotnet run
```

> [!NOTE]
> <span data-ttu-id="5e3c4-143">[`dotnet run`](../tools/dotnet-run.md)chama [`dotnet build`](../tools/dotnet-build.md) para garantir que os destinos de compilação foram criados e, em seguida `dotnet <assembly.dll>` , chama para executar o aplicativo de destino.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-143">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e3c4-144">Os comandos e as etapas mostradas neste tutorial para executar o aplicativo são usadas somente durante o tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-144">The commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="5e3c4-145">Quando estiver pronto para implantar o aplicativo, dê uma olhada nas diferentes [estratégias de implantação](../deploying/index.md) para aplicativos do .NET Core e no comando [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="5e3c4-145">Once you're ready to deploy your app, take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

<span data-ttu-id="5e3c4-146">Se tudo for bem-sucedido, um assembly chamado *MyApp.XmlSerializers.dll* será gerado na pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-146">If everything succeeds, an assembly named *MyApp.XmlSerializers.dll* is generated in the output folder.</span></span>

<span data-ttu-id="5e3c4-147">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="5e3c4-147">Congratulations!</span></span> <span data-ttu-id="5e3c4-148">Você acabou de:</span><span class="sxs-lookup"><span data-stu-id="5e3c4-148">You have just:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5e3c4-149">Criar um aplicativo do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-149">Created a .NET Core app.</span></span>
> - <span data-ttu-id="5e3c4-150">Adicionar uma referência ao pacote Microsoft.XmlSerializer.Generator.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-150">Added a reference to the Microsoft.XmlSerializer.Generator package.</span></span>
> - <span data-ttu-id="5e3c4-151">Editar o MyApp.csproj para adicionar dependências.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-151">Edited your MyApp.csproj to add dependencies.</span></span>
> - <span data-ttu-id="5e3c4-152">Adicionar uma classe e um XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-152">Added a class and an XmlSerializer.</span></span>
> - <span data-ttu-id="5e3c4-153">Compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5e3c4-153">Built and ran the application.</span></span>

## <a name="related-resources"></a><span data-ttu-id="5e3c4-154">Recursos relacionados</span><span class="sxs-lookup"><span data-stu-id="5e3c4-154">Related resources</span></span>

- [<span data-ttu-id="5e3c4-155">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="5e3c4-155">Introducing XML Serialization</span></span>](../../standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="5e3c4-156">Como serializar usando XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="5e3c4-156">How to serialize using XmlSerializer (C#)</span></span>](../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
- [<span data-ttu-id="5e3c4-157">Como serializar usando XmlSerializer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e3c4-157">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)
