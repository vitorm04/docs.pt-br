---
title: Como criar uma Ferramenta Global do .NET Core
description: Descreve como criar uma Ferramenta Global. A Ferramenta Global é um aplicativo de console instalado por meio da CLI do .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 045b8f7707b8ee36ea9674bba3974197a57c482d
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826415"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="17f27-104">Criar uma Ferramenta Global do .NET Core usando a CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="17f27-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="17f27-105">Este artigo ensina a criar e empacotar uma ferramenta Global do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17f27-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="17f27-106">A CLI do .NET Core permite que você crie um aplicativo de console como uma Ferramenta Global, o que outras pessoas podem instalar e executar facilmente.</span><span class="sxs-lookup"><span data-stu-id="17f27-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="17f27-107">Ferramentas Globais do .NET Core são pacotes NuGet que são instalados por meio da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17f27-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="17f27-108">Para obter mais informações sobre as Ferramentas Globais, confira [Visão geral das Ferramentas Globais do .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="17f27-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="17f27-109">Criar um projeto</span><span class="sxs-lookup"><span data-stu-id="17f27-109">Create a project</span></span>

<span data-ttu-id="17f27-110">Este artigo usa a CLI do .NET Core para criar e gerenciar um projeto.</span><span class="sxs-lookup"><span data-stu-id="17f27-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="17f27-111">Nossa ferramenta de exemplo será um aplicativo de console que gera um bot ASCII e imprime uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="17f27-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="17f27-112">Primeiro, crie um novo Aplicativo de Console do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="17f27-112">First, create a new .NET Core Console Application.</span></span>

```console
dotnet new console -o botsay
```

<span data-ttu-id="17f27-113">Navegue até o diretório `botsay` criado pelo comando anterior.</span><span class="sxs-lookup"><span data-stu-id="17f27-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="17f27-114">Adicionar o código</span><span class="sxs-lookup"><span data-stu-id="17f27-114">Add the code</span></span>

