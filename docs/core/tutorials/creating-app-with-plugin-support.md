---
title: Criar um aplicativo do .NET Core com plug-ins
description: Saiba como criar um aplicativo do .NET Core compatível com plug-ins.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 5267a56d0742d8e1cae4a81c058bc4ee05e83b4e
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579497"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="3b83d-103">Criar um aplicativo do .NET Core com plug-ins</span><span class="sxs-lookup"><span data-stu-id="3b83d-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="3b83d-104">Este tutorial mostra como criar um <xref:System.Runtime.Loader.AssemblyLoadContext> personalizado para carregar plug-ins.</span><span class="sxs-lookup"><span data-stu-id="3b83d-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="3b83d-105">Um <xref:System.Runtime.Loader.AssemblyDependencyResolver> é usado para resolver as dependências do plug-in.</span><span class="sxs-lookup"><span data-stu-id="3b83d-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="3b83d-106">O tutorial isola corretamente as dependências do plug-in do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="3b83d-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="3b83d-107">Você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="3b83d-107">You'll learn how to:</span></span>

- <span data-ttu-id="3b83d-108">Estruturar um projeto para permitir plug-ins.</span><span class="sxs-lookup"><span data-stu-id="3b83d-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="3b83d-109">Criar um <xref:System.Runtime.Loader.AssemblyLoadContext> personalizado para carregar cada plug-in.</span><span class="sxs-lookup"><span data-stu-id="3b83d-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="3b83d-110">Usar o tipo <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> para permitir que os plug-ins tenham dependências.</span><span class="sxs-lookup"><span data-stu-id="3b83d-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="3b83d-111">Criar plug-ins que possam ser implantados facilmente apenas copiando os artefatos de build.</span><span class="sxs-lookup"><span data-stu-id="3b83d-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b83d-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3b83d-112">Prerequisites</span></span>

