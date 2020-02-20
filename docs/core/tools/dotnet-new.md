---
title: Comando dotnet new
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
ms.date: 02/13/2020
ms.openlocfilehash: f11512acf5a1fdc4bde49b3d1212ccf6335dff8b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451324"
---
# <a name="dotnet-new"></a><span data-ttu-id="c0801-103">dotnet new</span><span class="sxs-lookup"><span data-stu-id="c0801-103">dotnet new</span></span>

<span data-ttu-id="c0801-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c0801-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c0801-105">Nome</span><span class="sxs-lookup"><span data-stu-id="c0801-105">Name</span></span>

<span data-ttu-id="c0801-106">`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="c0801-106">`dotnet new` - Creates a new project, configuration file, or solution based on the specified template.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c0801-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c0801-107">Synopsis</span></span>

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] 
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c0801-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c0801-108">Description</span></span>

<span data-ttu-id="c0801-109">O comando `dotnet new` cria um projeto .NET Core ou outros artefatos com base em um modelo.</span><span class="sxs-lookup"><span data-stu-id="c0801-109">The `dotnet new` command creates a .NET Core project or other artifacts based on a template.</span></span>

<span data-ttu-id="c0801-110">O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.</span><span class="sxs-lookup"><span data-stu-id="c0801-110">The command calls the [template engine](https://github.com/dotnet/templating) to create the artifacts on disk based on the specified template and options.</span></span>

## <a name="arguments"></a><span data-ttu-id="c0801-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c0801-111">Arguments</span></span>

- **`TEMPLATE`**

  <span data-ttu-id="c0801-112">O modelo para o qual criar uma instância quando o comando é invocado.</span><span class="sxs-lookup"><span data-stu-id="c0801-112">The template to instantiate when the command is invoked.</span></span> <span data-ttu-id="c0801-113">Cada modelo pode ter opções específicas que podem ser passadas.</span><span class="sxs-lookup"><span data-stu-id="c0801-113">Each template might have specific options you can pass.</span></span> <span data-ttu-id="c0801-114">Para obter mais informações, consulte [Opções de modelo](#template-options).</span><span class="sxs-lookup"><span data-stu-id="c0801-114">For more information, see [Template options](#template-options).</span></span>

  <span data-ttu-id="c0801-115">Você pode executar `dotnet new --list` para ver uma lista de todos os modelos instalados.</span><span class="sxs-lookup"><span data-stu-id="c0801-115">You can run `dotnet new --list` to see a list of all installed templates.</span></span> <span data-ttu-id="c0801-116">Se o valor de `TEMPLATE` não for uma correspondência exata no texto na coluna **modelos** ou **nome curto** da tabela retornada, uma correspondência de subcadeia de caracteres será executada nessas duas colunas.</span><span class="sxs-lookup"><span data-stu-id="c0801-116">If the `TEMPLATE` value isn't an exact match on text in the **Templates** or **Short Name** column from the returned table, a substring match is performed on those two columns.</span></span>

  <span data-ttu-id="c0801-117">A partir do SDK do .NET Core 3,0, a CLI procura modelos em NuGet.org quando você invoca o comando `dotnet new` nas seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="c0801-117">Starting with .NET Core 3.0 SDK, the CLI searches for templates in NuGet.org when you invoke the `dotnet new` command in the following conditions:</span></span>

  - <span data-ttu-id="c0801-118">Se a CLI não encontrar uma correspondência de modelo ao invocar `dotnet new`, nem mesmo parcial.</span><span class="sxs-lookup"><span data-stu-id="c0801-118">If the CLI can’t find a template match when invoking `dotnet new`, not even partial.</span></span>
  - <span data-ttu-id="c0801-119">Se houver uma versão mais recente do modelo disponível.</span><span class="sxs-lookup"><span data-stu-id="c0801-119">If there’s a newer version of the template available.</span></span> <span data-ttu-id="c0801-120">Nesse caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.</span><span class="sxs-lookup"><span data-stu-id="c0801-120">In this case, the project or artifact is created but the CLI warns you about an updated version of the template.</span></span>

  <span data-ttu-id="c0801-121">O comando contém uma lista padrão de modelos.</span><span class="sxs-lookup"><span data-stu-id="c0801-121">The command contains a default list of templates.</span></span> <span data-ttu-id="c0801-122">Use `dotnet new -l` para obter uma lista dos modelos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c0801-122">Use `dotnet new -l` to obtain a list of the available templates.</span></span> <span data-ttu-id="c0801-123">A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0801-123">The following table shows the templates that come pre-installed with the .NET Core SDK.</span></span> <span data-ttu-id="c0801-124">O idioma padrão do modelo é mostrado entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c0801-124">The default language for the template is shown inside the brackets.</span></span> <span data-ttu-id="c0801-125">Clique no link nome curto para ver as opções de modelo específicas.</span><span class="sxs-lookup"><span data-stu-id="c0801-125">Click on the short name link to see the specific template options.</span></span>

| <span data-ttu-id="c0801-126">Modelos</span><span class="sxs-lookup"><span data-stu-id="c0801-126">Templates</span></span>                                    | <span data-ttu-id="c0801-127">Nome curto</span><span class="sxs-lookup"><span data-stu-id="c0801-127">Short name</span></span>                      | <span data-ttu-id="c0801-128">Linguagem</span><span class="sxs-lookup"><span data-stu-id="c0801-128">Language</span></span>     | <span data-ttu-id="c0801-129">Marcas</span><span class="sxs-lookup"><span data-stu-id="c0801-129">Tags</span></span>                                  | <span data-ttu-id="c0801-130">Incluída</span><span class="sxs-lookup"><span data-stu-id="c0801-130">Introduced</span></span> |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| <span data-ttu-id="c0801-131">Aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="c0801-131">Console Application</span></span>                          | [<span data-ttu-id="c0801-132">console</span><span class="sxs-lookup"><span data-stu-id="c0801-132">console</span></span>](#console)             | <span data-ttu-id="c0801-133">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c0801-133">[C#], F#, VB</span></span> | <span data-ttu-id="c0801-134">Comum/Console</span><span class="sxs-lookup"><span data-stu-id="c0801-134">Common/Console</span></span>                        | <span data-ttu-id="c0801-135">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-135">1.0</span></span>        |
| <span data-ttu-id="c0801-136">Biblioteca de classes</span><span class="sxs-lookup"><span data-stu-id="c0801-136">Class library</span></span>                                | [<span data-ttu-id="c0801-137">classlib</span><span class="sxs-lookup"><span data-stu-id="c0801-137">classlib</span></span>](#classlib)           | <span data-ttu-id="c0801-138">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c0801-138">[C#], F#, VB</span></span> | <span data-ttu-id="c0801-139">Comum/Library</span><span class="sxs-lookup"><span data-stu-id="c0801-139">Common/Library</span></span>                        | <span data-ttu-id="c0801-140">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-140">1.0</span></span>        |
| <span data-ttu-id="c0801-141">Aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-141">WPF Application</span></span>                              | [<span data-ttu-id="c0801-142">WFP</span><span class="sxs-lookup"><span data-stu-id="c0801-142">wpf</span></span>](#wpf)                     | <span data-ttu-id="c0801-143">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-143">[C#]</span></span>         | <span data-ttu-id="c0801-144">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-144">Common/WPF</span></span>                            | <span data-ttu-id="c0801-145">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-145">3.0</span></span>        |
| <span data-ttu-id="c0801-146">Biblioteca de classes do WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-146">WPF Class library</span></span>                            | [<span data-ttu-id="c0801-147">wpflib</span><span class="sxs-lookup"><span data-stu-id="c0801-147">wpflib</span></span>](#wpf)                  | <span data-ttu-id="c0801-148">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-148">[C#]</span></span>         | <span data-ttu-id="c0801-149">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-149">Common/WPF</span></span>                            | <span data-ttu-id="c0801-150">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-150">3.0</span></span>        |
| <span data-ttu-id="c0801-151">Biblioteca de controle personalizado WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-151">WPF Custom Control Library</span></span>                   | [<span data-ttu-id="c0801-152">wpfcustomcontrollib</span><span class="sxs-lookup"><span data-stu-id="c0801-152">wpfcustomcontrollib</span></span>](#wpf)     | <span data-ttu-id="c0801-153">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-153">[C#]</span></span>         | <span data-ttu-id="c0801-154">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-154">Common/WPF</span></span>                            | <span data-ttu-id="c0801-155">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-155">3.0</span></span>        |
| <span data-ttu-id="c0801-156">Biblioteca de Controle de Usuário do WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-156">WPF User Control Library</span></span>                     | [<span data-ttu-id="c0801-157">wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c0801-157">wpfusercontrollib</span></span>](#wpf)       | <span data-ttu-id="c0801-158">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-158">[C#]</span></span>         | <span data-ttu-id="c0801-159">Comum/WPF</span><span class="sxs-lookup"><span data-stu-id="c0801-159">Common/WPF</span></span>                            | <span data-ttu-id="c0801-160">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-160">3.0</span></span>        |
| <span data-ttu-id="c0801-161">Aplicativo Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c0801-161">Windows Forms (WinForms) Application</span></span>         | [<span data-ttu-id="c0801-162">WinForms</span><span class="sxs-lookup"><span data-stu-id="c0801-162">winforms</span></span>](#winforms)           | <span data-ttu-id="c0801-163">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-163">[C#]</span></span>         | <span data-ttu-id="c0801-164">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="c0801-164">Common/WinForms</span></span>                       | <span data-ttu-id="c0801-165">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-165">3.0</span></span>        |
| <span data-ttu-id="c0801-166">Biblioteca de classes do Windows Forms (WinForms)</span><span class="sxs-lookup"><span data-stu-id="c0801-166">Windows Forms (WinForms) Class library</span></span>       | [<span data-ttu-id="c0801-167">winformslib</span><span class="sxs-lookup"><span data-stu-id="c0801-167">winformslib</span></span>](#winforms)        | <span data-ttu-id="c0801-168">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-168">[C#]</span></span>         | <span data-ttu-id="c0801-169">Comum/WinForms</span><span class="sxs-lookup"><span data-stu-id="c0801-169">Common/WinForms</span></span>                       | <span data-ttu-id="c0801-170">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-170">3.0</span></span>        |
| <span data-ttu-id="c0801-171">Serviço de trabalho</span><span class="sxs-lookup"><span data-stu-id="c0801-171">Worker Service</span></span>                               | [<span data-ttu-id="c0801-172">funcionários</span><span class="sxs-lookup"><span data-stu-id="c0801-172">worker</span></span>](#web-others)           | <span data-ttu-id="c0801-173">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-173">[C#]</span></span>         | <span data-ttu-id="c0801-174">Comum/de trabalho/Web</span><span class="sxs-lookup"><span data-stu-id="c0801-174">Common/Worker/Web</span></span>                     | <span data-ttu-id="c0801-175">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-175">3.0</span></span>        |
| <span data-ttu-id="c0801-176">Projeto de Teste de Unidade</span><span class="sxs-lookup"><span data-stu-id="c0801-176">Unit Test Project</span></span>                            | [<span data-ttu-id="c0801-177">MSTest</span><span class="sxs-lookup"><span data-stu-id="c0801-177">mstest</span></span>](#test)                 | <span data-ttu-id="c0801-178">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c0801-178">[C#], F#, VB</span></span> | <span data-ttu-id="c0801-179">Teste/MSTest</span><span class="sxs-lookup"><span data-stu-id="c0801-179">Test/MSTest</span></span>                           | <span data-ttu-id="c0801-180">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-180">1.0</span></span>        |
| <span data-ttu-id="c0801-181">Projeto de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c0801-181">NUnit 3 Test Project</span></span>                         | [<span data-ttu-id="c0801-182">nunit</span><span class="sxs-lookup"><span data-stu-id="c0801-182">nunit</span></span>](#nunit)                  | <span data-ttu-id="c0801-183">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c0801-183">[C#], F#, VB</span></span> | <span data-ttu-id="c0801-184">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="c0801-184">Test/NUnit</span></span>                            | <span data-ttu-id="c0801-185">2.1.400</span><span class="sxs-lookup"><span data-stu-id="c0801-185">2.1.400</span></span>    |
| <span data-ttu-id="c0801-186">Item de Teste do NUnit 3</span><span class="sxs-lookup"><span data-stu-id="c0801-186">NUnit 3 Test Item</span></span>                            | `nunit-test`                    | <span data-ttu-id="c0801-187">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c0801-187">[C#], F#, VB</span></span> | <span data-ttu-id="c0801-188">Teste/NUnit</span><span class="sxs-lookup"><span data-stu-id="c0801-188">Test/NUnit</span></span>                            | <span data-ttu-id="c0801-189">2.2</span><span class="sxs-lookup"><span data-stu-id="c0801-189">2.2</span></span>        |
| <span data-ttu-id="c0801-190">Projeto de Teste xUnit</span><span class="sxs-lookup"><span data-stu-id="c0801-190">xUnit Test Project</span></span>                           | [<span data-ttu-id="c0801-191">xUnit</span><span class="sxs-lookup"><span data-stu-id="c0801-191">xunit</span></span>](#test)                  | <span data-ttu-id="c0801-192">[C#], F#, VB</span><span class="sxs-lookup"><span data-stu-id="c0801-192">[C#], F#, VB</span></span> | <span data-ttu-id="c0801-193">Teste/xUnit</span><span class="sxs-lookup"><span data-stu-id="c0801-193">Test/xUnit</span></span>                            | <span data-ttu-id="c0801-194">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-194">1.0</span></span>        |
| <span data-ttu-id="c0801-195">Componente Razor</span><span class="sxs-lookup"><span data-stu-id="c0801-195">Razor Component</span></span>                              | `razorcomponent`                | <span data-ttu-id="c0801-196">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-196">[C#]</span></span>         | <span data-ttu-id="c0801-197">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c0801-197">Web/ASP.NET</span></span>                           | <span data-ttu-id="c0801-198">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-198">3.0</span></span>        |
| <span data-ttu-id="c0801-199">Página do Razor</span><span class="sxs-lookup"><span data-stu-id="c0801-199">Razor Page</span></span>                                   | [<span data-ttu-id="c0801-200">page</span><span class="sxs-lookup"><span data-stu-id="c0801-200">page</span></span>](#page)                   | <span data-ttu-id="c0801-201">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-201">[C#]</span></span>         | <span data-ttu-id="c0801-202">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c0801-202">Web/ASP.NET</span></span>                           | <span data-ttu-id="c0801-203">2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-203">2.0</span></span>        |
| <span data-ttu-id="c0801-204">Importações de Exibição do MVC</span><span class="sxs-lookup"><span data-stu-id="c0801-204">MVC ViewImports</span></span>                              | [<span data-ttu-id="c0801-205">viewimports</span><span class="sxs-lookup"><span data-stu-id="c0801-205">viewimports</span></span>](#namespace)       | <span data-ttu-id="c0801-206">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-206">[C#]</span></span>         | <span data-ttu-id="c0801-207">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c0801-207">Web/ASP.NET</span></span>                           | <span data-ttu-id="c0801-208">2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-208">2.0</span></span>        |
| <span data-ttu-id="c0801-209">MVC ViewStart</span><span class="sxs-lookup"><span data-stu-id="c0801-209">MVC ViewStart</span></span>                                | `viewstart`                     | <span data-ttu-id="c0801-210">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-210">[C#]</span></span>         | <span data-ttu-id="c0801-211">Web/ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c0801-211">Web/ASP.NET</span></span>                           | <span data-ttu-id="c0801-212">2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-212">2.0</span></span>        |
| <span data-ttu-id="c0801-213">Aplicativo de servidor mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="c0801-213">Blazor Server App</span></span>                            | [<span data-ttu-id="c0801-214">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c0801-214">blazorserver</span></span>](#blazorserver)   | <span data-ttu-id="c0801-215">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-215">[C#]</span></span>         | <span data-ttu-id="c0801-216">Web/mais e mais</span><span class="sxs-lookup"><span data-stu-id="c0801-216">Web/Blazor</span></span>                            | <span data-ttu-id="c0801-217">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-217">3.0</span></span>        |
| <span data-ttu-id="c0801-218">ASP.NET Core Vazio</span><span class="sxs-lookup"><span data-stu-id="c0801-218">ASP.NET Core Empty</span></span>                           | [<span data-ttu-id="c0801-219">web</span><span class="sxs-lookup"><span data-stu-id="c0801-219">web</span></span>](#web)                     | <span data-ttu-id="c0801-220">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c0801-220">[C#], F#</span></span>     | <span data-ttu-id="c0801-221">Web/Vazio</span><span class="sxs-lookup"><span data-stu-id="c0801-221">Web/Empty</span></span>                             | <span data-ttu-id="c0801-222">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-222">1.0</span></span>        |
| <span data-ttu-id="c0801-223">Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)</span><span class="sxs-lookup"><span data-stu-id="c0801-223">ASP.NET Core Web App (Model-View-Controller)</span></span> | [<span data-ttu-id="c0801-224">mvc</span><span class="sxs-lookup"><span data-stu-id="c0801-224">mvc</span></span>](#web-options)             | <span data-ttu-id="c0801-225">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c0801-225">[C#], F#</span></span>     | <span data-ttu-id="c0801-226">Web/MVC</span><span class="sxs-lookup"><span data-stu-id="c0801-226">Web/MVC</span></span>                               | <span data-ttu-id="c0801-227">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-227">1.0</span></span>        |
| <span data-ttu-id="c0801-228">Aplicativo Web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c0801-228">ASP.NET Core Web App</span></span>                         | [<span data-ttu-id="c0801-229">webapp, Razor</span><span class="sxs-lookup"><span data-stu-id="c0801-229">webapp, razor</span></span>](#web-options)   | <span data-ttu-id="c0801-230">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-230">[C#]</span></span>         | <span data-ttu-id="c0801-231">Web/MVC/Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c0801-231">Web/MVC/Razor Pages</span></span>                   | <span data-ttu-id="c0801-232">2,2, 2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-232">2.2, 2.0</span></span>   |
| <span data-ttu-id="c0801-233">ASP.NET Core com Angular</span><span class="sxs-lookup"><span data-stu-id="c0801-233">ASP.NET Core with Angular</span></span>                    | [<span data-ttu-id="c0801-234">angular</span><span class="sxs-lookup"><span data-stu-id="c0801-234">angular</span></span>](#spa)                 | <span data-ttu-id="c0801-235">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-235">[C#]</span></span>         | <span data-ttu-id="c0801-236">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c0801-236">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c0801-237">2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-237">2.0</span></span>        |
| <span data-ttu-id="c0801-238">ASP.NET Core com React.js</span><span class="sxs-lookup"><span data-stu-id="c0801-238">ASP.NET Core with React.js</span></span>                   | [<span data-ttu-id="c0801-239">reagir</span><span class="sxs-lookup"><span data-stu-id="c0801-239">react</span></span>](#spa)                   | <span data-ttu-id="c0801-240">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-240">[C#]</span></span>         | <span data-ttu-id="c0801-241">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c0801-241">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c0801-242">2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-242">2.0</span></span>        |
| <span data-ttu-id="c0801-243">ASP.NET Core com React.js e Redux</span><span class="sxs-lookup"><span data-stu-id="c0801-243">ASP.NET Core with React.js and Redux</span></span>         | [<span data-ttu-id="c0801-244">reactredux</span><span class="sxs-lookup"><span data-stu-id="c0801-244">reactredux</span></span>](#reactredux)       | <span data-ttu-id="c0801-245">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-245">[C#]</span></span>         | <span data-ttu-id="c0801-246">Web/MVC/SPA</span><span class="sxs-lookup"><span data-stu-id="c0801-246">Web/MVC/SPA</span></span>                           | <span data-ttu-id="c0801-247">2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-247">2.0</span></span>        |
| <span data-ttu-id="c0801-248">Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="c0801-248">Razor Class Library</span></span>                          | [<span data-ttu-id="c0801-249">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c0801-249">razorclasslib</span></span>](#razorclasslib) | <span data-ttu-id="c0801-250">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-250">[C#]</span></span>         | <span data-ttu-id="c0801-251">Web/Razor/Biblioteca/Biblioteca de Classes do Razor</span><span class="sxs-lookup"><span data-stu-id="c0801-251">Web/Razor/Library/Razor Class Library</span></span> | <span data-ttu-id="c0801-252">2.1</span><span class="sxs-lookup"><span data-stu-id="c0801-252">2.1</span></span>        |
| <span data-ttu-id="c0801-253">API Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c0801-253">ASP.NET Core Web API</span></span>                         | [<span data-ttu-id="c0801-254">webapi</span><span class="sxs-lookup"><span data-stu-id="c0801-254">webapi</span></span>](#webapi)               | <span data-ttu-id="c0801-255">[C#], F#</span><span class="sxs-lookup"><span data-stu-id="c0801-255">[C#], F#</span></span>     | <span data-ttu-id="c0801-256">Web/WebAPI</span><span class="sxs-lookup"><span data-stu-id="c0801-256">Web/WebAPI</span></span>                            | <span data-ttu-id="c0801-257">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-257">1.0</span></span>        |
| <span data-ttu-id="c0801-258">ASP.NET Core serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="c0801-258">ASP.NET Core gRPC Service</span></span>                    | [<span data-ttu-id="c0801-259">grpc</span><span class="sxs-lookup"><span data-stu-id="c0801-259">grpc</span></span>](#web-others)             | <span data-ttu-id="c0801-260">[C#]</span><span class="sxs-lookup"><span data-stu-id="c0801-260">[C#]</span></span>         | <span data-ttu-id="c0801-261">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c0801-261">Web/gRPC</span></span>                              | <span data-ttu-id="c0801-262">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-262">3.0</span></span>        |
| <span data-ttu-id="c0801-263">Arquivo de buffer de protocolo</span><span class="sxs-lookup"><span data-stu-id="c0801-263">Protocol Buffer File</span></span>                         | [<span data-ttu-id="c0801-264">proto</span><span class="sxs-lookup"><span data-stu-id="c0801-264">proto</span></span>](#namespace)             |              | <span data-ttu-id="c0801-265">Web/gRPC</span><span class="sxs-lookup"><span data-stu-id="c0801-265">Web/gRPC</span></span>                              | <span data-ttu-id="c0801-266">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-266">3.0</span></span>        |
| <span data-ttu-id="c0801-267">arquivo dotnet gitignore</span><span class="sxs-lookup"><span data-stu-id="c0801-267">dotnet gitignore file</span></span>                        | `gitignore`                     |              | <span data-ttu-id="c0801-268">Config</span><span class="sxs-lookup"><span data-stu-id="c0801-268">Config</span></span>                                | <span data-ttu-id="c0801-269">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-269">3.0</span></span>        |
| <span data-ttu-id="c0801-270">Arquivo global.json</span><span class="sxs-lookup"><span data-stu-id="c0801-270">global.json file</span></span>                             | [<span data-ttu-id="c0801-271">globaljson</span><span class="sxs-lookup"><span data-stu-id="c0801-271">globaljson</span></span>](#globaljson)       |              | <span data-ttu-id="c0801-272">Config</span><span class="sxs-lookup"><span data-stu-id="c0801-272">Config</span></span>                                | <span data-ttu-id="c0801-273">2,0</span><span class="sxs-lookup"><span data-stu-id="c0801-273">2.0</span></span>        |
| <span data-ttu-id="c0801-274">Configuração do NuGet</span><span class="sxs-lookup"><span data-stu-id="c0801-274">NuGet Config</span></span>                                 | `nugetconfig`                   |              | <span data-ttu-id="c0801-275">Config</span><span class="sxs-lookup"><span data-stu-id="c0801-275">Config</span></span>                                | <span data-ttu-id="c0801-276">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-276">1.0</span></span>        |
| <span data-ttu-id="c0801-277">arquivo de manifesto da ferramenta local dotnet</span><span class="sxs-lookup"><span data-stu-id="c0801-277">dotnet local tool manifest file</span></span>              | `tool-manifest`                 |              | <span data-ttu-id="c0801-278">Config</span><span class="sxs-lookup"><span data-stu-id="c0801-278">Config</span></span>                                | <span data-ttu-id="c0801-279">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-279">3.0</span></span>        |
| <span data-ttu-id="c0801-280">Configuração da Web</span><span class="sxs-lookup"><span data-stu-id="c0801-280">Web Config</span></span>                                   | `webconfig`                     |              | <span data-ttu-id="c0801-281">Config</span><span class="sxs-lookup"><span data-stu-id="c0801-281">Config</span></span>                                | <span data-ttu-id="c0801-282">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-282">1.0</span></span>        |
| <span data-ttu-id="c0801-283">Arquivo de Solução</span><span class="sxs-lookup"><span data-stu-id="c0801-283">Solution File</span></span>                                | `sln`                           |              | <span data-ttu-id="c0801-284">Solução</span><span class="sxs-lookup"><span data-stu-id="c0801-284">Solution</span></span>                              | <span data-ttu-id="c0801-285">1.0</span><span class="sxs-lookup"><span data-stu-id="c0801-285">1.0</span></span>        |

## <a name="options"></a><span data-ttu-id="c0801-286">Opções</span><span class="sxs-lookup"><span data-stu-id="c0801-286">Options</span></span>

- **`--dry-run`**

  <span data-ttu-id="c0801-287">Exibe um resumo do que aconteceria se o comando fornecido fosse executado.</span><span class="sxs-lookup"><span data-stu-id="c0801-287">Displays a summary of what would happen if the given command were run.</span></span> <span data-ttu-id="c0801-288">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-288">Available since .NET Core 2.2 SDK.</span></span>

- **`--force`**

  <span data-ttu-id="c0801-289">Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes.</span><span class="sxs-lookup"><span data-stu-id="c0801-289">Forces content to be generated even if it would change existing files.</span></span> <span data-ttu-id="c0801-290">Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="c0801-290">This is required when the template chosen would override existing files in the output directory.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c0801-291">Imprime uma ajuda para o comando.</span><span class="sxs-lookup"><span data-stu-id="c0801-291">Prints out help for the command.</span></span> <span data-ttu-id="c0801-292">Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo.</span><span class="sxs-lookup"><span data-stu-id="c0801-292">It can be invoked for the `dotnet new` command itself or for any template.</span></span> <span data-ttu-id="c0801-293">Por exemplo, `dotnet new mvc --help`.</span><span class="sxs-lookup"><span data-stu-id="c0801-293">For example, `dotnet new mvc --help`.</span></span>

- **`-i|--install <PATH|NUGET_ID>`**

  <span data-ttu-id="c0801-294">Instala um pacote de modelos do `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c0801-294">Installs a template pack from the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c0801-295">Se você deseja instalar uma versão de pré-lançamento de um pacote de modelo, é necessário especificar a versão no formato `<package-name>::<package-version>`.</span><span class="sxs-lookup"><span data-stu-id="c0801-295">If you want to install a prerelease version of a template package, you need to specify the version in the format of `<package-name>::<package-version>`.</span></span> <span data-ttu-id="c0801-296">Por padrão, `dotnet new` passa \* para a versão, que representa a versão de pacote estável mais recente.</span><span class="sxs-lookup"><span data-stu-id="c0801-296">By default, `dotnet new` passes \* for the version, which represents the latest stable package version.</span></span> <span data-ttu-id="c0801-297">Veja um exemplo na seção [exemplos](#examples) .</span><span class="sxs-lookup"><span data-stu-id="c0801-297">See an example in the [Examples](#examples) section.</span></span>
  
  <span data-ttu-id="c0801-298">Se uma versão do modelo já tiver sido instalada quando você executar esse comando, o modelo será atualizado para a versão especificada ou para a versão estável mais recente se nenhuma versão tiver sido especificada.</span><span class="sxs-lookup"><span data-stu-id="c0801-298">If a version of the template was already installed when you run this command, the template will be updated to the specified version, or to the latest stable version if no version was specified.</span></span>

  <span data-ttu-id="c0801-299">Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="c0801-299">For information on creating custom templates, see [Custom templates for dotnet new](custom-templates.md).</span></span>

- **`-l|--list`**

  <span data-ttu-id="c0801-300">Lista os modelos que contêm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="c0801-300">Lists templates containing the specified name.</span></span> <span data-ttu-id="c0801-301">Se nenhum nome for especificado, listará todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="c0801-301">If no name is specified, lists all templates.</span></span>

- **`-lang|--language {C#|F#|VB}`**

  <span data-ttu-id="c0801-302">A linguagem do modelo a ser criada.</span><span class="sxs-lookup"><span data-stu-id="c0801-302">The language of the template to create.</span></span> <span data-ttu-id="c0801-303">A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)).</span><span class="sxs-lookup"><span data-stu-id="c0801-303">The language accepted varies by the template (see defaults in the [arguments](#arguments) section).</span></span> <span data-ttu-id="c0801-304">Não é válida para alguns modelos.</span><span class="sxs-lookup"><span data-stu-id="c0801-304">Not valid for some templates.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c0801-305">Alguns shells interpretam `#` como um caractere especial.</span><span class="sxs-lookup"><span data-stu-id="c0801-305">Some shells interpret `#` as a special character.</span></span> <span data-ttu-id="c0801-306">Nesses casos, coloque o valor do parâmetro de idioma entre aspas.</span><span class="sxs-lookup"><span data-stu-id="c0801-306">In those cases, enclose the language parameter value in quotes.</span></span> <span data-ttu-id="c0801-307">Por exemplo, `dotnet new console -lang "F#"`.</span><span class="sxs-lookup"><span data-stu-id="c0801-307">For example, `dotnet new console -lang "F#"`.</span></span>

- **`-n|--name <OUTPUT_NAME>`**

  <span data-ttu-id="c0801-308">O nome para a saída criada.</span><span class="sxs-lookup"><span data-stu-id="c0801-308">The name for the created output.</span></span> <span data-ttu-id="c0801-309">Se nenhum nome for especificado, o nome do diretório atual será usado.</span><span class="sxs-lookup"><span data-stu-id="c0801-309">If no name is specified, the name of the current directory is used.</span></span>

- **`--nuget-source`**

  <span data-ttu-id="c0801-310">Especifica uma origem do NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="c0801-310">Specifies a NuGet source to use during install.</span></span> <span data-ttu-id="c0801-311">Disponível desde o SDK do .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="c0801-311">Available since .NET Core 2.1 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c0801-312">Local para colocar a saída gerada.</span><span class="sxs-lookup"><span data-stu-id="c0801-312">Location to place the generated output.</span></span> <span data-ttu-id="c0801-313">O padrão é o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="c0801-313">The default is the current directory.</span></span>

- **`--type`**

  <span data-ttu-id="c0801-314">Filtra modelos com base em tipos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c0801-314">Filters templates based on available types.</span></span> <span data-ttu-id="c0801-315">Os valores predefinidos são "projeto", "item" ou "outro".</span><span class="sxs-lookup"><span data-stu-id="c0801-315">Predefined values are "project", "item", or "other".</span></span>

- **`-u|--uninstall [PATH|NUGET_ID]`**

  <span data-ttu-id="c0801-316">Desinstala um pacote de modelos no `PATH` ou `NUGET_ID` fornecido.</span><span class="sxs-lookup"><span data-stu-id="c0801-316">Uninstalls a template pack at the `PATH` or `NUGET_ID` provided.</span></span> <span data-ttu-id="c0801-317">Quando o valor de `<PATH|NUGET_ID>` não é especificado, todos os pacotes de modelos instalados atualmente e seus modelos associados são exibidos.</span><span class="sxs-lookup"><span data-stu-id="c0801-317">When the `<PATH|NUGET_ID>` value isn't specified, all currently installed template packs and their associated templates are displayed.</span></span> <span data-ttu-id="c0801-318">Ao especificar `NUGET_ID`, não inclua o número de versão.</span><span class="sxs-lookup"><span data-stu-id="c0801-318">When specifying `NUGET_ID`, don't include the version number.</span></span>

  <span data-ttu-id="c0801-319">Se você não especificar um parâmetro para essa opção, o comando listará os modelos instalados e os detalhes sobre eles.</span><span class="sxs-lookup"><span data-stu-id="c0801-319">If you don't specify a parameter to this option, the command lists the installed templates and details about them.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c0801-320">Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="c0801-320">To uninstall a template using a `PATH`, you need to fully qualify the path.</span></span> <span data-ttu-id="c0801-321">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="c0801-321">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
  > <span data-ttu-id="c0801-322">Não inclua uma barra de diretório final de encerramento no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="c0801-322">Don't include a final terminating directory slash on your template path.</span></span>

- **`--update-apply`**

  <span data-ttu-id="c0801-323">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento e os instala.</span><span class="sxs-lookup"><span data-stu-id="c0801-323">Checks if there are updates available for the template packs that are currently installed and installs them.</span></span> <span data-ttu-id="c0801-324">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c0801-324">Available since .NET Core 3.0 SDK.</span></span>

- **`--update-check`**

  <span data-ttu-id="c0801-325">Verifica se há atualizações disponíveis para os pacotes de modelos que estão instalados no momento.</span><span class="sxs-lookup"><span data-stu-id="c0801-325">Checks if there are updates available for the template packs that are currently installed.</span></span> <span data-ttu-id="c0801-326">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c0801-326">Available since .NET Core 3.0 SDK.</span></span>

## <a name="template-options"></a><span data-ttu-id="c0801-327">Opções de modelo</span><span class="sxs-lookup"><span data-stu-id="c0801-327">Template options</span></span>

<span data-ttu-id="c0801-328">Cada modelo de projeto pode ter opções adicionais disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c0801-328">Each project template may have additional options available.</span></span> <span data-ttu-id="c0801-329">Os principais modelos têm as seguintes opções adicionais:</span><span class="sxs-lookup"><span data-stu-id="c0801-329">The core templates have the following additional options:</span></span>

### <a name="console"></a><span data-ttu-id="c0801-330">console</span><span class="sxs-lookup"><span data-stu-id="c0801-330">console</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-331">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-331">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-332">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c0801-332">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c0801-333">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-333">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-334">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-334">SDK version</span></span> | <span data-ttu-id="c0801-335">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-335">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-336">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-336">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-337">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-337">3.0</span></span>         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c0801-338">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="c0801-338">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c0801-339">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c0801-339">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c0801-340">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="c0801-340">Not supported for F#.</span></span> <span data-ttu-id="c0801-341">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-341">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c0801-342">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c0801-342">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`** 

  <span data-ttu-id="c0801-343">Se especificado, não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-343">If specified, doesn't execute an implicit restore during project creation.</span></span> <span data-ttu-id="c0801-344">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-344">Available since .NET Core 2.2 SDK.</span></span>

***

### <a name="classlib"></a><span data-ttu-id="c0801-345">classlib</span><span class="sxs-lookup"><span data-stu-id="c0801-345">classlib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-346">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-346">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-347">Valores: `netcoreapp<version>` para criar uma Biblioteca de classes do .NET Core ou `netstandard<version>` para criar uma Biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c0801-347">Values: `netcoreapp<version>` to create a .NET Core Class Library or `netstandard<version>` to create a .NET Standard Class Library.</span></span> <span data-ttu-id="c0801-348">O valor padrão é `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="c0801-348">The default value is `netstandard2.0`.</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c0801-349">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="c0801-349">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c0801-350">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c0801-350">For example, use `--langVersion 7.3` to use C# 7.3.</span></span> <span data-ttu-id="c0801-351">Sem suporte para F#.</span><span class="sxs-lookup"><span data-stu-id="c0801-351">Not supported for F#.</span></span> <span data-ttu-id="c0801-352">Disponível desde o SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-352">Available since .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c0801-353">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c0801-353">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-354">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-354">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="wpf"></a><span data-ttu-id="c0801-355">WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib</span><span class="sxs-lookup"><span data-stu-id="c0801-355">wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-356">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-356">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-357">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c0801-357">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c0801-358">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c0801-358">Available since .NET Core 3.1 SDK.</span></span> 

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c0801-359">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="c0801-359">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c0801-360">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c0801-360">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c0801-361">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c0801-361">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-362">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-362">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="winforms"></a><span data-ttu-id="c0801-363">WinForms, winformslib</span><span class="sxs-lookup"><span data-stu-id="c0801-363">winforms, winformslib</span></span>

- **`--langVersion <VERSION_NUMBER>`**

  <span data-ttu-id="c0801-364">Define a propriedade `LangVersion` no arquivo de projeto criado.</span><span class="sxs-lookup"><span data-stu-id="c0801-364">Sets the `LangVersion` property in the created project file.</span></span> <span data-ttu-id="c0801-365">Por exemplo, use `--langVersion 7.3` para usar C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c0801-365">For example, use `--langVersion 7.3` to use C# 7.3.</span></span>

  <span data-ttu-id="c0801-366">Para obter uma lista de C# versões padrão, consulte [padrões](../../csharp/language-reference/configure-language-version.md#defaults).</span><span class="sxs-lookup"><span data-stu-id="c0801-366">For a list of default C# versions, see [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-367">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-367">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web-others"></a><span data-ttu-id="c0801-368">trabalho, grpc</span><span class="sxs-lookup"><span data-stu-id="c0801-368">worker, grpc</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-369">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-369">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-370">O valor padrão é `netcoreapp3.1`.</span><span class="sxs-lookup"><span data-stu-id="c0801-370">The default value is `netcoreapp3.1`.</span></span> <span data-ttu-id="c0801-371">Disponível desde o SDK do .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c0801-371">Available since .NET Core 3.1 SDK.</span></span> 

- **`--exclude-launch-settings`**

  <span data-ttu-id="c0801-372">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-372">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-373">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-373">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="test"></a><span data-ttu-id="c0801-374">MSTest, xUnit</span><span class="sxs-lookup"><span data-stu-id="c0801-374">mstest, xunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-375">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-375">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-376">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0801-376">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c0801-377">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-377">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-378">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-378">SDK version</span></span> | <span data-ttu-id="c0801-379">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-379">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-380">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-380">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-381">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-381">3.0</span></span>         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c0801-382">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c0801-382">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-383">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-383">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="nunit"></a><span data-ttu-id="c0801-384">NUnit</span><span class="sxs-lookup"><span data-stu-id="c0801-384">nunit</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-385">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-385">Specifies the [framework](../../standard/frameworks.md) to target.</span></span>

  <span data-ttu-id="c0801-386">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-386">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-387">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-387">SDK version</span></span> | <span data-ttu-id="c0801-388">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-388">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-389">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-389">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-390">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-390">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c0801-391">2.2</span><span class="sxs-lookup"><span data-stu-id="c0801-391">2.2</span></span>         | `netcoreapp2.2` |
  | <span data-ttu-id="c0801-392">2.1</span><span class="sxs-lookup"><span data-stu-id="c0801-392">2.1</span></span>         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  <span data-ttu-id="c0801-393">Habilita o empacotamento para o projeto usando o [pacote dotnet](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="c0801-393">Enables packaging for the project using [dotnet pack](dotnet-pack.md).</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-394">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-394">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="page"></a><span data-ttu-id="c0801-395">página</span><span class="sxs-lookup"><span data-stu-id="c0801-395">page</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c0801-396">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-396">Namespace for the generated code.</span></span> <span data-ttu-id="c0801-397">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c0801-397">The default value is `MyApp.Namespace`.</span></span>

- **`-np|--no-pagemodel`**

  <span data-ttu-id="c0801-398">Cria a página sem um PageModel.</span><span class="sxs-lookup"><span data-stu-id="c0801-398">Creates the page without a PageModel.</span></span>

***

### <a name="namespace"></a><span data-ttu-id="c0801-399">viewimports, proto</span><span class="sxs-lookup"><span data-stu-id="c0801-399">viewimports, proto</span></span>

- **`-na|--namespace <NAMESPACE_NAME>`**

  <span data-ttu-id="c0801-400">Namespace para o código gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-400">Namespace for the generated code.</span></span> <span data-ttu-id="c0801-401">O valor padrão é `MyApp.Namespace`.</span><span class="sxs-lookup"><span data-stu-id="c0801-401">The default value is `MyApp.Namespace`.</span></span>

***

### <a name="blazorserver"></a><span data-ttu-id="c0801-402">blazorserver</span><span class="sxs-lookup"><span data-stu-id="c0801-402">blazorserver</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c0801-403">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c0801-403">The type of authentication to use.</span></span> <span data-ttu-id="c0801-404">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c0801-404">The possible values are:</span></span>

  - <span data-ttu-id="c0801-405">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c0801-405">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c0801-406">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="c0801-406">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c0801-407">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c0801-407">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c0801-408">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c0801-408">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c0801-409">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="c0801-409">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c0801-410">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c0801-410">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c0801-411">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-411">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c0801-412">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-412">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-413">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c0801-413">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c0801-414">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-414">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c0801-415">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-415">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c0801-416">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-416">The reset password policy ID for this project.</span></span> <span data-ttu-id="c0801-417">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-417">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c0801-418">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-418">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c0801-419">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-419">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c0801-420">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-420">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c0801-421">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-421">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c0801-422">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c0801-422">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c0801-423">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-423">The Client ID for this project.</span></span> <span data-ttu-id="c0801-424">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-424">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c0801-425">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c0801-425">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c0801-426">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="c0801-426">The domain for the directory tenant.</span></span> <span data-ttu-id="c0801-427">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-427">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-428">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c0801-428">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c0801-429">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-429">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c0801-430">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-430">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c0801-431">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c0801-431">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c0801-432">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="c0801-432">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c0801-433">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-433">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-434">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c0801-434">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c0801-435">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c0801-435">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c0801-436">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-436">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c0801-437">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-437">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c0801-438">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0801-438">Turns off HTTPS.</span></span> <span data-ttu-id="c0801-439">Essa opção só se aplica se `Individual`, `IndividualB2C`, `SingleOrg`ou `MultiOrg` não estiverem sendo usadas para `--auth`.</span><span class="sxs-lookup"><span data-stu-id="c0801-439">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used for `--auth`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c0801-440">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="c0801-440">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c0801-441">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-441">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-442">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-442">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="web"></a><span data-ttu-id="c0801-443">web</span><span class="sxs-lookup"><span data-stu-id="c0801-443">web</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c0801-444">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-444">Excludes *launchSettings.json* from the generated template.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-445">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-445">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-446">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-446">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c0801-447">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-447">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-448">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-448">SDK version</span></span> | <span data-ttu-id="c0801-449">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-449">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-450">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-450">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-451">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-451">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c0801-452">2.1</span><span class="sxs-lookup"><span data-stu-id="c0801-452">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c0801-453">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-453">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c0801-454">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0801-454">Turns off HTTPS.</span></span>

***

### <a name="web-options"></a><span data-ttu-id="c0801-455">MVC, webapp</span><span class="sxs-lookup"><span data-stu-id="c0801-455">mvc, webapp</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c0801-456">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c0801-456">The type of authentication to use.</span></span> <span data-ttu-id="c0801-457">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c0801-457">The possible values are:</span></span>

  - <span data-ttu-id="c0801-458">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c0801-458">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c0801-459">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="c0801-459">`Individual` - Individual authentication.</span></span>
  - <span data-ttu-id="c0801-460">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c0801-460">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c0801-461">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c0801-461">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c0801-462">`MultiOrg` – Autenticação organizacional para vários locatários.</span><span class="sxs-lookup"><span data-stu-id="c0801-462">`MultiOrg` - Organizational authentication for multiple tenants.</span></span>
  - <span data-ttu-id="c0801-463">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c0801-463">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c0801-464">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-464">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c0801-465">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-465">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-466">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c0801-466">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c0801-467">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-467">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c0801-468">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-468">Use with `IndividualB2C` authentication.</span></span>

- **`-rp|--reset-password-policy-id <ID>`**

  <span data-ttu-id="c0801-469">A ID da política de senha de redefinição para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-469">The reset password policy ID for this project.</span></span> <span data-ttu-id="c0801-470">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-470">Use with `IndividualB2C` authentication.</span></span>

- **`-ep|--edit-profile-policy-id <ID>`**

  <span data-ttu-id="c0801-471">A ID de política de perfil de edição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-471">The edit profile policy ID for this project.</span></span> <span data-ttu-id="c0801-472">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-472">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c0801-473">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-473">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c0801-474">Use com a autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-474">Use with `SingleOrg` or `MultiOrg` authentication.</span></span> <span data-ttu-id="c0801-475">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c0801-475">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c0801-476">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-476">The Client ID for this project.</span></span> <span data-ttu-id="c0801-477">Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-477">Use with `IndividualB2C`, `SingleOrg`, or `MultiOrg` authentication.</span></span> <span data-ttu-id="c0801-478">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c0801-478">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c0801-479">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="c0801-479">The domain for the directory tenant.</span></span> <span data-ttu-id="c0801-480">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-480">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-481">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c0801-481">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c0801-482">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-482">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c0801-483">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-483">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c0801-484">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c0801-484">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`--callback-path <PATH>`**

  <span data-ttu-id="c0801-485">O caminho de solicitação dentro do caminho base do aplicativo do URI de redirecionamento.</span><span class="sxs-lookup"><span data-stu-id="c0801-485">The request path within the application's base path of the redirect URI.</span></span> <span data-ttu-id="c0801-486">Use com a autenticação `SingleOrg` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-486">Use with `SingleOrg` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-487">O valor padrão é `/signin-oidc`.</span><span class="sxs-lookup"><span data-stu-id="c0801-487">The default value is `/signin-oidc`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c0801-488">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c0801-488">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c0801-489">Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-489">Only applies to `SingleOrg` or `MultiOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c0801-490">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-490">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c0801-491">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0801-491">Turns off HTTPS.</span></span> <span data-ttu-id="c0801-492">Essa opção é aplicável somente se `Individual`, `IndividualB2C`, `SingleOrg` ou `MultiOrg` não estão sendo usados.</span><span class="sxs-lookup"><span data-stu-id="c0801-492">This option only applies if `Individual`, `IndividualB2C`, `SingleOrg`, or `MultiOrg` aren't being used.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c0801-493">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="c0801-493">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c0801-494">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-494">Only applies to `Individual` or `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-495">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-495">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-496">Opção disponível desde o SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0801-496">Option available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="c0801-497">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-497">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-498">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-498">SDK version</span></span> | <span data-ttu-id="c0801-499">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-499">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-500">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-500">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-501">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-501">3.0</span></span>         | `netcoreapp3.0` |

- **`--no-restore`**

  <span data-ttu-id="c0801-502">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-502">Doesn't execute an implicit restore during project creation.</span></span>

- **`--use-browserlink`**

  <span data-ttu-id="c0801-503">Inclui BrowserLink no projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-503">Includes BrowserLink in the project.</span></span> <span data-ttu-id="c0801-504">Opção não disponível no SDK do .NET Core 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="c0801-504">Option not available in .NET Core 2.2 and 3.1 SDK.</span></span>

***

### <a name="spa"></a><span data-ttu-id="c0801-505">angular, reagir</span><span class="sxs-lookup"><span data-stu-id="c0801-505">angular, react</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c0801-506">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c0801-506">The type of authentication to use.</span></span> <span data-ttu-id="c0801-507">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c0801-507">Available since .NET Core 3.0 SDK.</span></span> 
  
  <span data-ttu-id="c0801-508">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c0801-508">The possible values are:</span></span>

  - <span data-ttu-id="c0801-509">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c0801-509">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c0801-510">`Individual` – Autenticação individual.</span><span class="sxs-lookup"><span data-stu-id="c0801-510">`Individual` - Individual authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c0801-511">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-511">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="c0801-512">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-512">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c0801-513">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0801-513">Turns off HTTPS.</span></span> <span data-ttu-id="c0801-514">Essa opção se aplica somente se a autenticação for `None`.</span><span class="sxs-lookup"><span data-stu-id="c0801-514">This option only applies if authentication is `None`.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c0801-515">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="c0801-515">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c0801-516">Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-516">Only applies to `Individual` or `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-517">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c0801-517">Available since .NET Core 3.0 SDK.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-518">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-518">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-519">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-519">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c0801-520">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-520">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-521">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-521">SDK version</span></span> | <span data-ttu-id="c0801-522">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-522">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-523">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-523">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-524">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-524">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c0801-525">2.1</span><span class="sxs-lookup"><span data-stu-id="c0801-525">2.1</span></span>         | `netcoreapp2.0` |

***

### <a name="reactredux"></a><span data-ttu-id="c0801-526">reactredux</span><span class="sxs-lookup"><span data-stu-id="c0801-526">reactredux</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c0801-527">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-527">Excludes *launchSettings.json* from the generated template.</span></span> 

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-528">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-528">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-529">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-529">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c0801-530">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-530">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-531">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-531">SDK version</span></span> | <span data-ttu-id="c0801-532">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-532">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-533">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-533">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-534">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-534">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c0801-535">2.1</span><span class="sxs-lookup"><span data-stu-id="c0801-535">2.1</span></span>         | `netcoreapp2.0` |

- **`--no-restore`**

  <span data-ttu-id="c0801-536">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-536">Doesn't execute an implicit restore during project creation.</span></span>

- **`--no-https`**

  <span data-ttu-id="c0801-537">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0801-537">Turns off HTTPS.</span></span>

***

### <a name="razorclasslib"></a><span data-ttu-id="c0801-538">razorclasslib</span><span class="sxs-lookup"><span data-stu-id="c0801-538">razorclasslib</span></span>

- **`--no-restore`**

  <span data-ttu-id="c0801-539">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-539">Doesn't execute an implicit restore during project creation.</span></span>

- **`-s|--support-pages-and-views`**

  <span data-ttu-id="c0801-540">Dá suporte à adição de páginas e exibições do Razor tradicionais, além dos componentes dessa biblioteca.</span><span class="sxs-lookup"><span data-stu-id="c0801-540">Supports adding traditional Razor pages and Views in addition to components to this library.</span></span> <span data-ttu-id="c0801-541">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c0801-541">Available since .NET Core 3.0 SDK.</span></span>

***
  
### <a name="webapi"></a><span data-ttu-id="c0801-542">webapi</span><span class="sxs-lookup"><span data-stu-id="c0801-542">webapi</span></span>

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  <span data-ttu-id="c0801-543">O tipo de autenticação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c0801-543">The type of authentication to use.</span></span> <span data-ttu-id="c0801-544">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="c0801-544">The possible values are:</span></span>

  - <span data-ttu-id="c0801-545">`None` – Nenhuma autenticação (Padrão).</span><span class="sxs-lookup"><span data-stu-id="c0801-545">`None` - No authentication (Default).</span></span>
  - <span data-ttu-id="c0801-546">`IndividualB2C` – Autenticação individual com o Azure AD B2C.</span><span class="sxs-lookup"><span data-stu-id="c0801-546">`IndividualB2C` - Individual authentication with Azure AD B2C.</span></span>
  - <span data-ttu-id="c0801-547">`SingleOrg` – Autenticação organizacional para um único locatário.</span><span class="sxs-lookup"><span data-stu-id="c0801-547">`SingleOrg` - Organizational authentication for a single tenant.</span></span>
  - <span data-ttu-id="c0801-548">`Windows` – Autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="c0801-548">`Windows` - Windows authentication.</span></span>

- **`--aad-b2c-instance <INSTANCE>`**

  <span data-ttu-id="c0801-549">A instância de Azure Active Directory B2C à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-549">The Azure Active Directory B2C instance to connect to.</span></span> <span data-ttu-id="c0801-550">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-550">Use with `IndividualB2C` authentication.</span></span> <span data-ttu-id="c0801-551">O valor padrão é `https://login.microsoftonline.com/tfp/`.</span><span class="sxs-lookup"><span data-stu-id="c0801-551">The default value is `https://login.microsoftonline.com/tfp/`.</span></span>

- **`-ssp|--susi-policy-id <ID>`**

  <span data-ttu-id="c0801-552">A ID da política de entrada e inscrição deste projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-552">The sign-in and sign-up policy ID for this project.</span></span> <span data-ttu-id="c0801-553">Use com a autenticação do `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-553">Use with `IndividualB2C` authentication.</span></span>

- **`--aad-instance <INSTANCE>`**

  <span data-ttu-id="c0801-554">A instância de Azure Active Directory à qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-554">The Azure Active Directory instance to connect to.</span></span> <span data-ttu-id="c0801-555">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-555">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c0801-556">O valor padrão é `https://login.microsoftonline.com/`.</span><span class="sxs-lookup"><span data-stu-id="c0801-556">The default value is `https://login.microsoftonline.com/`.</span></span>

- **`--client-id <ID>`**

  <span data-ttu-id="c0801-557">A ID do cliente para este projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-557">The Client ID for this project.</span></span> <span data-ttu-id="c0801-558">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-558">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c0801-559">O valor padrão é `11111111-1111-1111-11111111111111111`.</span><span class="sxs-lookup"><span data-stu-id="c0801-559">The default value is `11111111-1111-1111-11111111111111111`.</span></span>

- **`--domain <DOMAIN>`**

  <span data-ttu-id="c0801-560">O domínio para o locatário do diretório.</span><span class="sxs-lookup"><span data-stu-id="c0801-560">The domain for the directory tenant.</span></span> <span data-ttu-id="c0801-561">Use com a autenticação `IndividualB2C` ou `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-561">Use with `IndividualB2C` or `SingleOrg` authentication.</span></span> <span data-ttu-id="c0801-562">O valor padrão é `qualified.domain.name`.</span><span class="sxs-lookup"><span data-stu-id="c0801-562">The default value is `qualified.domain.name`.</span></span>

- **`--tenant-id <ID>`**

  <span data-ttu-id="c0801-563">A ID de Tenantid do diretório ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="c0801-563">The TenantId ID of the directory to connect to.</span></span> <span data-ttu-id="c0801-564">Use com a autenticação do `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-564">Use with `SingleOrg` authentication.</span></span> <span data-ttu-id="c0801-565">O valor padrão é `22222222-2222-2222-2222-222222222222`.</span><span class="sxs-lookup"><span data-stu-id="c0801-565">The default value is `22222222-2222-2222-2222-222222222222`.</span></span>

- **`-r|--org-read-access`**

  <span data-ttu-id="c0801-566">Permite que este aplicativo Leia o acesso ao diretório.</span><span class="sxs-lookup"><span data-stu-id="c0801-566">Allows this application read-access to the directory.</span></span> <span data-ttu-id="c0801-567">Aplica-se somente à autenticação `SingleOrg`.</span><span class="sxs-lookup"><span data-stu-id="c0801-567">Only applies to `SingleOrg` authentication.</span></span>

- **`--exclude-launch-settings`**

  <span data-ttu-id="c0801-568">Exclui *launchSettings. JSON* do modelo gerado.</span><span class="sxs-lookup"><span data-stu-id="c0801-568">Excludes *launchSettings.json* from the generated template.</span></span>

- **`--no-https`**

  <span data-ttu-id="c0801-569">Desativa o HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0801-569">Turns off HTTPS.</span></span> <span data-ttu-id="c0801-570">`app.UseHsts` e `app.UseHttpsRedirection` não são adicionados ao `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="c0801-570">`app.UseHsts` and `app.UseHttpsRedirection` aren't added to `Startup.Configure`.</span></span> <span data-ttu-id="c0801-571">Esta opção se aplica somente se `IndividualB2C` ou `SingleOrg` não estiverem sendo usados para autenticação.</span><span class="sxs-lookup"><span data-stu-id="c0801-571">This option only applies if `IndividualB2C` or `SingleOrg` aren't being used for authentication.</span></span>

- **`-uld|--use-local-db`**

  <span data-ttu-id="c0801-572">Especifica LocalDB deve ser usado em vez do SQLite.</span><span class="sxs-lookup"><span data-stu-id="c0801-572">Specifies LocalDB should be used instead of SQLite.</span></span> <span data-ttu-id="c0801-573">Aplica-se somente à autenticação `IndividualB2C`.</span><span class="sxs-lookup"><span data-stu-id="c0801-573">Only applies to `IndividualB2C` authentication.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c0801-574">Especifica a [estrutura](../../standard/frameworks.md) a ser direcionada.</span><span class="sxs-lookup"><span data-stu-id="c0801-574">Specifies the [framework](../../standard/frameworks.md) to target.</span></span> <span data-ttu-id="c0801-575">Opção não disponível no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="c0801-575">Option not available in .NET Core 2.2 SDK.</span></span>

  <span data-ttu-id="c0801-576">A tabela a seguir lista os valores padrão de acordo com o número de versão do SDK que você está usando:</span><span class="sxs-lookup"><span data-stu-id="c0801-576">The following table lists the default values according to the SDK version number you're using:</span></span>

  | <span data-ttu-id="c0801-577">Versão do SDK</span><span class="sxs-lookup"><span data-stu-id="c0801-577">SDK version</span></span> | <span data-ttu-id="c0801-578">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="c0801-578">Default value</span></span>   |
  |-------------|-----------------|
  | <span data-ttu-id="c0801-579">3.1</span><span class="sxs-lookup"><span data-stu-id="c0801-579">3.1</span></span>         | `netcoreapp3.1` |
  | <span data-ttu-id="c0801-580">3.0</span><span class="sxs-lookup"><span data-stu-id="c0801-580">3.0</span></span>         | `netcoreapp3.0` |
  | <span data-ttu-id="c0801-581">2.1</span><span class="sxs-lookup"><span data-stu-id="c0801-581">2.1</span></span>         | `netcoreapp2.1` |

- **`--no-restore`**

  <span data-ttu-id="c0801-582">Não executa uma restauração implícita durante a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c0801-582">Doesn't execute an implicit restore during project creation.</span></span>

***

### <a name="globaljson"></a><span data-ttu-id="c0801-583">globaljson</span><span class="sxs-lookup"><span data-stu-id="c0801-583">globaljson</span></span>

- **`--sdk-version <VERSION_NUMBER>`**

  <span data-ttu-id="c0801-584">Especifica a versão do SDK do .NET Core a ser usada no arquivo *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="c0801-584">Specifies the version of the .NET Core SDK to use in the *global.json* file.</span></span>

***

## <a name="examples"></a><span data-ttu-id="c0801-585">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c0801-585">Examples</span></span>

- <span data-ttu-id="c0801-586">Crie um projeto de aplicativo de console em C# especificando o nome do modelo:</span><span class="sxs-lookup"><span data-stu-id="c0801-586">Create a C# console application project by specifying the template name:</span></span>

  ```dotnetcli
  dotnet new "Console Application"
  ```

- <span data-ttu-id="c0801-587">Crie um projeto de aplicativo de console F# no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="c0801-587">Create an F# console application project in the current directory:</span></span>

  ```dotnetcli
  dotnet new console -lang F#
  ```

- <span data-ttu-id="c0801-588">Crie um projeto de biblioteca de classe .NET Standard no diretório especificado:</span><span class="sxs-lookup"><span data-stu-id="c0801-588">Create a .NET Standard class library project in the specified directory:</span></span>

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- <span data-ttu-id="c0801-589">Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:</span><span class="sxs-lookup"><span data-stu-id="c0801-589">Create a new ASP.NET Core C# MVC project in the current directory with no authentication:</span></span>

  ```dotnetcli
  dotnet new mvc -au None
  ```

- <span data-ttu-id="c0801-590">Crie um projeto de xUnit:</span><span class="sxs-lookup"><span data-stu-id="c0801-590">Create a new xUnit project:</span></span>

  ```dotnetcli
  dotnet new xunit
  ```

- <span data-ttu-id="c0801-591">Listar todos os modelos disponíveis para modelos de aplicativo de página única (SPA):</span><span class="sxs-lookup"><span data-stu-id="c0801-591">List all templates available for Single Page Application (SPA) templates:</span></span>

  ```dotnetcli
  dotnet new spa -l
  ```

- <span data-ttu-id="c0801-592">Liste todos os modelos que correspondem à substring *we*.</span><span class="sxs-lookup"><span data-stu-id="c0801-592">List all templates matching the *we* substring.</span></span> <span data-ttu-id="c0801-593">Nenhuma correspondência exata é encontrada, portanto, a correspondência de substring é executada em relação tanto ao nome curto quanto às colunas de nome.</span><span class="sxs-lookup"><span data-stu-id="c0801-593">No exact match is found, so substring matching runs against both the short name and name columns.</span></span>

  ```dotnetcli
  dotnet new we -l
  ```

- <span data-ttu-id="c0801-594">Tentativa de invocar o modelo correspondente a *ng*.</span><span class="sxs-lookup"><span data-stu-id="c0801-594">Attempt to invoke the template matching *ng*.</span></span> <span data-ttu-id="c0801-595">Se não for possível determinar uma única correspondência, liste os modelos que são correspondências parciais.</span><span class="sxs-lookup"><span data-stu-id="c0801-595">If a single match can't be determined, list the templates that are partial matches.</span></span>

  ```dotnetcli
  dotnet new ng
  ```

- <span data-ttu-id="c0801-596">Instale a versão 2,0 dos modelos SPA para ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="c0801-596">Install version 2.0 of the SPA templates for ASP.NET Core:</span></span>

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- <span data-ttu-id="c0801-597">Liste os modelos instalados e os detalhes sobre eles, incluindo como desinstalá-los:</span><span class="sxs-lookup"><span data-stu-id="c0801-597">List the installed templates and details about them, including how to uninstall them:</span></span>

  ```dotnetcli
  dotnet new -u
  ```

- <span data-ttu-id="c0801-598">Crie um *global. JSON* no diretório atual definindo a versão do SDK para 3.1.101:</span><span class="sxs-lookup"><span data-stu-id="c0801-598">Create a *global.json* in the current directory setting the SDK version to 3.1.101:</span></span>

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a><span data-ttu-id="c0801-599">Confira também</span><span class="sxs-lookup"><span data-stu-id="c0801-599">See also</span></span>

- [<span data-ttu-id="c0801-600">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c0801-600">Custom templates for dotnet new</span></span>](custom-templates.md)
- <span data-ttu-id="c0801-601">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md) (Criar um modelo personalizado para dotnet new)</span><span class="sxs-lookup"><span data-stu-id="c0801-601">[Create a custom template for dotnet new](../tutorials/cli-templates-create-item-template.md)</span></span>
- [<span data-ttu-id="c0801-602">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="c0801-602">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="c0801-603">Modelos disponíveis para dotnet new</span><span class="sxs-lookup"><span data-stu-id="c0801-603">Available templates for dotnet new</span></span>](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
