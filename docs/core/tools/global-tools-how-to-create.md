---
title: 'Tutorial: Crie uma ferramenta .NET Core'
description: Aprenda a criar uma ferramenta .NET Core. Uma ferramenta é um aplicativo de console que é instalado usando o .NET Core CLI.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156719"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="17d54-104">Tutorial: Crie uma ferramenta .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="17d54-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="17d54-105">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="17d54-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="17d54-106">Este tutorial ensina como criar e empacotar uma ferramenta .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17d54-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="17d54-107">O .NET Core CLI permite que você crie um aplicativo de console como uma ferramenta, que outros podem instalar e executar.</span><span class="sxs-lookup"><span data-stu-id="17d54-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="17d54-108">As ferramentas .NET Core são pacotes NuGet instalados a partir do .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="17d54-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="17d54-109">Para obter mais informações sobre ferramentas, consulte [a visão geral das ferramentas .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="17d54-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="17d54-110">A ferramenta que você criará é um aplicativo de console que leva uma mensagem como entrada e exibe a mensagem junto com linhas de texto que criam a imagem de um robô.</span><span class="sxs-lookup"><span data-stu-id="17d54-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="17d54-111">Este é o primeiro de uma série de três tutoriais.</span><span class="sxs-lookup"><span data-stu-id="17d54-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="17d54-112">Neste tutorial, você cria e empacota uma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="17d54-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="17d54-113">Nos próximos dois tutoriais você [usa a ferramenta como uma ferramenta global](global-tools-how-to-use.md) e usa a ferramenta como uma ferramenta [local.](local-tools-how-to-use.md)</span><span class="sxs-lookup"><span data-stu-id="17d54-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="17d54-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="17d54-114">Prerequisites</span></span>

- <span data-ttu-id="17d54-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="17d54-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="17d54-116">Este tutorial e o tutorial a seguir [para ferramentas globais](global-tools-how-to-use.md) aplicam-se às versões .NET Core SDK 2.1 e posteriores porque as ferramentas globais estão disponíveis a partir dessa versão.</span><span class="sxs-lookup"><span data-stu-id="17d54-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="17d54-117">Mas este tutorial pressupõe que você instalou o 3.1 ou posterior para que você tenha a opção de continuar no [tutorial de ferramentas locais](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="17d54-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="17d54-118">As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="17d54-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="17d54-119">Os procedimentos para criar uma ferramenta são os mesmos, quer você a use como uma ferramenta global ou como uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="17d54-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="17d54-120">Um editor de texto ou editor de código de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="17d54-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="17d54-121">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="17d54-121">Create a project</span></span>

1. <span data-ttu-id="17d54-122">Abra um prompt de comando e crie uma pasta chamada *repositório*.</span><span class="sxs-lookup"><span data-stu-id="17d54-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="17d54-123">Navegue até a pasta do *repositório* e digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="17d54-123">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   <span data-ttu-id="17d54-124">O comando cria uma nova pasta chamada *microsoft.botsay* a pasta *de repositório.*</span><span class="sxs-lookup"><span data-stu-id="17d54-124">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

1. <span data-ttu-id="17d54-125">Navegue até a pasta *microsoft.botsay.*</span><span class="sxs-lookup"><span data-stu-id="17d54-125">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="17d54-126">Adicionar o código</span><span class="sxs-lookup"><span data-stu-id="17d54-126">Add the code</span></span>

1. <span data-ttu-id="17d54-127">Abra `Program.cs` o arquivo com seu editor de código.</span><span class="sxs-lookup"><span data-stu-id="17d54-127">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="17d54-128">Adicione a `using` seguinte diretiva à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="17d54-128">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="17d54-129">Substitua `Main` o método pelo seguinte código para processar os argumentos da linha de comando para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17d54-129">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   <span data-ttu-id="17d54-130">Se nenhum argumento for aprovado, uma mensagem de ajuda curta será exibida.</span><span class="sxs-lookup"><span data-stu-id="17d54-130">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="17d54-131">Caso contrário, todos os argumentos são concatenados em uma `ShowBot` única seqüência e impressos chamando o método que você cria na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="17d54-131">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="17d54-132">Adicione um novo `ShowBot` método chamado que leva um parâmetro de seqüência.</span><span class="sxs-lookup"><span data-stu-id="17d54-132">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="17d54-133">O método imprime a mensagem e uma imagem de um robô usando linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="17d54-133">The method prints out the message and an image of a robot using lines of text.</span></span>

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. <span data-ttu-id="17d54-134">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="17d54-134">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="17d54-135">Testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="17d54-135">Test the application</span></span>