- <span data-ttu-id="3b83d-113">Instale o [SDK do .NET Core 3,0](https://dotnet.microsoft.com/download) ou uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="3b83d-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="3b83d-114">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3b83d-114">Create the application</span></span>

<span data-ttu-id="3b83d-115">A primeira etapa é criar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="3b83d-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="3b83d-116">Crie uma nova pasta e, nessa pasta, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3b83d-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="3b83d-117">Para facilitar a criação do projeto, crie um arquivo de solução do Visual Studio na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="3b83d-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="3b83d-118">Execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="3b83d-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="3b83d-119">Execute o seguinte comando para adicionar o projeto de aplicativo à solução:</span><span class="sxs-lookup"><span data-stu-id="3b83d-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="3b83d-120">Agora podemos preencher o esqueleto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b83d-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="3b83d-121">Substitua o código no arquivo *AppWithPlugin/Program.cs* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3b83d-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="3b83d-122">Criar as interfaces do plug-in</span><span class="sxs-lookup"><span data-stu-id="3b83d-122">Create the plugin interfaces</span></span>

<span data-ttu-id="3b83d-123">A próxima etapa na criação de um aplicativo com plug-ins é definir a interface que os plug-ins precisam implementar.</span><span class="sxs-lookup"><span data-stu-id="3b83d-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="3b83d-124">Sugerimos a criação de uma biblioteca de classes contendo todos os tipos que você planeja usar para a comunicação entre o aplicativo e os plug-ins.</span><span class="sxs-lookup"><span data-stu-id="3b83d-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="3b83d-125">Essa divisão permite que você publique sua interface de plug-in como um pacote sem precisar enviar seu aplicativo completo.</span><span class="sxs-lookup"><span data-stu-id="3b83d-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="3b83d-126">Na pasta raiz do projeto, execute `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="3b83d-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="3b83d-127">Além disso, execute `dotnet sln add PluginBase/PluginBase.csproj` para adicionar o projeto ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="3b83d-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="3b83d-128">Exclua o arquivo `PluginBase/Class1.cs` e crie um arquivo na pasta `PluginBase` chamada `ICommand.cs` com a seguinte definição de interface:</span><span class="sxs-lookup"><span data-stu-id="3b83d-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="3b83d-129">Essa interface `ICommand` é aquela que todos os plug-ins implementarão.</span><span class="sxs-lookup"><span data-stu-id="3b83d-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="3b83d-130">Agora que a interface `ICommand` está definida, o projeto de aplicativo pode ser um pouco mais preenchido.</span><span class="sxs-lookup"><span data-stu-id="3b83d-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="3b83d-131">Adicione uma referência do projeto `AppWithPlugin` ao projeto `PluginBase` com o comando `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` na pasta raiz.</span><span class="sxs-lookup"><span data-stu-id="3b83d-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="3b83d-132">Substitua o comentário `// Load commands from plugins` pelo seguinte snippet de código para permitir que os plug-ins sejam carregados dos caminhos de arquivo fornecidos:</span><span class="sxs-lookup"><span data-stu-id="3b83d-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

<span data-ttu-id="3b83d-133">Em seguida, substitua o comentário `// Output the loaded commands` pelo snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3b83d-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="3b83d-134">Substitua o comentário `// Execute the command with the name passed as an argument` pelo snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="3b83d-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="3b83d-135">E, finalmente, adicione métodos estáticos à classe `Program` denominada `LoadPlugin` e `CreateCommands`, como é mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="3b83d-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a><span data-ttu-id="3b83d-136">Carregar plug-ins</span><span class="sxs-lookup"><span data-stu-id="3b83d-136">Load plugins</span></span>

<span data-ttu-id="3b83d-137">Agora, o aplicativo pode carregar e instanciar corretamente os comandos de assemblies de plug-in carregados, mas ainda não consegue carregar os assemblies de plug-in.</span><span class="sxs-lookup"><span data-stu-id="3b83d-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="3b83d-138">Crie um arquivo chamado *PluginLoadContext.cs* na pasta *AppWithPlugin* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="3b83d-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="3b83d-139">O tipo `PluginLoadContext` é derivado do tipo <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="3b83d-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="3b83d-140">O tipo de `AssemblyLoadContext` é um tipo especial no tempo de execução que permite aos desenvolvedores isolar assemblies carregados em grupos diferentes para garantir que as versões do assembly não entrem em conflito.</span><span class="sxs-lookup"><span data-stu-id="3b83d-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="3b83d-141">Além disso, um `AssemblyLoadContext` personalizado pode escolher caminhos diferentes de onde carregar os assemblies e substituir o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="3b83d-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="3b83d-142">O `PluginLoadContext` usa uma instância do tipo `AssemblyDependencyResolver` introduzida no .NET Core 3.0 para resolver nomes de assembly para caminhos.</span><span class="sxs-lookup"><span data-stu-id="3b83d-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="3b83d-143">O objeto `AssemblyDependencyResolver` é construído com o caminho para uma biblioteca de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="3b83d-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="3b83d-144">Ele resolve assemblies e bibliotecas nativas para seus caminhos relativos com base no arquivo *.deps.json* da biblioteca de classes cujo caminho foi passado para o construtor `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="3b83d-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="3b83d-145">O `AssemblyLoadContext` personalizado permite que os plug-ins tenham suas próprias dependências e o `AssemblyDependencyResolver` facilita o carregamento correto das dependências.</span><span class="sxs-lookup"><span data-stu-id="3b83d-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="3b83d-146">Agora que o projeto `AppWithPlugin` tem o tipo `PluginLoadContext`, atualize o método `Program.LoadPlugin` com o seguinte corpo:</span><span class="sxs-lookup"><span data-stu-id="3b83d-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

<span data-ttu-id="3b83d-147">Com uma instância de `PluginLoadContext` diferente para cada plug-in, os plug-ins pode ter dependências diferentes ou mesmo conflitantes sem problemas.</span><span class="sxs-lookup"><span data-stu-id="3b83d-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="3b83d-148">Plug-in simples sem dependências</span><span class="sxs-lookup"><span data-stu-id="3b83d-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="3b83d-149">Novamente na pasta raiz, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3b83d-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="3b83d-150">Execute o seguinte comando para criar um novo projeto de biblioteca de classes chamado `HelloPlugin`:</span><span class="sxs-lookup"><span data-stu-id="3b83d-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="3b83d-151">Execute o seguinte comando para adicionar o projeto à solução de `AppWithPlugin`:</span><span class="sxs-lookup"><span data-stu-id="3b83d-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="3b83d-152">Substitua o arquivo *HelloPlugin/Class1.cs* por um arquivo chamado *HelloCommand.cs* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="3b83d-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="3b83d-153">Agora, abra o arquivo *HelloPlugin.csproj*.</span><span class="sxs-lookup"><span data-stu-id="3b83d-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="3b83d-154">Ele deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="3b83d-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="3b83d-155">Entre as marcas `<Project>`, adicione os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="3b83d-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="3b83d-156">O elemento `<Private>false</Private>` é importante.</span><span class="sxs-lookup"><span data-stu-id="3b83d-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="3b83d-157">Ele informa ao MSBuild que ele não deve copiar o *PluginBase.dll* para o diretório de saída do HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="3b83d-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="3b83d-158">Se o assembly *PluginBase.dll* estiver presente no diretório de saída, o `PluginLoadContext` encontrará o assembly lá e o carregará ao carregar o assembly *HelloPlugin.dll*.</span><span class="sxs-lookup"><span data-stu-id="3b83d-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="3b83d-159">Neste ponto, o tipo `HelloPlugin.HelloCommand` implementará a interface `ICommand` do *PluginBase.dll* no diretório de saída do projeto `HelloPlugin`, não a interface `ICommand` que é carregada no contexto de carregamento padrão.</span><span class="sxs-lookup"><span data-stu-id="3b83d-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="3b83d-160">Como o tempo de execução vê esses dois tipos como tipos diferentes de assemblies diferentes, o método `AppWithPlugin.Program.CreateCommands` não encontrará os comandos.</span><span class="sxs-lookup"><span data-stu-id="3b83d-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="3b83d-161">Como resultado, os metadados `<Private>false</Private>` serão necessários para a referência ao assembly que contém as interfaces de plug-in.</span><span class="sxs-lookup"><span data-stu-id="3b83d-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="3b83d-162">Agora que o projeto `HelloPlugin` está concluído, devemos atualizar o projeto `AppWithPlugin` para saber onde o plug-in `HelloPlugin` pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="3b83d-162">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="3b83d-163">Após o comentário `// Paths to plugins to load`, adicione `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` como um elemento da matriz `pluginPaths`.</span><span class="sxs-lookup"><span data-stu-id="3b83d-163">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="3b83d-164">Plug-in com dependências de biblioteca</span><span class="sxs-lookup"><span data-stu-id="3b83d-164">Plugin with library dependencies</span></span>

<span data-ttu-id="3b83d-165">Quase todos os plug-ins são mais complexos do que um simples "Olá, Mundo", e muitos plug-ins têm dependências de outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="3b83d-165">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="3b83d-166">Os projetos de plug-in `JsonPlugin` e `OldJson` no exemplo mostram dois exemplos de plug-ins com dependências de pacotes NuGet em `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="3b83d-166">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="3b83d-167">Os próprios arquivos do projeto não têm nenhuma informação especial para as referências do projeto e (depois de adicionar os caminhos do plug-in à matriz de `pluginPaths`), os plug-ins são executados perfeitamente, mesmo que sejam executados na mesma execução do aplicativo AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="3b83d-167">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="3b83d-168">No entanto, esses projetos não copiam os assemblies referenciados para o diretório de saída, de modo que os assemblies precisam estar presentes na máquina do usuário para que os plug-ins funcionem.</span><span class="sxs-lookup"><span data-stu-id="3b83d-168">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="3b83d-169">Há duas maneiras de contornar esse problema.</span><span class="sxs-lookup"><span data-stu-id="3b83d-169">There are two ways to work around this problem.</span></span> <span data-ttu-id="3b83d-170">A primeira opção é usar o comando `dotnet publish` para publicar a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="3b83d-170">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="3b83d-171">Como alternativa, se você quer usar a saída do `dotnet build` para seu plug-in, adicione a propriedade `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` entre as marcas `<PropertyGroup>` no arquivo de projeto do plug-in.</span><span class="sxs-lookup"><span data-stu-id="3b83d-171">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="3b83d-172">Veja o projeto de plug-in `XcopyablePlugin` como exemplo.</span><span class="sxs-lookup"><span data-stu-id="3b83d-172">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="3b83d-173">Outros exemplos no exemplo</span><span class="sxs-lookup"><span data-stu-id="3b83d-173">Other examples in the sample</span></span>

<span data-ttu-id="3b83d-174">O código-fonte completo para este tutorial pode ser encontrado no [repositório dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="3b83d-174">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="3b83d-175">O exemplo completo inclui alguns outros exemplos do comportamento `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="3b83d-175">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="3b83d-176">Por exemplo, o objeto `AssemblyDependencyResolver` também pode resolver bibliotecas nativas, bem como assemblies satélites localizados incluídos em pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="3b83d-176">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="3b83d-177">O `UVPlugin` e `FrenchPlugin` no repositório de amostras demonstram esses cenários.</span><span class="sxs-lookup"><span data-stu-id="3b83d-177">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-from-a-nuget-package"></a><span data-ttu-id="3b83d-178">Referenciar um plug-in de um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="3b83d-178">Reference a plugin from a NuGet package</span></span>

<span data-ttu-id="3b83d-179">Vamos supor que haja um aplicativo A que tenha uma interface de plug-in definida no pacote NuGet chamado `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="3b83d-179">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="3b83d-180">Como você referenciaria o pacote corretamente em seu projeto de plug-in?</span><span class="sxs-lookup"><span data-stu-id="3b83d-180">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="3b83d-181">Para as referências do projeto, o uso dos metadados `<Private>false</Private>` no elemento `ProjectReference` no arquivo de projeto impediu que a dll fosse copiada para a saída.</span><span class="sxs-lookup"><span data-stu-id="3b83d-181">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="3b83d-182">Faça referenciar o pacote `A.PluginBase` corretamente, altere o elemento `<PackageReference>` no arquivo de projeto para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3b83d-182">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="3b83d-183">Isso impede que os assemblies `A.PluginBase` sejam copiados para o diretório de saída do plug-in e garante que o plug-in use a versão A do `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="3b83d-183">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="3b83d-184">Recomendações de estrutura de destino do plug-in</span><span class="sxs-lookup"><span data-stu-id="3b83d-184">Plugin target framework recommendations</span></span>

<span data-ttu-id="3b83d-185">Como o carregamento de dependência do plug-in usa o arquivo *.deps.json*, há uma pegadinha em relação à estrutura de destino do plug-in.</span><span class="sxs-lookup"><span data-stu-id="3b83d-185">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="3b83d-186">Especificamente, os plug-ins devem ser direcionados a um runtime como o .NET Core 3.0 e não a uma versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3b83d-186">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="3b83d-187">O arquivo *.deps.json* é gerado com base na estrutura de destino do projeto e, como muitos pacotes compatíveis com o .NET Standard enviam assemblies de referência para compilar no .NET Standard e assemblies de implementação para tempos de execução específicos, o *.deps.json* pode não reconhecer corretamente os assemblies de implementação ou obter a versão do .NET Standard de um assembly em vez da versão do .NET Core esperada.</span><span class="sxs-lookup"><span data-stu-id="3b83d-187">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
