---
title: Criar um aplicativo do .NET Core com plug-ins
description: Saiba como criar um aplicativo do .NET Core compatível com plug-ins.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: 54a4459619ee69fc74a14da7ff7fe10a472a4433
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849437"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="0f1bc-103">Criar um aplicativo do .NET Core com plug-ins</span><span class="sxs-lookup"><span data-stu-id="0f1bc-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="0f1bc-104">Este tutorial mostra como:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="0f1bc-105">Estruturar um projeto para permitir plug-ins.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="0f1bc-106">Criar um <xref:System.Runtime.Loader.AssemblyLoadContext> personalizado para carregar cada plug-in.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="0f1bc-107">Usar o tipo `System.Runtime.Loader.AssemblyDependencyResolver` para permitir que os plug-ins tenham dependências.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="0f1bc-108">Criar plug-ins que possam ser implantados facilmente apenas copiando os artefatos de build.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f1bc-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="0f1bc-109">Prerequisites</span></span>

- <span data-ttu-id="0f1bc-110">Instale o [SDK do .NET Core 3.0 Versão Prévia 2](https://dotnet.microsoft.com/download) ou uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-110">Install the [.NET Core 3.0 Preview 2 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="0f1bc-111">Criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="0f1bc-111">Create the application</span></span>

<span data-ttu-id="0f1bc-112">A primeira etapa é criar o aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="0f1bc-113">Crie uma pasta e execute `dotnet new console -o AppWithPlugin` nela.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-113">Create a new folder, and in that folder run `dotnet new console -o AppWithPlugin`.</span></span> 
2. <span data-ttu-id="0f1bc-114">Para facilitar o build do projeto, crie um arquivo de solução do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-114">To make building the project easier, create a Visual Studio solution file.</span></span> <span data-ttu-id="0f1bc-115">Execute `dotnet new sln` na mesma pasta.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-115">Run `dotnet new sln` in the same folder.</span></span> 
3. <span data-ttu-id="0f1bc-116">Execute `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` para adicionar o projeto de aplicativo à solução.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-116">Run `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` to add the app project to the solution.</span></span>

<span data-ttu-id="0f1bc-117">Agora podemos preencher o esqueleto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="0f1bc-118">Substitua o código no arquivo *AppWithPlugin/Program.cs* pelo código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="0f1bc-119">Criar as interfaces do plug-in</span><span class="sxs-lookup"><span data-stu-id="0f1bc-119">Create the plugin interfaces</span></span>

<span data-ttu-id="0f1bc-120">A próxima etapa na criação de um aplicativo com plug-ins é definir a interface que os plug-ins precisam implementar.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="0f1bc-121">Sugerimos a criação de uma biblioteca de classes contendo todos os tipos que você planeja usar para a comunicação entre o aplicativo e os plug-ins.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="0f1bc-122">Essa divisão permite que você publique sua interface de plug-in como um pacote sem precisar enviar seu aplicativo completo.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="0f1bc-123">Na pasta raiz do projeto, execute `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="0f1bc-124">Além disso, execute `dotnet sln add PluginBase/PluginBase.csproj` para adicionar o projeto ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="0f1bc-125">Exclua o arquivo `PluginBase/Class1.cs` e crie um arquivo na pasta `PluginBase` chamada `ICommand.cs` com a seguinte definição de interface:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="0f1bc-126">Essa interface `ICommand` é aquela que todos os plug-ins implementarão.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="0f1bc-127">Agora que a interface `ICommand` está definida, o projeto de aplicativo pode ser um pouco mais preenchido.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="0f1bc-128">Adicione uma referência do projeto `AppWithPlugin` ao projeto `PluginBase` com o comando `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` na pasta raiz.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="0f1bc-129">Substitua o comentário `// Load commands from plugins` pelo seguinte snippet de código para permitir que os plug-ins sejam carregados dos caminhos de arquivo fornecidos:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="0f1bc-130">Em seguida, substitua o comentário `// Output the loaded commands` pelo snippet de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="0f1bc-131">Substitua o comentário `// Execute the command with the name passed as an argument` pelo snippet a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="0f1bc-132">E, finalmente, adicione métodos estáticos à classe `Program` denominada `LoadPlugin` e `CreateCommands`, como é mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="0f1bc-133">Carregar plug-ins</span><span class="sxs-lookup"><span data-stu-id="0f1bc-133">Load plugins</span></span>

<span data-ttu-id="0f1bc-134">Agora o aplicativo pode carregar os comandos e criar uma instância deles corretamente dos assemblies de plug-in carregados, mas ele ainda não pode carregar os assemblies de plug-in.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="0f1bc-135">Crie um arquivo chamado *PluginLoadContext.cs* na pasta *AppWithPlugin* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="0f1bc-136">O tipo `PluginLoadContext` é derivado do tipo <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="0f1bc-137">O tipo `AssemblyLoadContext` é um tipo especial no tempo de execução que permite que os desenvolvedores isolem os assemblies carregados em grupos diferentes para garantir que as versões do assembly não entrem em conflito.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="0f1bc-138">Além disso, um `AssemblyLoadContext` personalizado pode escolher caminhos diferentes de onde carregar os assemblies e substituir o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="0f1bc-139">O `PluginLoadContext` usa uma instância do tipo `AssemblyDependencyResolver` introduzida no .NET Core 3.0 para resolver nomes de assembly para caminhos.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="0f1bc-140">O objeto `AssemblyDependencyResolver` é construído com o caminho para uma biblioteca de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="0f1bc-141">Ele resolve assemblies e bibliotecas nativas para seus caminhos relativos com base no arquivo *.deps.json* da biblioteca de classes cujo caminho foi passado para o construtor `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-141">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="0f1bc-142">O `AssemblyLoadContext` personalizado permite que os plug-ins tenham suas próprias dependências e o `AssemblyDependencyResolver` facilita o carregamento correto das dependências.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="0f1bc-143">Agora que o projeto `AppWithPlugin` tem o tipo `PluginLoadContext`, atualize o método `Program.LoadPlugin` com o seguinte corpo:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="0f1bc-144">Com uma instância de `PluginLoadContext` diferente para cada plug-in, os plug-ins pode ter dependências diferentes ou mesmo conflitantes sem problemas.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="0f1bc-145">Criar um plug-in simples sem dependências</span><span class="sxs-lookup"><span data-stu-id="0f1bc-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="0f1bc-146">Novamente na pasta raiz, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="0f1bc-147">Execute `dotnet new classlib -o HelloPlugin` para criar um projeto de biblioteca de classes chamado `HelloPlugin`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-147">Run `dotnet new classlib -o HelloPlugin` to create a new class library project named `HelloPlugin`.</span></span>
2. <span data-ttu-id="0f1bc-148">Execute `dotnet sln add HelloPlugin/HelloPlugin.csproj` para adicionar o projeto à solução `AppWithPlugin`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-148">Run `dotnet sln add HelloPlugin/HelloPlugin.csproj` to add the project to the `AppWithPlugin` solution.</span></span> 
3. <span data-ttu-id="0f1bc-149">Substitua o arquivo *HelloPlugin/Class1.cs* por um arquivo chamado *HelloCommand.cs* com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="0f1bc-150">Agora, abra o arquivo *HelloPlugin.csproj*.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="0f1bc-151">Ele deve ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="0f1bc-152">Entre as marcas `<Project>`, adicione os seguintes elementos:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="0f1bc-153">O elemento `<Private>false</Private>` é muito importante.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="0f1bc-154">Ele informa ao MSBuild que ele não deve copiar o *PluginBase.dll* para o diretório de saída do HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="0f1bc-155">Se o assembly *PluginBase.dll* estiver presente no diretório de saída, o `PluginLoadContext` encontrará o assembly lá e o carregará ao carregar o assembly *HelloPlugin.dll*.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="0f1bc-156">Neste ponto, o tipo `HelloPlugin.HelloCommand` implementará a interface `ICommand` do *PluginBase.dll* no diretório de saída do projeto `HelloPlugin`, não a interface `ICommand` que é carregada no contexto de carregamento padrão.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="0f1bc-157">Como o tempo de execução considera esses dois tipos como tipos diferentes de assemblies diferentes, o método `AppWithPlugin.Program.CreateCommands` não localizará os comandos.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="0f1bc-158">Como resultado, os metadados `<Private>false</Private>` serão necessários para a referência ao assembly que contém as interfaces de plug-in.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="0f1bc-159">Agora que o projeto `HelloPlugin` está concluído, devemos atualizar o projeto `AppWithPlugin` para saber onde o plug-in `HelloPlugin` pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="0f1bc-160">Após o comentário `// Paths to plugins to load`, adicione `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` como um elemento da matriz `pluginPaths`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="0f1bc-161">Criar um plug-in com dependências de biblioteca</span><span class="sxs-lookup"><span data-stu-id="0f1bc-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="0f1bc-162">Quase todos os plug-ins são mais complexos do que um simples "Olá, Mundo", e muitos plug-ins têm dependências de outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="0f1bc-163">Os projetos de plug-in `JsonPlugin` e `OldJson` no exemplo mostram dois exemplos de plug-ins com dependências de pacotes NuGet em `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="0f1bc-164">Os arquivos de projeto em si não têm informações especiais sobre as referências do projeto, e (depois que os caminhos do plug-in são adicionados à matriz `pluginPaths`) os plug-ins são executados perfeitamente, mesmo que seja na mesma execução do aplicativo AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="0f1bc-165">No entanto, esses projetos não copiam os assemblies referenciados para seus diretórios de saída, portanto, os assemblies precisam estar presentes no computador do usuário para que os plug-ins funcionem.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="0f1bc-166">Há duas maneiras de contornar esse problema.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="0f1bc-167">A primeira opção é usar o comando `dotnet publish` para publicar a biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="0f1bc-168">Como alternativa, se você quer usar a saída do `dotnet build` para seu plug-in, adicione a propriedade `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` entre as marcas `<PropertyGroup>` no arquivo de projeto do plug-in.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="0f1bc-169">Veja o projeto de plug-in `XcopyablePlugin` como exemplo.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="0f1bc-170">Outros exemplos de plug-in na amostra</span><span class="sxs-lookup"><span data-stu-id="0f1bc-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="0f1bc-171">O código-fonte completo para este tutorial pode ser encontrado no [repositório dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="0f1bc-171">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="0f1bc-172">O exemplo completo inclui alguns outros exemplos do comportamento `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-172">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="0f1bc-173">Por exemplo, o objeto `AssemblyDependencyResolver` também pode resolver bibliotecas nativas, bem como assemblies satélites localizados incluídos em pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-173">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="0f1bc-174">O `UVPlugin` e `FrenchPlugin` no repositório de amostras demonstram esses cenários.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-174">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="0f1bc-175">Como referenciar um assembly de interface de plug-in definido em um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="0f1bc-175">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="0f1bc-176">Vamos supor que haja um aplicativo A que tenha uma interface de plug-in definida no pacote NuGet chamado `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-176">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="0f1bc-177">Como você referenciaria o pacote corretamente em seu projeto de plug-in?</span><span class="sxs-lookup"><span data-stu-id="0f1bc-177">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="0f1bc-178">Para as referências do projeto, o uso dos metadados `<Private>false</Private>` no elemento `ProjectReference` no arquivo de projeto impediu que a dll fosse copiada para a saída.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-178">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="0f1bc-179">Faça referenciar o pacote `A.PluginBase` corretamente, altere o elemento `<PackageReference>` no arquivo de projeto para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f1bc-179">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="0f1bc-180">Isso impede que os assemblies `A.PluginBase` sejam copiados para o diretório de saída do plug-in e garante que o plug-in use a versão A do `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-180">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="0f1bc-181">Recomendações de estrutura de destino do plug-in</span><span class="sxs-lookup"><span data-stu-id="0f1bc-181">Plugin target framework recommendations</span></span>

<span data-ttu-id="0f1bc-182">Como o carregamento de dependência do plug-in usa o arquivo *.deps.json*, há uma pegadinha em relação à estrutura de destino do plug-in.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-182">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="0f1bc-183">Especificamente, os plug-ins devem ser direcionados a um tempo de execução como o .NET Core 3.0 e não a uma versão do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-183">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="0f1bc-184">O arquivo *.deps.json* é gerado com base na estrutura de destino do projeto e, como muitos pacotes compatíveis com o .NET Standard enviam assemblies de referência para compilar no .NET Standard e assemblies de implementação para tempos de execução específicos, o *.deps.json* pode não reconhecer corretamente os assemblies de implementação ou obter a versão do .NET Standard de um assembly em vez da versão do .NET Core esperada.</span><span class="sxs-lookup"><span data-stu-id="0f1bc-184">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