<span data-ttu-id="17d54-136">Execute o projeto e veja a saída.</span><span class="sxs-lookup"><span data-stu-id="17d54-136">Run the project and see the output.</span></span> <span data-ttu-id="17d54-137">Experimente essas variações na linha de comando para ver diferentes resultados:</span><span class="sxs-lookup"><span data-stu-id="17d54-137">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="17d54-138">Todos os argumentos após o delimitador `--` são passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17d54-138">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="17d54-139">Empacote a ferramenta</span><span class="sxs-lookup"><span data-stu-id="17d54-139">Package the tool</span></span>

<span data-ttu-id="17d54-140">Antes de empacotar e distribuir o aplicativo como uma ferramenta, você precisa modificar o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="17d54-140">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="17d54-141">Abra o arquivo *microsoft.botsay.csproj* e adicione três novos nodes XML ao final do `<PropertyGroup>` nó:</span><span class="sxs-lookup"><span data-stu-id="17d54-141">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="17d54-142">`<ToolCommandName>`é um elemento opcional que especifica o comando que invocará a ferramenta depois de instalada.</span><span class="sxs-lookup"><span data-stu-id="17d54-142">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="17d54-143">Se esse elemento não for fornecido, o nome de comando da ferramenta é o nome do arquivo do projeto sem a extensão *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="17d54-143">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="17d54-144">`<PackageOutputPath>`é um elemento opcional que determina onde o pacote NuGet será produzido.</span><span class="sxs-lookup"><span data-stu-id="17d54-144">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="17d54-145">O pacote NuGet é o que o .NET Core CLI usa para instalar sua ferramenta.</span><span class="sxs-lookup"><span data-stu-id="17d54-145">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="17d54-146">O arquivo do projeto agora se parece com o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="17d54-146">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="17d54-147">Crie um pacote NuGet executando o comando [dotnet pack:](dotnet-pack.md)</span><span class="sxs-lookup"><span data-stu-id="17d54-147">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="17d54-148">O arquivo *microsoft.botsay.1.0.0.nupkg* é criado na `<PackageOutputPath>` pasta identificada pelo valor do arquivo *microsoft.botsay.csproj,* que neste exemplo é a pasta *./nupkg.*</span><span class="sxs-lookup"><span data-stu-id="17d54-148">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="17d54-149">Quando você quiser liberar uma ferramenta publicamente, você pode carregá-la para `https://www.nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="17d54-149">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="17d54-150">Uma vez que a ferramenta esteja disponível no NuGet, os desenvolvedores podem instalar a ferramenta usando o comando [dotnet tool install.](dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="17d54-150">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="17d54-151">Para este tutorial você instala o pacote diretamente da pasta *nupkg* local, para que não haja necessidade de carregar o pacote para NuGet.</span><span class="sxs-lookup"><span data-stu-id="17d54-151">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="17d54-152">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="17d54-152">Troubleshoot</span></span>

<span data-ttu-id="17d54-153">Se você receber uma mensagem de erro ao seguir o tutorial, consulte [Problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="17d54-153">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="17d54-154">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="17d54-154">Next steps</span></span>

<span data-ttu-id="17d54-155">Neste tutorial, você criou um aplicativo de console e o embalou como uma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="17d54-155">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="17d54-156">Para aprender como usar a ferramenta como ferramenta global, avance para o próximo tutorial.</span><span class="sxs-lookup"><span data-stu-id="17d54-156">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="17d54-157">Instale e use uma ferramenta global</span><span class="sxs-lookup"><span data-stu-id="17d54-157">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="17d54-158">Se preferir, você pode pular o tutorial de ferramentas globais e ir diretamente para o tutorial de ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="17d54-158">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="17d54-159">Instale e use uma ferramenta local</span><span class="sxs-lookup"><span data-stu-id="17d54-159">Install and use a local tool</span></span>](local-tools-how-to-use.md)
