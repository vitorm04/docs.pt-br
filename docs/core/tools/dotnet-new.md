---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 04/10/2020
ms.openlocfilehash: 4ad0d7e54f93582237ed9457b562957018916d36
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463606"
---
# <a name="dotnet-new"></a><span data-ttu-id="d2f16-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2f16-103">dotnet new</span></span>

<span data-ttu-id="d2f16-104">**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d2f16-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d2f16-105">Nome</span><span class="sxs-lookup"><span data-stu-id="d2f16-105">Name</span></span>

<span data-ttu-id="d2f16-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d2f16-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d2f16-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a><span data-ttu-id="d2f16-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2f16-108">Description</span></span>

<span data-ttu-id="d2f16-109">O `dotnet new` comando cria um projeto .NET Core ou outros artefatos baseados em um modelo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="d2f16-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="d2f16-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="d2f16-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d2f16-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="d2f16-112">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="d2f16-113">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="d2f16-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="d2f16-114">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="d2f16-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="d2f16-115">Você pode `dotnet new --list` correr para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="d2f16-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="d2f16-116">Se `TEMPLATE` o valor não for uma correspondência exata no texto na coluna **Modelos** ou **Nome Curto** da tabela retornada, uma correspondência de substring será realizada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="d2f16-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="d2f16-117">Começando com o .NET Core 3.0 SDK, a CLI `dotnet new` procura modelos em NuGet.org quando você invoca o comando nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="d2f16-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="d2f16-118">Se a CLI não conseguir encontrar uma `dotnet new`correspondência de modelo ao invocar, nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="d2f16-118">If the CLI can't find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="d2f16-119">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="d2f16-119">If there's a newer version of the template available.</span></span> <span data-ttu-id="d2f16-120">Neste caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="d2f16-121">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="d2f16-121">The command contains a default list of templates.</span></span> <span data-ttu-id="d2f16-122">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d2f16-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="d2f16-123">A tabela a seguir mostra os modelos que vêm pré-instalados com o .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="d2f16-124">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="d2f16-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="d2f16-125">Clique no link nome curto para ver as opções específicas de modelo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="d2f16-126">Modelos</span><span class="sxs-lookup"><span data-stu-id="d2f16-126">Templates</span></span>                                    | <span data-ttu-id="d2f16-127">Nome curto</span><span class="sxs-lookup"><span data-stu-id="d2f16-127">Short name</span></span>                      | <span data-ttu-id="d2f16-128">Linguagem</span><span class="sxs-lookup"><span data-stu-id="d2f16-128">Language</span></span>     | <span data-ttu-id="d2f16-129">Marcas</span><span class="sxs-lookup"><span data-stu-id="d2f16-129">Tags</span></span>                                  | <span data-ttu-id="d2f16-130">Introduzido</span><span class="sxs-lookup"><span data-stu-id="d2f16-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="d2f16-131">Aplicativo do Console</span><span class="sxs-lookup"><span data-stu-id="d2f16-131">Console Application</span></span>                          | [<span data-ttu-id="d2f16-132">Console</span><span class="sxs-lookup"><span data-stu-id="d2f16-132">console</span></span>](#console)             | <span data-ttu-id="d2f16-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2f16-133">[C#], F#, VB</span></span> | <span data-ttu-id="d2f16-134">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="d2f16-134">Common/Console</span></span>                        | <span data-ttu-id="d2f16-135">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-135">1.0</span></span>        |
| <span data-ttu-id="d2f16-136">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="d2f16-136">Class library</span></span>                                | [<span data-ttu-id="d2f16-137">classlib</span><span class="sxs-lookup"><span data-stu-id="d2f16-137">classlib</span></span>](#classlib)           | <span data-ttu-id="d2f16-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2f16-138">[C#], F#, VB</span></span> | <span data-ttu-id="d2f16-139">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="d2f16-139">Common/Library</span></span>                        | <span data-ttu-id="d2f16-140">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-140">1.0</span></span>        |
| <span data-ttu-id="d2f16-141">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-141">WPF Application</span></span>                              | [<span data-ttu-id="d2f16-142">Wpf</span><span class="sxs-lookup"><span data-stu-id="d2f16-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="d2f16-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-143">[C#]</span></span>         | <span data-ttu-id="d2f16-144">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-144">Common/WPF</span></span>                            | <span data-ttu-id="d2f16-145">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-145">3.0</span></span>        |
| <span data-ttu-id="d2f16-146">Biblioteca de classe WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-146">WPF Class library</span></span>                            | [<span data-ttu-id="d2f16-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="d2f16-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="d2f16-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-148">[C#]</span></span>         | <span data-ttu-id="d2f16-149">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-149">Common/WPF</span></span>                            | <span data-ttu-id="d2f16-150">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-150">3.0</span></span>        |
| <span data-ttu-id="d2f16-151">Biblioteca de Controles Personalizados do WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="d2f16-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="d2f16-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="d2f16-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-153">[C#]</span></span>         | <span data-ttu-id="d2f16-154">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-154">Common/WPF</span></span>                            | <span data-ttu-id="d2f16-155">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-155">3.0</span></span>        |
| <span data-ttu-id="d2f16-156">Biblioteca de controle de usuário WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="d2f16-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d2f16-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="d2f16-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-158">[C#]</span></span>         | <span data-ttu-id="d2f16-159">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="d2f16-159">Common/WPF</span></span>                            | <span data-ttu-id="d2f16-160">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-160">3.0</span></span>        |
| <span data-ttu-id="d2f16-161">Aplicativo Formulários do Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="d2f16-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="d2f16-162">Winforms</span><span class="sxs-lookup"><span data-stu-id="d2f16-162">winforms</span></span>](#winforms)           | <span data-ttu-id="d2f16-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-163">[C#]</span></span>         | <span data-ttu-id="d2f16-164">Formas comuns/winforms</span><span class="sxs-lookup"><span data-stu-id="d2f16-164">Common/WinForms</span></span>                       | <span data-ttu-id="d2f16-165">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-165">3.0</span></span>        |
| <span data-ttu-id="d2f16-166">Biblioteca de classes de Formulários do Windows (WinForms)</span><span class="sxs-lookup"><span data-stu-id="d2f16-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="d2f16-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="d2f16-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="d2f16-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-168">[C#]</span></span>         | <span data-ttu-id="d2f16-169">Formas comuns/winforms</span><span class="sxs-lookup"><span data-stu-id="d2f16-169">Common/WinForms</span></span>                       | <span data-ttu-id="d2f16-170">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-170">3.0</span></span>        |
| <span data-ttu-id="d2f16-171">Serviço ao Trabalhador</span><span class="sxs-lookup"><span data-stu-id="d2f16-171">Worker Service</span></span>                               | [<span data-ttu-id="d2f16-172">Trabalhador</span><span class="sxs-lookup"><span data-stu-id="d2f16-172">worker</span></span>](#web-others)           | <span data-ttu-id="d2f16-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-173">[C#]</span></span>         | <span data-ttu-id="d2f16-174">Comum/Trabalhador/Web</span><span class="sxs-lookup"><span data-stu-id="d2f16-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="d2f16-175">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-175">3.0</span></span>        |
| <span data-ttu-id="d2f16-176">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="d2f16-176">Unit Test Project</span></span>                            | [<span data-ttu-id="d2f16-177">Mstest</span><span class="sxs-lookup"><span data-stu-id="d2f16-177">mstest</span></span>](#test)                 | <span data-ttu-id="d2f16-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2f16-178">[C#], F#, VB</span></span> | <span data-ttu-id="d2f16-179">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="d2f16-179">Test/MSTest</span></span>                           | <span data-ttu-id="d2f16-180">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-180">1.0</span></span>        |
| <span data-ttu-id="d2f16-181">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="d2f16-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="d2f16-182">Nunit</span><span class="sxs-lookup"><span data-stu-id="d2f16-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="d2f16-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2f16-183">[C#], F#, VB</span></span> | <span data-ttu-id="d2f16-184">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="d2f16-184">Test/NUnit</span></span>                            | <span data-ttu-id="d2f16-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="d2f16-185">2.1.400</span></span>    |
| <span data-ttu-id="d2f16-186">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="d2f16-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="d2f16-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2f16-187">[C#], F#, VB</span></span> | <span data-ttu-id="d2f16-188">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="d2f16-188">Test/NUnit</span></span>                            | <span data-ttu-id="d2f16-189">2.2</span><span class="sxs-lookup"><span data-stu-id="d2f16-189">2.2</span></span>        |
| <span data-ttu-id="d2f16-190">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="d2f16-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="d2f16-191">Xunit</span><span class="sxs-lookup"><span data-stu-id="d2f16-191">xunit</span></span>](#test)                  | <span data-ttu-id="d2f16-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="d2f16-192">[C#], F#, VB</span></span> | <span data-ttu-id="d2f16-193">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="d2f16-193">Test/xUnit</span></span>                            | <span data-ttu-id="d2f16-194">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-194">1.0</span></span>        |
| <span data-ttu-id="d2f16-195">Componente da navalha</span><span class="sxs-lookup"><span data-stu-id="d2f16-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="d2f16-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-196">[C#]</span></span>         | <span data-ttu-id="d2f16-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2f16-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f16-198">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-198">3.0</span></span>        |
| <span data-ttu-id="d2f16-199">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="d2f16-199">Razor Page</span></span>                                   | [<span data-ttu-id="d2f16-200">Página</span><span class="sxs-lookup"><span data-stu-id="d2f16-200">page</span></span>](#page)                   | <span data-ttu-id="d2f16-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-201">[C#]</span></span>         | <span data-ttu-id="d2f16-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2f16-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f16-203">2,0</span><span class="sxs-lookup"><span data-stu-id="d2f16-203">2.0</span></span>        |
| <span data-ttu-id="d2f16-204">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="d2f16-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="d2f16-205">verimportações</span><span class="sxs-lookup"><span data-stu-id="d2f16-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="d2f16-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-206">[C#]</span></span>         | <span data-ttu-id="d2f16-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2f16-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f16-208">2,0</span><span class="sxs-lookup"><span data-stu-id="d2f16-208">2.0</span></span>        |
| <span data-ttu-id="d2f16-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="d2f16-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="d2f16-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-210">[C#]</span></span>         | <span data-ttu-id="d2f16-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d2f16-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="d2f16-212">2,0</span><span class="sxs-lookup"><span data-stu-id="d2f16-212">2.0</span></span>        |
| <span data-ttu-id="d2f16-213">Aplicativo Blazor Server</span><span class="sxs-lookup"><span data-stu-id="d2f16-213">Blazor Server App</span></span>                            | [<span data-ttu-id="d2f16-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d2f16-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="d2f16-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-215">[C#]</span></span>         | <span data-ttu-id="d2f16-216">Web/Blazor</span><span class="sxs-lookup"><span data-stu-id="d2f16-216">Web/Blazor</span></span>                            | <span data-ttu-id="d2f16-217">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-217">3.0</span></span>        |
| <span data-ttu-id="d2f16-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="d2f16-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="d2f16-219">Web</span><span class="sxs-lookup"><span data-stu-id="d2f16-219">web</span></span>](#web)                     | <span data-ttu-id="d2f16-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d2f16-220">[C#], F#</span></span>     | <span data-ttu-id="d2f16-221">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="d2f16-221">Web/Empty</span></span>                             | <span data-ttu-id="d2f16-222">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-222">1.0</span></span>        |
| <span data-ttu-id="d2f16-223">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="d2f16-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="d2f16-224">Mvc</span><span class="sxs-lookup"><span data-stu-id="d2f16-224">mvc</span></span>](#web-options)             | <span data-ttu-id="d2f16-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d2f16-225">[C#], F#</span></span>     | <span data-ttu-id="d2f16-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="d2f16-226">Web/MVC</span></span>                               | <span data-ttu-id="d2f16-227">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-227">1.0</span></span>        |
| <span data-ttu-id="d2f16-228">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2f16-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="d2f16-229">webapp, navalha</span><span class="sxs-lookup"><span data-stu-id="d2f16-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="d2f16-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-230">[C#]</span></span>         | <span data-ttu-id="d2f16-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="d2f16-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="d2f16-232">2.2, 2.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="d2f16-233">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="d2f16-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="d2f16-234">angular</span><span class="sxs-lookup"><span data-stu-id="d2f16-234">angular</span></span>](#spa)                 | <span data-ttu-id="d2f16-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-235">[C#]</span></span>         | <span data-ttu-id="d2f16-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2f16-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2f16-237">2,0</span><span class="sxs-lookup"><span data-stu-id="d2f16-237">2.0</span></span>        |
| <span data-ttu-id="d2f16-238">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="d2f16-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="d2f16-239">Reagir</span><span class="sxs-lookup"><span data-stu-id="d2f16-239">react</span></span>](#spa)                   | <span data-ttu-id="d2f16-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-240">[C#]</span></span>         | <span data-ttu-id="d2f16-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2f16-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2f16-242">2,0</span><span class="sxs-lookup"><span data-stu-id="d2f16-242">2.0</span></span>        |
| <span data-ttu-id="d2f16-243">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="d2f16-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="d2f16-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="d2f16-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="d2f16-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-245">[C#]</span></span>         | <span data-ttu-id="d2f16-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="d2f16-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="d2f16-247">2,0</span><span class="sxs-lookup"><span data-stu-id="d2f16-247">2.0</span></span>        |
| <span data-ttu-id="d2f16-248">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="d2f16-248">Razor Class Library</span></span>                          | [<span data-ttu-id="d2f16-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d2f16-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="d2f16-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-250">[C#]</span></span>         | <span data-ttu-id="d2f16-251">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="d2f16-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="d2f16-252">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-252">2.1</span></span>        |
| <span data-ttu-id="d2f16-253">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d2f16-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="d2f16-254">webapi</span><span class="sxs-lookup"><span data-stu-id="d2f16-254">webapi</span></span>](#webapi)               | <span data-ttu-id="d2f16-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="d2f16-255">[C#], F#</span></span>     | <span data-ttu-id="d2f16-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="d2f16-256">Web/WebAPI</span></span>                            | <span data-ttu-id="d2f16-257">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-257">1.0</span></span>        |
| <span data-ttu-id="d2f16-258">ASP.NET Core gRPC Service</span><span class="sxs-lookup"><span data-stu-id="d2f16-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="d2f16-259">grpc</span><span class="sxs-lookup"><span data-stu-id="d2f16-259">grpc</span></span>](#web-others)             | <span data-ttu-id="d2f16-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="d2f16-260">[C#]</span></span>         | <span data-ttu-id="d2f16-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d2f16-261">Web/gRPC</span></span>                              | <span data-ttu-id="d2f16-262">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-262">3.0</span></span>        |
| <span data-ttu-id="d2f16-263">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="d2f16-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="d2f16-264">Proto</span><span class="sxs-lookup"><span data-stu-id="d2f16-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="d2f16-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="d2f16-265">Web/gRPC</span></span>                              | <span data-ttu-id="d2f16-266">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-266">3.0</span></span>        |
| <span data-ttu-id="d2f16-267">dotnet arquivo gitignore</span><span class="sxs-lookup"><span data-stu-id="d2f16-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="d2f16-268">Config</span><span class="sxs-lookup"><span data-stu-id="d2f16-268">Config</span></span>                                | <span data-ttu-id="d2f16-269">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-269">3.0</span></span>        |
| <span data-ttu-id="d2f16-270">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="d2f16-270">global.json file</span></span>                             | [<span data-ttu-id="d2f16-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="d2f16-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="d2f16-272">Config</span><span class="sxs-lookup"><span data-stu-id="d2f16-272">Config</span></span>                                | <span data-ttu-id="d2f16-273">2,0</span><span class="sxs-lookup"><span data-stu-id="d2f16-273">2.0</span></span>        |
| <span data-ttu-id="d2f16-274">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="d2f16-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="d2f16-275">Config</span><span class="sxs-lookup"><span data-stu-id="d2f16-275">Config</span></span>                                | <span data-ttu-id="d2f16-276">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-276">1.0</span></span>        |
| <span data-ttu-id="d2f16-277">dotnet arquivo manifesto ferramenta local</span><span class="sxs-lookup"><span data-stu-id="d2f16-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="d2f16-278">Config</span><span class="sxs-lookup"><span data-stu-id="d2f16-278">Config</span></span>                                | <span data-ttu-id="d2f16-279">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-279">3.0</span></span>        |
| <span data-ttu-id="d2f16-280">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="d2f16-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="d2f16-281">Config</span><span class="sxs-lookup"><span data-stu-id="d2f16-281">Config</span></span>                                | <span data-ttu-id="d2f16-282">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-282">1.0</span></span>        |
| <span data-ttu-id="d2f16-283">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="d2f16-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="d2f16-284">Solução</span><span class="sxs-lookup"><span data-stu-id="d2f16-284">Solution</span></span>                              | <span data-ttu-id="d2f16-285">1.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="d2f16-286">Opções</span><span class="sxs-lookup"><span data-stu-id="d2f16-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="d2f16-287">Exibe um resumo do que aconteceria se o comando dado fosse executado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="d2f16-288">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="d2f16-289">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="d2f16-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="d2f16-290">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="d2f16-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d2f16-291">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="d2f16-291">Prints out help for the command.</span></span> <span data-ttu-id="d2f16-292">Ele pode ser invocado para o `dotnet new` comando em si ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="d2f16-293">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="d2f16-294">Instala um pacote de `PATH` `NUGET_ID` modelo si mesmo ou fornecido.</span><span class="sxs-lookup"><span data-stu-id="d2f16-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d2f16-295">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="d2f16-296">Por `dotnet new` padrão, \* passa para a versão, que representa a versão mais recente do pacote estável.</span><span class="sxs-lookup"><span data-stu-id="d2f16-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="d2f16-297">Veja um exemplo na seção [Exemplos.](#examples)</span><span class="sxs-lookup"><span data-stu-id="d2f16-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="d2f16-298">Se uma versão do modelo já estiver instalada quando você executar este comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão foi especificada.</span><span class="sxs-lookup"><span data-stu-id="d2f16-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="d2f16-299">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="d2f16-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="d2f16-300">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="d2f16-301">Se nenhum nome for especificado, lista todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="d2f16-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="d2f16-302">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="d2f16-302">The language of the template to create.</span></span> <span data-ttu-id="d2f16-303">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="d2f16-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="d2f16-304">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="d2f16-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d2f16-305">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="d2f16-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="d2f16-306">Nesses casos, inclui o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="d2f16-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="d2f16-307">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="d2f16-308">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="d2f16-308">The name for the created output.</span></span> <span data-ttu-id="d2f16-309">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source <SOURCE>`**

  <span data-ttu-id="d2f16-310">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="d2f16-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="d2f16-311">Disponível desde .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d2f16-312">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="d2f16-312">Location to place the generated output.</span></span> <span data-ttu-id="d2f16-313">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d2f16-313">The default is the current directory.</span></span>

- **`--type <TYPE>`**

  <span data-ttu-id="d2f16-314">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d2f16-314">Filters templates based on available types.</span></span> <span data-ttu-id="d2f16-315">Os valores `project` `item`predefinidos são, ou `other`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-315">Predefined values are `project`, `item`, or `other`.</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="d2f16-316">Desinstala um pacote `PATH` de `NUGET_ID` modelo no ou fornecido.</span><span class="sxs-lookup"><span data-stu-id="d2f16-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="d2f16-317">Quando `<PATH|NUGET_ID>` o valor não é especificado, todos os pacotes de modelos instalados no momento e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="d2f16-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="d2f16-318">Ao `NUGET_ID`especificar, não inclua o número da versão.</span><span class="sxs-lookup"><span data-stu-id="d2f16-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="d2f16-319">Se você não especificar um parâmetro para essa opção, o comando listaos os modelos e detalhes instalados sobre eles.</span><span class="sxs-lookup"><span data-stu-id="d2f16-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d2f16-320">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="d2f16-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="d2f16-321">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="d2f16-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="d2f16-322">Não inclua uma barra final de diretório de terminação no seu caminho de modelo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="d2f16-323">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="d2f16-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="d2f16-324">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2f16-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="d2f16-325">Verifique se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="d2f16-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="d2f16-326">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2f16-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="d2f16-327">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="d2f16-327">Template options</span></span>

<span data-ttu-id="d2f16-328">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d2f16-328">Each project template may have additional options available.</span></span> <span data-ttu-id="d2f16-329">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="d2f16-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="d2f16-330">console</span><span class="sxs-lookup"><span data-stu-id="d2f16-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-331">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-332">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2f16-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2f16-333">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-334">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-334">SDK version</span></span> | <span data-ttu-id="d2f16-335">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-336">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-337">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f16-338">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f16-339">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2f16-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d2f16-340">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="d2f16-340">Not supported for F#.</span></span> <span data-ttu-id="d2f16-341">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f16-342">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2f16-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-343">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="d2f16-344">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="d2f16-345">classlib</span><span class="sxs-lookup"><span data-stu-id="d2f16-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-346">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-347">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d2f16-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="d2f16-348">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f16-349">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f16-350">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2f16-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="d2f16-351">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="d2f16-351">Not supported for F#.</span></span> <span data-ttu-id="d2f16-352">Disponível desde .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f16-353">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2f16-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-354">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a><span data-ttu-id="d2f16-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="d2f16-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-356">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-357">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d2f16-358">Disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-358">Available since .NET Core 3.1 SDK.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f16-359">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f16-360">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2f16-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d2f16-361">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2f16-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-362">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms-winformslib"></a><a name="winforms"></a><span data-ttu-id="d2f16-363">winforms, winformslib</span><span class="sxs-lookup"><span data-stu-id="d2f16-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="d2f16-364">Define `LangVersion` a propriedade no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="d2f16-365">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="d2f16-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="d2f16-366">Para obter uma lista de [versões](../../csharp/language-reference/configure-language-version.md#defaults)C# padrão, consulte Padrões .</span><span class="sxs-lookup"><span data-stu-id="d2f16-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-367">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="worker-grpc"></a><a name="web-others"></a><span data-ttu-id="d2f16-368">trabalhador, grpc</span><span class="sxs-lookup"><span data-stu-id="d2f16-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-369">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-370">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="d2f16-371">Disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-371">Available since .NET Core 3.1 SDK.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f16-372">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-373">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="mstest-xunit"></a><a name="test"></a><span data-ttu-id="d2f16-374">mstest, xunit</span><span class="sxs-lookup"><span data-stu-id="d2f16-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-375">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-376">Opção disponível desde .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2f16-377">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-378">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-378">SDK version</span></span> | <span data-ttu-id="d2f16-379">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-380">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-381">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d2f16-382">Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d2f16-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-383">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="d2f16-384">Nunit</span><span class="sxs-lookup"><span data-stu-id="d2f16-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-385">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="d2f16-386">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-387">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-387">SDK version</span></span> | <span data-ttu-id="d2f16-388">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-389">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-390">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f16-391">2.2</span><span class="sxs-lookup"><span data-stu-id="d2f16-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="d2f16-392">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="d2f16-393">Permite a embalagem para o projeto usando [o pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="d2f16-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-394">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="d2f16-395">página</span><span class="sxs-lookup"><span data-stu-id="d2f16-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d2f16-396">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-396">Namespace for the generated code.</span></span> <span data-ttu-id="d2f16-397">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="d2f16-398">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="d2f16-398">Creates the page without a PageModel.</span></span>

***

### <a name="viewimports-proto"></a><a name="namespace"></a><span data-ttu-id="d2f16-399">verimportações, proto</span><span class="sxs-lookup"><span data-stu-id="d2f16-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="d2f16-400">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-400">Namespace for the generated code.</span></span> <span data-ttu-id="d2f16-401">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="d2f16-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="d2f16-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f16-403">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-403">The type of authentication to use.</span></span> <span data-ttu-id="d2f16-404">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2f16-404">The possible values are:</span></span>

  - <span data-ttu-id="d2f16-405">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2f16-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f16-406">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d2f16-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d2f16-407">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d2f16-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2f16-408">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d2f16-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2f16-409">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="d2f16-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d2f16-410">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d2f16-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2f16-411">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2f16-412">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-413">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2f16-414">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2f16-415">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d2f16-416">O iD da política de senha redefinida para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="d2f16-417">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d2f16-418">O ID de política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d2f16-419">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2f16-420">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2f16-421">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f16-422">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2f16-423">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-423">The Client ID for this project.</span></span> <span data-ttu-id="d2f16-424">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f16-425">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2f16-426">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="d2f16-426">The domain for the directory tenant.</span></span> <span data-ttu-id="d2f16-427">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-428">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2f16-429">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2f16-430">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f16-431">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d2f16-432">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d2f16-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d2f16-433">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-434">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2f16-435">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d2f16-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2f16-436">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f16-437">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f16-438">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2f16-438">Turns off HTTPS.</span></span> <span data-ttu-id="d2f16-439">Esta opção só `Individual`se `IndividualB2C` `SingleOrg`aplica `MultiOrg` se , , `--auth`ou não estiver sendo usado para .</span><span class="sxs-lookup"><span data-stu-id="d2f16-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f16-440">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2f16-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f16-441">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-442">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="d2f16-443">web</span><span class="sxs-lookup"><span data-stu-id="d2f16-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f16-444">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-445">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-446">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f16-447">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-448">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-448">SDK version</span></span> | <span data-ttu-id="d2f16-449">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-450">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-451">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f16-452">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d2f16-453">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f16-454">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2f16-454">Turns off HTTPS.</span></span>

***

### <a name="mvc-webapp"></a><a name="web-options"></a><span data-ttu-id="d2f16-455">mvc, webapp</span><span class="sxs-lookup"><span data-stu-id="d2f16-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f16-456">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-456">The type of authentication to use.</span></span> <span data-ttu-id="d2f16-457">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2f16-457">The possible values are:</span></span>

  - <span data-ttu-id="d2f16-458">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2f16-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f16-459">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d2f16-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="d2f16-460">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d2f16-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2f16-461">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d2f16-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2f16-462">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="d2f16-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="d2f16-463">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d2f16-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2f16-464">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2f16-465">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-466">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2f16-467">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2f16-468">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="d2f16-469">O iD da política de senha redefinida para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="d2f16-470">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="d2f16-471">O ID de política de perfil de edição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="d2f16-472">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2f16-473">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2f16-474">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f16-475">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2f16-476">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-476">The Client ID for this project.</span></span> <span data-ttu-id="d2f16-477">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="d2f16-478">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2f16-479">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="d2f16-479">The domain for the directory tenant.</span></span> <span data-ttu-id="d2f16-480">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-481">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2f16-482">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2f16-483">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f16-484">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="d2f16-485">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="d2f16-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="d2f16-486">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-487">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2f16-488">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d2f16-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2f16-489">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f16-490">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f16-491">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2f16-491">Turns off HTTPS.</span></span> <span data-ttu-id="d2f16-492">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="d2f16-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f16-493">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2f16-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f16-494">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-495">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-496">Opção disponível desde .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="d2f16-497">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-498">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-498">SDK version</span></span> | <span data-ttu-id="d2f16-499">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-500">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-501">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="d2f16-502">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="d2f16-503">Inclui o BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="d2f16-504">Opção não disponível em .NET Core 2.2 e 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

- **`-rrc|--razor-runtime-compilation`**

  <span data-ttu-id="d2f16-505">Determina se o projeto está configurado para usar a [compilação Razor runtime](/aspnet/core/mvc/views/view-compilation#runtime-compilation) em compilações Debug.</span><span class="sxs-lookup"><span data-stu-id="d2f16-505">Determines if the project is configured to use [Razor runtime compilation](/aspnet/core/mvc/views/view-compilation#runtime-compilation) in Debug builds.</span></span> <span data-ttu-id="d2f16-506">Opção disponível desde .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-506">Option available since .NET Core 3.1 SDK.</span></span>

***

### <a name="angular-react"></a><a name="spa"></a><span data-ttu-id="d2f16-507">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="d2f16-507">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f16-508">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-508">The type of authentication to use.</span></span> <span data-ttu-id="d2f16-509">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2f16-509">Available since .NET Core 3.0 SDK.</span></span>
  
  <span data-ttu-id="d2f16-510">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2f16-510">The possible values are:</span></span>

  - <span data-ttu-id="d2f16-511">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2f16-511">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f16-512">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="d2f16-512">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f16-513">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-513">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-514">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-514">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f16-515">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2f16-515">Turns off HTTPS.</span></span> <span data-ttu-id="d2f16-516">Essa opção só se aplica `None`se a autenticação for .</span><span class="sxs-lookup"><span data-stu-id="d2f16-516">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f16-517">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2f16-517">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f16-518">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-518">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-519">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2f16-519">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-520">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-520">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-521">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-521">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f16-522">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-522">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-523">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-523">SDK version</span></span> | <span data-ttu-id="d2f16-524">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-524">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-525">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-525">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-526">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-526">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f16-527">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-527">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="d2f16-528">reactredux</span><span class="sxs-lookup"><span data-stu-id="d2f16-528">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f16-529">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-529">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-530">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-530">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-531">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-531">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f16-532">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-532">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-533">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-533">SDK version</span></span> | <span data-ttu-id="d2f16-534">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-534">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-535">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-535">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-536">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-536">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f16-537">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-537">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="d2f16-538">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-538">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f16-539">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2f16-539">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="d2f16-540">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="d2f16-540">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="d2f16-541">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-541">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="d2f16-542">Suporta a adição de páginas e visualizações tradicionais de navalha, além de componentes para esta biblioteca.</span><span class="sxs-lookup"><span data-stu-id="d2f16-542">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="d2f16-543">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d2f16-543">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="d2f16-544">webapi</span><span class="sxs-lookup"><span data-stu-id="d2f16-544">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="d2f16-545">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-545">The type of authentication to use.</span></span> <span data-ttu-id="d2f16-546">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="d2f16-546">The possible values are:</span></span>

  - <span data-ttu-id="d2f16-547">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="d2f16-547">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="d2f16-548">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="d2f16-548">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="d2f16-549">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="d2f16-549">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="d2f16-550">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="d2f16-550">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="d2f16-551">A ocorrência B2C do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-551">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="d2f16-552">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-552">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="d2f16-553">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-553">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="d2f16-554">O id da política de inscrição e login para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-554">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="d2f16-555">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-555">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="d2f16-556">A instância do Diretório Ativo do Azure para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-556">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="d2f16-557">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-557">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f16-558">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-558">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="d2f16-559">O ID do Cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-559">The Client ID for this project.</span></span> <span data-ttu-id="d2f16-560">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-560">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f16-561">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-561">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="d2f16-562">O domínio para o inquilino do diretório.</span><span class="sxs-lookup"><span data-stu-id="d2f16-562">The domain for the directory tenant.</span></span> <span data-ttu-id="d2f16-563">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-563">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f16-564">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-564">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="d2f16-565">O ID TenantId do diretório para se conectar.</span><span class="sxs-lookup"><span data-stu-id="d2f16-565">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="d2f16-566">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-566">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="d2f16-567">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-567">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="d2f16-568">Permite que este aplicativo leia acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="d2f16-568">Allows this application read-access to the directory.</span></span> <span data-ttu-id="d2f16-569">Só se `SingleOrg` aplica à autenticação.</span><span class="sxs-lookup"><span data-stu-id="d2f16-569">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="d2f16-570">Exclui *o lançamentoSettings.json* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="d2f16-570">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="d2f16-571">Desativa https.</span><span class="sxs-lookup"><span data-stu-id="d2f16-571">Turns off HTTPS.</span></span> <span data-ttu-id="d2f16-572">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="d2f16-572">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="d2f16-573">Essa opção só `IndividualB2C` se `SingleOrg` aplica se ou não estiver sendo usada para autenticação.</span><span class="sxs-lookup"><span data-stu-id="d2f16-573">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="d2f16-574">Especifica o LocalDB deve ser usado em vez de SQLite.</span><span class="sxs-lookup"><span data-stu-id="d2f16-574">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="d2f16-575">Só se `IndividualB2C` aplica à autenticação.</span><span class="sxs-lookup"><span data-stu-id="d2f16-575">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="d2f16-576">Especifica a [estrutura](../../standard/frameworks.md) para o alvo.</span><span class="sxs-lookup"><span data-stu-id="d2f16-576">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="d2f16-577">Opção não disponível no .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="d2f16-577">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="d2f16-578">A tabela a seguir lista os valores padrão de acordo com o número da versão sdk que você está usando:</span><span class="sxs-lookup"><span data-stu-id="d2f16-578">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="d2f16-579">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="d2f16-579">SDK version</span></span> | <span data-ttu-id="d2f16-580">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="d2f16-580">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="d2f16-581">3.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-581">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="d2f16-582">3.0</span><span class="sxs-lookup"><span data-stu-id="d2f16-582">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="d2f16-583">2.1</span><span class="sxs-lookup"><span data-stu-id="d2f16-583">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="d2f16-584">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="d2f16-584">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="d2f16-585">globaljson</span><span class="sxs-lookup"><span data-stu-id="d2f16-585">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="d2f16-586">Especifica a versão do .NET Core SDK para usar no arquivo *global.json.*</span><span class="sxs-lookup"><span data-stu-id="d2f16-586">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="d2f16-587">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d2f16-587">Examples</span></span>

- <span data-ttu-id="d2f16-588">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="d2f16-588">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="d2f16-589">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d2f16-589">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="d2f16-590">Criar um projeto de biblioteca de classe .NET padrão no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="d2f16-590">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="d2f16-591">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="d2f16-591">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="d2f16-592">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="d2f16-592">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="d2f16-593">Liste todos os modelos disponíveis para os modelos spa (Single Page Application, aplicativo de página única):</span><span class="sxs-lookup"><span data-stu-id="d2f16-593">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="d2f16-594">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="d2f16-594">List all templates matching the *we* substring.</span></span> <span data-ttu-id="d2f16-595">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="d2f16-595">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="d2f16-596">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="d2f16-596">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="d2f16-597">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="d2f16-597">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="d2f16-598">Instale a versão 2.0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="d2f16-598">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="d2f16-599">Liste os modelos e detalhes instalados sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="d2f16-599">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="d2f16-600">Crie um *global.json* no diretório atual definindo a versão SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="d2f16-600">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="d2f16-601">Confira também</span><span class="sxs-lookup"><span data-stu-id="d2f16-601">See also</span></span>

- [<span data-ttu-id="d2f16-602">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2f16-602">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="d2f16-603">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="d2f16-603">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="d2f16-604">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="d2f16-604">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="d2f16-605">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="d2f16-605">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