<span data-ttu-id="17f27-115">Abra o arquivo `Program.cs` com o seu editor de texto favorito, como o `vim` ou o [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="17f27-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="17f27-116">Adicione a diretiva `using` a seguir na parte superior do arquivo, isso ajuda a reduzir o código para exibir as informações de versão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17f27-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="17f27-117">Em seguida, mova para baixo até o método `Main`.</span><span class="sxs-lookup"><span data-stu-id="17f27-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="17f27-118">Substitua o método com o código a seguir para processar os argumentos de linha de comando para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17f27-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="17f27-119">Se nenhum argumento foi passado, uma breve mensagem de ajuda é exibida.</span><span class="sxs-lookup"><span data-stu-id="17f27-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="17f27-120">Caso contrário, todos os argumentos são transformados em uma cadeia de caracteres e impressos com o bot.</span><span class="sxs-lookup"><span data-stu-id="17f27-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

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

### <a name="create-the-bot"></a><span data-ttu-id="17f27-121">Criar o bot</span><span class="sxs-lookup"><span data-stu-id="17f27-121">Create the bot</span></span>

<span data-ttu-id="17f27-122">Em seguida, adicione um novo método chamado `ShowBot` que usa um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="17f27-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="17f27-123">Esse método imprime a mensagem e o bot de ASCII.</span><span class="sxs-lookup"><span data-stu-id="17f27-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="17f27-124">O código de bot ASCII foi obtido do exemplo [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs).</span><span class="sxs-lookup"><span data-stu-id="17f27-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

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

### <a name="test-the-tool"></a><span data-ttu-id="17f27-125">Testar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="17f27-125">Test the tool</span></span>

<span data-ttu-id="17f27-126">Execute o projeto e veja a saída.</span><span class="sxs-lookup"><span data-stu-id="17f27-126">Run the project and see the output.</span></span> <span data-ttu-id="17f27-127">Experimente estas variações de linha de comando para ver resultados diferentes:</span><span class="sxs-lookup"><span data-stu-id="17f27-127">Try these variations of the command-line to see different results:</span></span>

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="17f27-128">Todos os argumentos após o delimitador `--` são passados para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17f27-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="setup-the-global-tool"></a><span data-ttu-id="17f27-129">Configurar a ferramenta global</span><span class="sxs-lookup"><span data-stu-id="17f27-129">Setup the global tool</span></span>

<span data-ttu-id="17f27-130">Antes de poder empacotar e distribuir o aplicativo como uma Ferramenta Global, você precisa modificar o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="17f27-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="17f27-131">Abra o arquivo `botsay.csproj` e adicione três novos nós XML ao nó `<Project><PropertyGroup>`:</span><span class="sxs-lookup"><span data-stu-id="17f27-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`  
<span data-ttu-id="17f27-132">[OBRIGATÓRIO] Indica que o aplicativo será empacotado para instalação como uma Ferramenta Global.</span><span class="sxs-lookup"><span data-stu-id="17f27-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`  
<span data-ttu-id="17f27-133">[OPCIONAL] Um nome alternativo para a ferramenta, caso contrário, o nome do comando para a ferramenta será nomeado após o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="17f27-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="17f27-134">Você pode ter várias ferramentas em um pacote, sendo que escolher um nome amigável e exclusivo ajuda a diferenciar de outras ferramentas no mesmo pacote.</span><span class="sxs-lookup"><span data-stu-id="17f27-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`  
<span data-ttu-id="17f27-135">[OPCIONAL] O local em que o pacote NuGet será produzido.</span><span class="sxs-lookup"><span data-stu-id="17f27-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="17f27-136">O pacote NuGet é o que as Ferramentas Globais da CLI do .NET Core usam para instalar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="17f27-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

<span data-ttu-id="17f27-137">Embora `<PackageOutputPath>` seja opcional, use-o neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="17f27-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="17f27-138">Verifique se você o definiu: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span><span class="sxs-lookup"><span data-stu-id="17f27-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="17f27-139">Em seguida, crie um pacote NuGet para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17f27-139">Next, create a NuGet package for your application.</span></span>

```console
dotnet pack
```

<span data-ttu-id="17f27-140">O arquivo `botsay.1.0.0.nupkg` é criado na pasta identificada pelo valor XML `<PackageOutputPath>` do arquivo `botsay.csproj`, que neste exemplo é a pasta `./nupkg`.</span><span class="sxs-lookup"><span data-stu-id="17f27-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="17f27-141">Isso torna mais fácil instalar e testar.</span><span class="sxs-lookup"><span data-stu-id="17f27-141">This makes it easy to install and test.</span></span> <span data-ttu-id="17f27-142">Quando você desejar liberar uma ferramenta para o público, carregue-a para [https://www.nuget.org](https://www.nuget.org). Quando a ferramenta estiver disponível no NuGet, os desenvolvedores podem executar uma instalação da ferramenta em todo o usuário usando a opção `--global` do comando [dotnet tool install](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="17f27-142">When you want to release a tool publicly, upload it to [https://www.nuget.org](https://www.nuget.org). Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="17f27-143">Agora que você tem um pacote, instale a ferramenta desse pacote:</span><span class="sxs-lookup"><span data-stu-id="17f27-143">Now that you have a package, install the tool from that package:</span></span> 

```console
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="17f27-144">O parâmetro `--add-source` instrui a CLI do .NET Core a usar temporariamente a pasta `./nupkg` (nossa pasta `<PackageOutputPath>`) como uma fonte adicional de feed para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="17f27-144">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="17f27-145">Para obter mais informações sobre a instalação das Ferramentas Globais, confira [Visão geral das Ferramentas Globais do .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="17f27-145">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="17f27-146">Se a instalação for bem-sucedida, será exibida uma mensagem mostrando o comando usado para chamar a ferramenta e a versão instalada, de maneira semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="17f27-146">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="17f27-147">Agora você deve ser capaz de digitar `botsay` e obter uma resposta da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="17f27-147">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="17f27-148">Se a instalação for bem-sucedida, mas não for possível usar o comando `botsay`, talvez você precise abrir um novo terminal para atualizar o PATH.</span><span class="sxs-lookup"><span data-stu-id="17f27-148">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="17f27-149">Remover a ferramenta</span><span class="sxs-lookup"><span data-stu-id="17f27-149">Remove the tool</span></span>

<span data-ttu-id="17f27-150">Quando terminar suas experiências com a ferramenta, você poderá removê-la com o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="17f27-150">Once you're done experimenting with the tool, you can remove it with the following commnand:</span></span>

```console
dotnet tool uninstall -g botsay
```
