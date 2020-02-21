---
title: 'Tutorial: criar uma ferramenta do .NET Core'
description: Saiba como criar uma ferramenta do .NET Core. Uma ferramenta é um aplicativo de console que é instalado usando o CLI do .NET Core.
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543398"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="9e824-104">Tutorial: criar uma ferramenta do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="9e824-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="9e824-105">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="9e824-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="9e824-106">Este tutorial ensina como criar e empacotar uma ferramenta do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e824-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="9e824-107">O CLI do .NET Core permite criar um aplicativo de console como uma ferramenta, que outras pessoas podem instalar e executar.</span><span class="sxs-lookup"><span data-stu-id="9e824-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="9e824-108">As ferramentas do .NET Core são pacotes NuGet instalados a partir do CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e824-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="9e824-109">Para obter mais informações sobre ferramentas, consulte [visão geral das ferramentas do .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="9e824-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="9e824-110">A ferramenta que você criará é um aplicativo de console que recebe uma mensagem como entrada e exibe a mensagem junto com linhas de texto que criam a imagem de um robô.</span><span class="sxs-lookup"><span data-stu-id="9e824-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="9e824-111">Este é o primeiro de uma série de três tutoriais.</span><span class="sxs-lookup"><span data-stu-id="9e824-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="9e824-112">Neste tutorial, você criará e empacotará uma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="9e824-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="9e824-113">Nos próximos dois tutoriais, você [usará a ferramenta como uma ferramenta global](global-tools-how-to-use.md) e [usará a ferramenta como uma ferramenta local](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="9e824-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e824-114">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="9e824-114">Prerequisites</span></span>

- <span data-ttu-id="9e824-115">[SDK do .NET Core 3,1](https://dotnet.microsoft.com/download) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="9e824-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="9e824-116">Este tutorial e o tutorial a seguir [para ferramentas globais](global-tools-how-to-use.md) se aplicam ao SDK do .NET Core 2,1 e versões posteriores porque as ferramentas globais estão disponíveis a partir dessa versão.</span><span class="sxs-lookup"><span data-stu-id="9e824-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="9e824-117">Mas este tutorial pressupõe que você tenha instalado o 3,1 ou posterior para que você tenha a opção de continuar no [tutorial de ferramentas locais](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="9e824-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="9e824-118">As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="9e824-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="9e824-119">Os procedimentos para criar uma ferramenta são os mesmos se você usá-la como uma ferramenta global ou como uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="9e824-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="9e824-120">Um editor de texto ou editor de código de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="9e824-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="9e824-121">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="9e824-121">Create a project</span></span>

1. <span data-ttu-id="9e824-122">Abra um prompt de comando e crie uma pasta chamada *Repository*.</span><span class="sxs-lookup"><span data-stu-id="9e824-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="9e824-123">Navegue até a pasta *repositório* e insira o comando a seguir, substituindo `<name>` por um valor exclusivo para tornar o nome do projeto exclusivo.</span><span class="sxs-lookup"><span data-stu-id="9e824-123">Navigate to the *repository* folder and enter the following command, replacing `<name>` with a unique value to make the project name unique.</span></span> 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   <span data-ttu-id="9e824-124">Por exemplo, você pode executar o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="9e824-124">For example, you could run the following command:</span></span>

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   <span data-ttu-id="9e824-125">O comando cria uma nova pasta chamada *botsay\<-name >* na pasta *Repository* .</span><span class="sxs-lookup"><span data-stu-id="9e824-125">The command creates a new folder named *botsay-\<name>* under the *repository* folder.</span></span>

1. <span data-ttu-id="9e824-126">Navegue até o *nome do botsay-\<>* pasta.</span><span class="sxs-lookup"><span data-stu-id="9e824-126">Navigate to the *botsay-\<name>* folder.</span></span>

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a><span data-ttu-id="9e824-127">Adicionar o código</span><span class="sxs-lookup"><span data-stu-id="9e824-127">Add the code</span></span>

1. <span data-ttu-id="9e824-128">Abra o arquivo `Program.cs` com seu editor de código.</span><span class="sxs-lookup"><span data-stu-id="9e824-128">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="9e824-129">Adicione a seguinte diretiva `using` à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="9e824-129">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="9e824-130">Substitua o método `Main` pelo código a seguir para processar os argumentos de linha de comando para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e824-130">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

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

   <span data-ttu-id="9e824-131">Se nenhum argumento for passado, será exibida uma mensagem de ajuda curta.</span><span class="sxs-lookup"><span data-stu-id="9e824-131">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="9e824-132">Caso contrário, todos os argumentos são concatenados em uma única cadeia de caracteres e impressos chamando o método de `ShowBot` que você cria na próxima etapa.</span><span class="sxs-lookup"><span data-stu-id="9e824-132">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="9e824-133">Adicione um novo método chamado `ShowBot` que usa um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="9e824-133">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="9e824-134">O método imprime a mensagem e uma imagem de um robô usando linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="9e824-134">The method prints out the message and an image of a robot using lines of text.</span></span>

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

1. <span data-ttu-id="9e824-135">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="9e824-135">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="9e824-136">Testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="9e824-136">Test the application</span></span>

<span data-ttu-id="9e824-137">Execute o projeto e veja a saída.</span><span class="sxs-lookup"><span data-stu-id="9e824-137">Run the project and see the output.</span></span> <span data-ttu-id="9e824-138">Experimente essas variações na linha de comando para ver os resultados diferentes:</span><span class="sxs-lookup"><span data-stu-id="9e824-138">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="9e824-139">Todos os argumentos após o delimitador `--` são passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e824-139">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="9e824-140">Empacotar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="9e824-140">Package the tool</span></span>

<span data-ttu-id="9e824-141">Antes de poder empacotar e distribuir o aplicativo como uma ferramenta, você precisa modificar o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="9e824-141">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span> 

1. <span data-ttu-id="9e824-142">Abra o *botsay-\<nome > arquivo. csproj* e adicione três novos nós XML ao final do nó de `<PropertyGroup>`:</span><span class="sxs-lookup"><span data-stu-id="9e824-142">Open the *botsay-\<name>.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="9e824-143">`<ToolCommandName>` é um elemento opcional que especifica o comando que invocará a ferramenta após sua instalação.</span><span class="sxs-lookup"><span data-stu-id="9e824-143">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="9e824-144">Se esse elemento não for fornecido, o nome do comando para a ferramenta será o nome do arquivo de projeto sem a extensão *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="9e824-144">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="9e824-145">`<PackageOutputPath>` é um elemento opcional que determina onde o pacote NuGet será produzido.</span><span class="sxs-lookup"><span data-stu-id="9e824-145">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="9e824-146">O pacote NuGet é o que o CLI do .NET Core usa para instalar sua ferramenta.</span><span class="sxs-lookup"><span data-stu-id="9e824-146">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="9e824-147">O arquivo de projeto agora é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9e824-147">The project file now looks like the following example:</span></span>

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

1. <span data-ttu-id="9e824-148">Crie um pacote NuGet executando o comando [dotnet Pack](dotnet-pack.md) :</span><span class="sxs-lookup"><span data-stu-id="9e824-148">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="9e824-149">O *nome botsay-\<> arquivo. 1.0.0. nupkg* é criado na pasta identificada pelo valor `<PackageOutputPath>` do arquivo *botsay-\<nome >. csproj* , que neste exemplo é a pasta *./nupkg* .</span><span class="sxs-lookup"><span data-stu-id="9e824-149">The *botsay-\<name>.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *botsay-\<name>.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="9e824-150">Quando você quiser liberar uma ferramenta publicamente, poderá carregá-la no `https://www.nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="9e824-150">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="9e824-151">Depois que a ferramenta estiver disponível no NuGet, os desenvolvedores poderão instalar a ferramenta usando o comando [dotnet ferramenta de instalação](dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="9e824-151">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="9e824-152">Para este tutorial, você instala o pacote diretamente da pasta *nupkg* local, portanto, não é necessário carregar o pacote no NuGet.</span><span class="sxs-lookup"><span data-stu-id="9e824-152">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="9e824-153">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="9e824-153">Troubleshoot</span></span>

<span data-ttu-id="9e824-154">Se você receber uma mensagem de erro ao seguir o tutorial, consulte [solucionar problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="9e824-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e824-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="9e824-155">Next steps</span></span>

<span data-ttu-id="9e824-156">Neste tutorial, você criou um aplicativo de console e o empacotava como uma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="9e824-156">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="9e824-157">Para saber como usar a ferramenta como uma ferramenta global, avance para o próximo tutorial.</span><span class="sxs-lookup"><span data-stu-id="9e824-157">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e824-158">Instalar e usar uma ferramenta global</span><span class="sxs-lookup"><span data-stu-id="9e824-158">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="9e824-159">Se preferir, você pode ignorar o tutorial de ferramentas globais e ir diretamente para o tutorial de ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="9e824-159">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e824-160">Instalar e usar uma ferramenta local</span><span class="sxs-lookup"><span data-stu-id="9e824-160">Install and use a local tool</span></span>](local-tools-how-to-use.md)
