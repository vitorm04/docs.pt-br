---
title: Comando dotnet new – CLI do .NET Core
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
author: mairaw
ms.author: mairaw
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 4432587c0015c353a34816eee4206dc53cdefba9
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="dotnet-new"></a><span data-ttu-id="61b29-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="61b29-103">dotnet new</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="61b29-104">Nome</span><span class="sxs-lookup"><span data-stu-id="61b29-104">Name</span></span>

<span data-ttu-id="61b29-105">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="61b29-105">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="61b29-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="61b29-106">Synopsis</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="61b29-107">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="61b29-107">.NET Core 2.0</span></span>](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="61b29-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="61b29-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="61b29-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="61b29-109">Description</span></span>

<span data-ttu-id="61b29-110">O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido.</span><span class="sxs-lookup"><span data-stu-id="61b29-110">The `dotnet new` command provides a convenient way to initialize a valid .NET Core project.</span></span>

<span data-ttu-id="61b29-111">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="61b29-111">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="61b29-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="61b29-112">Arguments</span></span>

`TEMPLATE`

<span data-ttu-id="61b29-113">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="61b29-113">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="61b29-114">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="61b29-114">Each template might have specific options you can pass.</span></span> <span data-ttu-id="61b29-115">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="61b29-115">For more information, see [Template options](#template-options).</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="61b29-116">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="61b29-116">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="61b29-117">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="61b29-117">The command contains a default list of templates.</span></span> <span data-ttu-id="61b29-118">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="61b29-118">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="61b29-119">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="61b29-119">The following table shows the templates that come pre-installed with the .NET Core 2.0 SDK.</span></span> <span data-ttu-id="61b29-120">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="61b29-120">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="61b29-121">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="61b29-121">Template description</span></span>                          | <span data-ttu-id="61b29-122">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="61b29-122">Template name</span></span> | <span data-ttu-id="61b29-123">Linguagens</span><span class="sxs-lookup"><span data-stu-id="61b29-123">Languages</span></span>     |
|----------------------------------------------|---------------|---------------|
| <span data-ttu-id="61b29-124">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="61b29-124">Console application</span></span>                          | `console`     | <span data-ttu-id="61b29-125">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="61b29-125">[C#], F#, VB</span></span>  |
| <span data-ttu-id="61b29-126">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="61b29-126">Class library</span></span>                                | `classlib`    | <span data-ttu-id="61b29-127">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="61b29-127">[C#], F#, VB</span></span>  |
| <span data-ttu-id="61b29-128">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="61b29-128">Unit test project</span></span>                            | `mstest`      | <span data-ttu-id="61b29-129">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="61b29-129">[C#], F#, VB</span></span>  |
| <span data-ttu-id="61b29-130">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="61b29-130">xUnit test project</span></span>                           | `xunit`       | <span data-ttu-id="61b29-131">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="61b29-131">[C#], F#, VB</span></span>  |
| <span data-ttu-id="61b29-132">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="61b29-132">ASP.NET Core empty</span></span>                           | `web`         | <span data-ttu-id="61b29-133">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-133">[C#], F#</span></span>      |
| <span data-ttu-id="61b29-134">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="61b29-134">ASP.NET Core Web App (Model-View-Controller)</span></span> | `mvc`         | <span data-ttu-id="61b29-135">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-135">[C#], F#</span></span>      |
| <span data-ttu-id="61b29-136">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61b29-136">ASP.NET Core Web App</span></span>                         | `razor`       | <span data-ttu-id="61b29-137">[C#]</span><span class="sxs-lookup"><span data-stu-id="61b29-137">[C#]</span></span>          |
| <span data-ttu-id="61b29-138">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="61b29-138">ASP.NET Core with Angular</span></span>                    | `angular`     | <span data-ttu-id="61b29-139">[C#]</span><span class="sxs-lookup"><span data-stu-id="61b29-139">[C#]</span></span>          |
| <span data-ttu-id="61b29-140">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="61b29-140">ASP.NET Core with React.js</span></span>                   | `react`       | <span data-ttu-id="61b29-141">[C#]</span><span class="sxs-lookup"><span data-stu-id="61b29-141">[C#]</span></span>          |
| <span data-ttu-id="61b29-142">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="61b29-142">ASP.NET Core with React.js and Redux</span></span>         | `reactredux`  | <span data-ttu-id="61b29-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="61b29-143">[C#]</span></span>          |
| <span data-ttu-id="61b29-144">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61b29-144">ASP.NET Core Web API</span></span>                         | `webapi`      | <span data-ttu-id="61b29-145">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-145">[C#], F#</span></span>      |
| <span data-ttu-id="61b29-146">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="61b29-146">global.json file</span></span>                             | `globaljson`  |               |
| <span data-ttu-id="61b29-147">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="61b29-147">Nuget config</span></span>                                 | `nugetconfig` |               |
| <span data-ttu-id="61b29-148">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="61b29-148">Web config</span></span>                                   | `webconfig`   |               |
| <span data-ttu-id="61b29-149">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="61b29-149">Solution file</span></span>                                | `sln`         |               |
| <span data-ttu-id="61b29-150">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="61b29-150">Razor page</span></span>                                   | `page`        |               |
| <span data-ttu-id="61b29-151">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="61b29-151">MVC ViewImports</span></span>                              | `viewimports` |               |
| <span data-ttu-id="61b29-152">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="61b29-152">MVC ViewStart</span></span>                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="61b29-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="61b29-153">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="61b29-154">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="61b29-154">The command contains a default list of templates.</span></span> <span data-ttu-id="61b29-155">Use `dotnet new -all` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="61b29-155">Use `dotnet new -all` to obtain a list of the available templates.</span></span> <span data-ttu-id="61b29-156">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="61b29-156">The following table shows the templates that come pre-installed with the .NET Core 1.x SDK.</span></span> <span data-ttu-id="61b29-157">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="61b29-157">The default language for the template is shown inside the brackets.</span></span>

|<span data-ttu-id="61b29-158">Descrição do modelo</span><span class="sxs-lookup"><span data-stu-id="61b29-158">Template description</span></span>  | <span data-ttu-id="61b29-159">Nome do modelo</span><span class="sxs-lookup"><span data-stu-id="61b29-159">Template name</span></span> | <span data-ttu-id="61b29-160">Linguagens</span><span class="sxs-lookup"><span data-stu-id="61b29-160">Languages</span></span> |
|----------------------|---------------|-----------|
| <span data-ttu-id="61b29-161">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="61b29-161">Console application</span></span>  | `console`     | <span data-ttu-id="61b29-162">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-162">[C#], F#</span></span>  |
| <span data-ttu-id="61b29-163">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="61b29-163">Class library</span></span>        | `classlib`    | <span data-ttu-id="61b29-164">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-164">[C#], F#</span></span>  |
| <span data-ttu-id="61b29-165">Projeto de teste de unidade</span><span class="sxs-lookup"><span data-stu-id="61b29-165">Unit test project</span></span>    | `mstest`      | <span data-ttu-id="61b29-166">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-166">[C#], F#</span></span>  |
| <span data-ttu-id="61b29-167">Projeto de teste de xUnit</span><span class="sxs-lookup"><span data-stu-id="61b29-167">xUnit test project</span></span>   | `xunit`       | <span data-ttu-id="61b29-168">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-168">[C#], F#</span></span>  |
| <span data-ttu-id="61b29-169">ASP.NET Core vazio</span><span class="sxs-lookup"><span data-stu-id="61b29-169">ASP.NET Core empty</span></span>   | `web`         | <span data-ttu-id="61b29-170">[C#]</span><span class="sxs-lookup"><span data-stu-id="61b29-170">[C#]</span></span>      |
| <span data-ttu-id="61b29-171">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61b29-171">ASP.NET Core Web App</span></span> | `mvc`         | <span data-ttu-id="61b29-172">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="61b29-172">[C#], F#</span></span>  |
| <span data-ttu-id="61b29-173">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="61b29-173">ASP.NET Core Web API</span></span> | `webapi`      | <span data-ttu-id="61b29-174">[C#]</span><span class="sxs-lookup"><span data-stu-id="61b29-174">[C#]</span></span>      |
| <span data-ttu-id="61b29-175">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="61b29-175">Nuget config</span></span>         | `nugetconfig` |           |
| <span data-ttu-id="61b29-176">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="61b29-176">Web config</span></span>           | `webconfig`   |           |
| <span data-ttu-id="61b29-177">Arquivo de solução</span><span class="sxs-lookup"><span data-stu-id="61b29-177">Solution file</span></span>        | `sln`         |           |

---

## <a name="options"></a><span data-ttu-id="61b29-178">Opções</span><span class="sxs-lookup"><span data-stu-id="61b29-178">Options</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="61b29-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="61b29-179">.NET Core 2.0</span></span>](#tab/netcore2x)

`--force`

<span data-ttu-id="61b29-180">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="61b29-180">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="61b29-181">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-181">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="61b29-182">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="61b29-182">Prints out help for the command.</span></span> <span data-ttu-id="61b29-183">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="61b29-183">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-i|--install <PATH|NUGET_ID>`

<span data-ttu-id="61b29-184">Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="61b29-184">Installs a source or template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="61b29-185">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="61b29-185">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="61b29-186">Por padrão, `dotnet new` passa \* para a versão, o que representa a última versão estável do pacote.</span><span class="sxs-lookup"><span data-stu-id="61b29-186">By default, `dotnet new` passes \* for the version, which represents the last stable package version.</span></span> <span data-ttu-id="61b29-187">Veja um exemplo na seção [Exemplos](#examples).</span><span class="sxs-lookup"><span data-stu-id="61b29-187">See an example at the [Examples](#examples) section.</span></span>

<span data-ttu-id="61b29-188">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="61b29-188">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

`-l|--list`

<span data-ttu-id="61b29-189">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="61b29-189">Lists templates containing the specified name.</span></span> <span data-ttu-id="61b29-190">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="61b29-190">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="61b29-191">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-191">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#|VB}`

<span data-ttu-id="61b29-192">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="61b29-192">The language of the template to create.</span></span> <span data-ttu-id="61b29-193">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="61b29-193">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="61b29-194">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="61b29-194">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="61b29-195">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="61b29-195">The name for the created output.</span></span> <span data-ttu-id="61b29-196">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="61b29-196">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="61b29-197">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="61b29-197">Location to place the generated output.</span></span> <span data-ttu-id="61b29-198">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="61b29-198">The default is the current directory.</span></span>

`--type`

<span data-ttu-id="61b29-199">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="61b29-199">Filters templates based on available types.</span></span> <span data-ttu-id="61b29-200">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="61b29-200">Predefined values are "project", "item" or "other".</span></span>

`-u|--uninstall <PATH|NUGET_ID>`

<span data-ttu-id="61b29-201">Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="61b29-201">Uninstalls a source or template pack at the `PATH` or `NUGET_ID` provided.</span></span>

> [!NOTE]
> <span data-ttu-id="61b29-202">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="61b29-202">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="61b29-203">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="61b29-203">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="61b29-204">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="61b29-204">Additionally, do not include a final terminating directory slash on your template path.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="61b29-205">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="61b29-205">.NET Core 1.x</span></span>](#tab/netcore1x)

`-all|--show-all`

<span data-ttu-id="61b29-206">Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado.</span><span class="sxs-lookup"><span data-stu-id="61b29-206">Shows all templates for a specific type of project when running in the context of the `dotnet new` command alone.</span></span> <span data-ttu-id="61b29-207">Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força.</span><span class="sxs-lookup"><span data-stu-id="61b29-207">When running in the context of a specific template, such as `dotnet new web -all`, `-all` is interpreted as a force creation flag.</span></span> <span data-ttu-id="61b29-208">Isso é necessário quando o diretório de saída já contiver um projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-208">This is required when the output directory already contains a project.</span></span>

`-h|--help`

<span data-ttu-id="61b29-209">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="61b29-209">Prints out help for the command.</span></span> <span data-ttu-id="61b29-210">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="61b29-210">It can be invoked for the `dotnet new` command itself or for any template, such as `dotnet new mvc --help`.</span></span>

`-l|--list`

<span data-ttu-id="61b29-211">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="61b29-211">Lists templates containing the specified name.</span></span> <span data-ttu-id="61b29-212">Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="61b29-212">If invoked for the `dotnet new` command, it lists the possible templates available for the given directory.</span></span> <span data-ttu-id="61b29-213">Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-213">For example if the directory already contains a project, it doesn't list all project templates.</span></span>

`-lang|--language {C#|F#}`

<span data-ttu-id="61b29-214">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="61b29-214">The language of the template to create.</span></span> <span data-ttu-id="61b29-215">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="61b29-215">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="61b29-216">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="61b29-216">Not valid for some templates.</span></span>

    > [!NOTE]
    > Some shells interpret `#` as a special character. In those cases, you need to enclose the language parameter value, such as `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

<span data-ttu-id="61b29-217">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="61b29-217">The name for the created output.</span></span> <span data-ttu-id="61b29-218">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="61b29-218">If no name is specified, the name of the current directory is used.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="61b29-219">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="61b29-219">Location to place the generated output.</span></span> <span data-ttu-id="61b29-220">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="61b29-220">The default is the current directory.</span></span>

---

## <a name="template-options"></a><span data-ttu-id="61b29-221">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="61b29-221">Template options</span></span>

<span data-ttu-id="61b29-222">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="61b29-222">Each project template may have additional options available.</span></span> <span data-ttu-id="61b29-223">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="61b29-223">The core templates have the following additional options:</span></span>

# <a name="net-core-20tabnetcore2x"></a>[<span data-ttu-id="61b29-224">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="61b29-224">.NET Core 2.0</span></span>](#tab/netcore2x)

<span data-ttu-id="61b29-225">**console, angular, react, reactredux**</span><span class="sxs-lookup"><span data-stu-id="61b29-225">**console, angular, react, reactredux**</span></span>

  <span data-ttu-id="61b29-226">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-226">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="61b29-227">**classlib**</span><span class="sxs-lookup"><span data-stu-id="61b29-227">**classlib**</span></span>

<span data-ttu-id="61b29-228">`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="61b29-228">`-f|--framework <FRAMEWORK>` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="61b29-229">Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="61b29-229">Values: `netcoreapp2.0` to create a .NET Core Class Library or `netstandard2.0` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="61b29-230">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="61b29-230">The default value is `netstandard2.0`.</span></span>

<span data-ttu-id="61b29-231">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-231">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="61b29-232">**mstest, xunit**</span><span class="sxs-lookup"><span data-stu-id="61b29-232">**mstest, xunit**</span></span>

<span data-ttu-id="61b29-233">`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="61b29-233">`-p|--enable-pack` - Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

<span data-ttu-id="61b29-234">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-234">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="61b29-235">**globaljson**</span><span class="sxs-lookup"><span data-stu-id="61b29-235">**globaljson**</span></span>

<span data-ttu-id="61b29-236">`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="61b29-236">`--sdk-version <VERSION_NUMBER>` - Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

<span data-ttu-id="61b29-237">**web**</span><span class="sxs-lookup"><span data-stu-id="61b29-237">**web**</span></span>

<span data-ttu-id="61b29-238">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="61b29-238">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="61b29-239">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-239">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="61b29-240">**webapi**</span><span class="sxs-lookup"><span data-stu-id="61b29-240">**webapi**</span></span>

<span data-ttu-id="61b29-241">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="61b29-241">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="61b29-242">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="61b29-242">The possible values are:</span></span>

- <span data-ttu-id="61b29-243">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="61b29-243">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="61b29-244">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="61b29-244">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="61b29-245">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="61b29-245">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="61b29-246">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="61b29-246">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="61b29-247">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="61b29-247">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="61b29-248">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-248">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="61b29-249">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="61b29-249">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

<span data-ttu-id="61b29-250">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-250">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="61b29-251">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-251">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="61b29-252">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="61b29-252">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="61b29-253">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-253">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="61b29-254">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="61b29-254">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="61b29-255">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-255">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="61b29-256">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-256">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="61b29-257">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="61b29-257">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="61b29-258">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="61b29-258">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="61b29-259">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-259">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="61b29-260">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="61b29-260">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="61b29-261">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="61b29-261">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="61b29-262">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-262">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="61b29-263">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="61b29-263">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="61b29-264">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="61b29-264">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="61b29-265">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-265">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="61b29-266">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="61b29-266">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="61b29-267">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="61b29-267">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="61b29-268">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-268">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="61b29-269">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-269">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="61b29-270">**mvc, razor**</span><span class="sxs-lookup"><span data-stu-id="61b29-270">**mvc, razor**</span></span>

<span data-ttu-id="61b29-271">`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="61b29-271">`-au|--auth <AUTHENTICATION_TYPE>` - The type of authentication to use.</span></span> <span data-ttu-id="61b29-272">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="61b29-272">The possible values are:</span></span>

- <span data-ttu-id="61b29-273">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="61b29-273">`None` - No authentication (Default).</span></span>
- <span data-ttu-id="61b29-274">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="61b29-274">`Individual` - Individual authentication.</span></span>
- <span data-ttu-id="61b29-275">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="61b29-275">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
- <span data-ttu-id="61b29-276">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="61b29-276">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
- <span data-ttu-id="61b29-277">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="61b29-277">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
- <span data-ttu-id="61b29-278">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="61b29-278">`Windows` - Windows authentication.</span></span>

<span data-ttu-id="61b29-279">`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="61b29-279">`--aad-b2c-instance <INSTANCE>` - The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="61b29-280">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-280">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="61b29-281">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="61b29-281">The default value is `https://login.microsoftonline.com/tfp/` .</span></span>

<span data-ttu-id="61b29-282">`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-282">`-ssp|--susi-policy-id <ID>` - The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="61b29-283">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-283">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="61b29-284">`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-284">`-rp|--reset-password-policy-id <ID>` - The reset password policy ID for this project.</span></span> <span data-ttu-id="61b29-285">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-285">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="61b29-286">`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-286">`-ep|--edit-profile-policy-id <ID>` - The edit profile policy ID for this project.</span></span> <span data-ttu-id="61b29-287">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-287">Use with `IndividualB2C` authentication.</span></span>

<span data-ttu-id="61b29-288">`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="61b29-288">`--aad-instance <INSTANCE>` - The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="61b29-289">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-289">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="61b29-290">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="61b29-290">The default value is `https://login.microsoftonline.com/`.</span></span>

<span data-ttu-id="61b29-291">`--client-id <ID>` – A ID do cliente deste projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-291">`--client-id <ID>` - The Client ID for this project.</span></span> <span data-ttu-id="61b29-292">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-292">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="61b29-293">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="61b29-293">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

<span data-ttu-id="61b29-294">`--domain <DOMAIN>` – O domínio do locatário de diretório.</span><span class="sxs-lookup"><span data-stu-id="61b29-294">`--domain <DOMAIN>` - The domain for the directory tenant.</span></span> <span data-ttu-id="61b29-295">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-295">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="61b29-296">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="61b29-296">The default value is `qualified.domain.name`.</span></span>

<span data-ttu-id="61b29-297">`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="61b29-297">`--tenant-id <ID>` - The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="61b29-298">Use com a autenticação `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-298">Use with `SingleOrg` authentication..</span></span> <span data-ttu-id="61b29-299">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="61b29-299">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

<span data-ttu-id="61b29-300">`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="61b29-300">`--callback-path <PATH>` - The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="61b29-301">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-301">Use with `SingleOrg` or `IndividualB2C` authentication..</span></span> <span data-ttu-id="61b29-302">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="61b29-302">The default value is `/signin-oidc`.</span></span>

<span data-ttu-id="61b29-303">`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório.</span><span class="sxs-lookup"><span data-stu-id="61b29-303">`-r|--org-read-access` - Allows this application read-access to the directory.</span></span> <span data-ttu-id="61b29-304">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="61b29-304">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

<span data-ttu-id="61b29-305">`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="61b29-305">`--use-launch-settings` - Includes *launchSettings.json* in the generated template output.</span></span>

<span data-ttu-id="61b29-306">`--use-browserlink` – Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-306">`--use-browserlink` - Includes BrowserLink in the project.</span></span>

<span data-ttu-id="61b29-307">`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="61b29-307">`-uld|--use-local-db` - Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="61b29-308">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="61b29-308">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

<span data-ttu-id="61b29-309">`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="61b29-309">`--no-restore` - Doesn't perform an implicit restore during project creation.</span></span>

<span data-ttu-id="61b29-310">**page**</span><span class="sxs-lookup"><span data-stu-id="61b29-310">**page**</span></span>

<span data-ttu-id="61b29-311">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="61b29-311">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="61b29-312">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="61b29-312">The default value is `MyApp.Namespace`.</span></span>

<span data-ttu-id="61b29-313">`-np|--no-pagemodel` – Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="61b29-313">`-np|--no-pagemodel` - Creates the page without a PageModel.</span></span>

<span data-ttu-id="61b29-314">**viewimports**</span><span class="sxs-lookup"><span data-stu-id="61b29-314">**viewimports**</span></span>

<span data-ttu-id="61b29-315">`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado.</span><span class="sxs-lookup"><span data-stu-id="61b29-315">`-na|--namespace <NAMESPACE_NAME>`- Namespace for the generated code.</span></span> <span data-ttu-id="61b29-316">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="61b29-316">The default value is `MyApp.Namespace`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="61b29-317">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="61b29-317">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="61b29-318">**console, xunit, mstest, web, webapi** </span><span class="sxs-lookup"><span data-stu-id="61b29-318">**console, xunit, mstest, web, webapi**</span></span>

<span data-ttu-id="61b29-319">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="61b29-319">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="61b29-320">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="61b29-320">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="61b29-321">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="61b29-321">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="61b29-322">**classlib**</span><span class="sxs-lookup"><span data-stu-id="61b29-322">**classlib**</span></span>

<span data-ttu-id="61b29-323">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="61b29-323">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="61b29-324">Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`.</span><span class="sxs-lookup"><span data-stu-id="61b29-324">Values: `netcoreapp1.0`, `netcoreapp1.1`, or `netstandard1.0` to `netstandard1.6`.</span></span> <span data-ttu-id="61b29-325">O valor padrão é `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="61b29-325">The default value is `netstandard1.4`.</span></span>

<span data-ttu-id="61b29-326">**mvc**</span><span class="sxs-lookup"><span data-stu-id="61b29-326">**mvc**</span></span>

<span data-ttu-id="61b29-327">`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina.</span><span class="sxs-lookup"><span data-stu-id="61b29-327">`-f|--framework` - Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="61b29-328">Valores: `netcoreapp1.0` ou `netcoreapp1.1`.</span><span class="sxs-lookup"><span data-stu-id="61b29-328">Values: `netcoreapp1.0` or `netcoreapp1.1`.</span></span> <span data-ttu-id="61b29-329">O valor padrão é `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="61b29-329">The default value is `netcoreapp1.0`.</span></span>

<span data-ttu-id="61b29-330">`-au|--auth` – O tipo de autenticação usado.</span><span class="sxs-lookup"><span data-stu-id="61b29-330">`-au|--auth` - The type of authentication to use.</span></span> <span data-ttu-id="61b29-331">Valores: `None` ou `Individual`.</span><span class="sxs-lookup"><span data-stu-id="61b29-331">Values: `None` or `Individual`.</span></span> <span data-ttu-id="61b29-332">O valor padrão é `None`.</span><span class="sxs-lookup"><span data-stu-id="61b29-332">The default value is `None`.</span></span>

<span data-ttu-id="61b29-333">`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="61b29-333">`-uld|--use-local-db` - Specifies whether or not to use LocalDB instead of SQLite.</span></span> <span data-ttu-id="61b29-334">Valores: `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="61b29-334">Values: `true` or `false`.</span></span> <span data-ttu-id="61b29-335">O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="61b29-335">The default value is `false`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="61b29-336">Exemplos</span><span class="sxs-lookup"><span data-stu-id="61b29-336">Examples</span></span>

<span data-ttu-id="61b29-337">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="61b29-337">Create an F# console application project in the current directory:</span></span>

`dotnet new console -lang F#`

<span data-ttu-id="61b29-338">Crie um projeto de biblioteca de classes do .NET Standard no diretório especificado (disponível somente com o SDK do .NET Core 2.0 ou versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="61b29-338">Create a .NET Standard class library project in the specified directory (available only with .NET Core 2.0 SDK or later versions):</span></span>

`dotnet new classlib -lang VB -o MyLibrary`

<span data-ttu-id="61b29-339">Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="61b29-339">Create a new ASP.NET Core C# MVC application project in the current directory with no authentication targeting .NET Core 2.0:</span></span>

`dotnet new mvc -au None -f netcoreapp2.0`

<span data-ttu-id="61b29-340">Crie um novo aplicativo xUnit direcionando o .NET Core 2.0:</span><span class="sxs-lookup"><span data-stu-id="61b29-340">Create a new xUnit application targeting .NET Core 2.0:</span></span>

`dotnet new xunit --framework netcoreapp2.0`

<span data-ttu-id="61b29-341">Lista todos os modelos disponíveis para o MVC:</span><span class="sxs-lookup"><span data-stu-id="61b29-341">List all templates available for MVC:</span></span>

`dotnet new mvc -l`

<span data-ttu-id="61b29-342">Instale a versão 2.0 dos modelos de aplicativo de página única do ASP.NET Core (opção de comando disponível somente para o SDK do .NET Core 1.1 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="61b29-342">Install version 2.0 of the Single Page Application templates for ASP.NET Core (command option available for .NET Core SDK 1.1 and later versions only):</span></span>

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

## <a name="see-also"></a><span data-ttu-id="61b29-343">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61b29-343">See also</span></span>

[<span data-ttu-id="61b29-344">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="61b29-344">Custom templates for dotnet new</span></span>](custom-templates.md)  
<span data-ttu-id="61b29-345">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="61b29-345">[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md)</span></span>  
[<span data-ttu-id="61b29-346">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="61b29-346">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="61b29-347">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="61b29-347">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
