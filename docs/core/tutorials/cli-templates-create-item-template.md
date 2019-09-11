---
title: Criar um modelo de item para o comando dotnet new - CLI do .NET Core
description: Saiba como criar um modelo de item para o comando dotnet new. Os modelos de item podem conter qualquer quantidade de arquivos.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 4d47146913ed83ff3dd029558f79f23b4f54ce19
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849512"
---
# <a name="tutorial-create-an-item-template"></a><span data-ttu-id="4ae54-104">Tutorial: Criar um modelo de item</span><span class="sxs-lookup"><span data-stu-id="4ae54-104">Tutorial: Create an item template</span></span>

<span data-ttu-id="4ae54-105">Com o .NET Core, você pode criar e implantar modelos que geram projetos, arquivos e até recursos.</span><span class="sxs-lookup"><span data-stu-id="4ae54-105">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="4ae54-106">Este tutorial é a parte um de uma série que ensina como criar, instalar e desinstalar modelos para usar com o comando `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="4ae54-106">This tutorial is part one of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="4ae54-107">Nesta parte da série, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="4ae54-107">In this part of the series, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="4ae54-108">Criar uma classe para um modelo de item</span><span class="sxs-lookup"><span data-stu-id="4ae54-108">Create a class for an item template</span></span>
> * <span data-ttu-id="4ae54-109">Criar a pasta e o arquivo de configuração do modelo</span><span class="sxs-lookup"><span data-stu-id="4ae54-109">Create the template config folder and file</span></span>
> * <span data-ttu-id="4ae54-110">Instalar um modelo a partir de um caminho de arquivos</span><span class="sxs-lookup"><span data-stu-id="4ae54-110">Install a template from a file path</span></span>
> * <span data-ttu-id="4ae54-111">Testar um modelo de item</span><span class="sxs-lookup"><span data-stu-id="4ae54-111">Test an item template</span></span>
> * <span data-ttu-id="4ae54-112">Desinstalar um modelo de item</span><span class="sxs-lookup"><span data-stu-id="4ae54-112">Uninstall an item template</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ae54-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="4ae54-113">Prerequisites</span></span>

* <span data-ttu-id="4ae54-114">[SDK do .NET Core 2.2](https://dotnet.microsoft.com/download) ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ae54-114">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) or later versions.</span></span>
* <span data-ttu-id="4ae54-115">Leia o artigo de referência [Modelos personalizados para dotnet new](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="4ae54-115">Read the reference article [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

  <span data-ttu-id="4ae54-116">O artigo de referência explica os conceitos básicos sobre modelos e como eles são agrupados.</span><span class="sxs-lookup"><span data-stu-id="4ae54-116">The reference article explains the basics about templates and how they're put together.</span></span> <span data-ttu-id="4ae54-117">Algumas dessas informações serão reiteradas aqui.</span><span class="sxs-lookup"><span data-stu-id="4ae54-117">Some of this information will be reiterated here.</span></span>

* <span data-ttu-id="4ae54-118">Abra um terminal e navegue até a pasta _working\templates\\_ .</span><span class="sxs-lookup"><span data-stu-id="4ae54-118">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-the-required-folders"></a><span data-ttu-id="4ae54-119">Criar as pastas obrigatórias</span><span class="sxs-lookup"><span data-stu-id="4ae54-119">Create the required folders</span></span>

<span data-ttu-id="4ae54-120">Esta série usa uma "pasta de trabalho" na qual sua fonte de modelo está contida e uma "pasta de teste" usada para testar seus modelos.</span><span class="sxs-lookup"><span data-stu-id="4ae54-120">This series uses a "working folder" where your template source is contained and a "testing folder" used to test your templates.</span></span> <span data-ttu-id="4ae54-121">A pasta de trabalho e a pasta de teste devem estar na mesma pasta pai.</span><span class="sxs-lookup"><span data-stu-id="4ae54-121">The working folder and testing folder should be under the same parent folder.</span></span>

<span data-ttu-id="4ae54-122">Primeiro, crie a pasta pai. Use o nome que desejar para a pasta.</span><span class="sxs-lookup"><span data-stu-id="4ae54-122">First, create the parent folder, the name does not matter.</span></span> <span data-ttu-id="4ae54-123">Em seguida, crie uma subpasta chamada _working_.</span><span class="sxs-lookup"><span data-stu-id="4ae54-123">Then, create a subfolder named _working_.</span></span> <span data-ttu-id="4ae54-124">Na pasta _working_, crie uma subpasta chamada _templates_.</span><span class="sxs-lookup"><span data-stu-id="4ae54-124">Inside of the _working_ folder, create a subfolder named _templates_.</span></span>

<span data-ttu-id="4ae54-125">Em seguida, crie uma pasta na pasta pai chamada _test_.</span><span class="sxs-lookup"><span data-stu-id="4ae54-125">Next, create a folder under the parent folder named _test_.</span></span> <span data-ttu-id="4ae54-126">A estrutura da pasta deve ser semelhante a isto:</span><span class="sxs-lookup"><span data-stu-id="4ae54-126">The folder structure should look like the following:</span></span>

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a><span data-ttu-id="4ae54-127">Criar um modelo de item</span><span class="sxs-lookup"><span data-stu-id="4ae54-127">Create an item template</span></span>

<span data-ttu-id="4ae54-128">Um modelo de item é um tipo específico de modelo que contém um ou mais arquivos.</span><span class="sxs-lookup"><span data-stu-id="4ae54-128">An item template is a specific type of template that contains one or more files.</span></span> <span data-ttu-id="4ae54-129">Esses tipos de modelos são úteis quando você deseja gerar algo como um arquivo de configuração, código ou solução.</span><span class="sxs-lookup"><span data-stu-id="4ae54-129">These types of templates are useful when you want to generate something like a config, code, or solution file.</span></span> <span data-ttu-id="4ae54-130">Neste exemplo, você criará uma classe que adiciona um método de extensão ao tipo de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4ae54-130">In this example, you'll create a class that adds an extension method to the string type.</span></span>

<span data-ttu-id="4ae54-131">No terminal, navegue até a pasta _working\templates\\_ e crie uma nova subpasta chamada _extensions_.</span><span class="sxs-lookup"><span data-stu-id="4ae54-131">In your terminal, navigate to the _working\templates\\_ folder and create a new subfolder named _extensions_.</span></span> <span data-ttu-id="4ae54-132">Insira a pasta.</span><span class="sxs-lookup"><span data-stu-id="4ae54-132">Enter the folder.</span></span>

```console
working
└───templates
    └───extensions
```

<span data-ttu-id="4ae54-133">Crie um novo arquivo chamado _CommonExtensions.cs_ e abra-o com seu editor de texto favorito.</span><span class="sxs-lookup"><span data-stu-id="4ae54-133">Create a new file named _CommonExtensions.cs_ and open it with your favorite text editor.</span></span> <span data-ttu-id="4ae54-134">Essa classe fornecerá um método de extensão chamado `Reverse` que reverterá o conteúdo de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4ae54-134">This class will provide an extension method named `Reverse` that reverses the contents of a string.</span></span> <span data-ttu-id="4ae54-135">Cole no seguinte código e salve o arquivo:</span><span class="sxs-lookup"><span data-stu-id="4ae54-135">Paste in the following code and save the file:</span></span>

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

<span data-ttu-id="4ae54-136">Agora que você tem o conteúdo do modelo criado, é necessário criar a configuração do modelo na pasta raiz do modelo.</span><span class="sxs-lookup"><span data-stu-id="4ae54-136">Now that you have the content of the template created, you need to create the template config at the root folder of the template.</span></span>

## <a name="create-the-template-config"></a><span data-ttu-id="4ae54-137">Criar a configuração do modelo</span><span class="sxs-lookup"><span data-stu-id="4ae54-137">Create the template config</span></span>

<span data-ttu-id="4ae54-138">Os modelos são reconhecidos no .NET Core por uma pasta especial e um arquivo de configuração que está na raiz do modelo.</span><span class="sxs-lookup"><span data-stu-id="4ae54-138">Templates are recognized in .NET Core by a special folder and config file that exist at the root of your template.</span></span> <span data-ttu-id="4ae54-139">Neste tutorial, a pasta de modelos está localizada em _working\templates\extensions\\_ .</span><span class="sxs-lookup"><span data-stu-id="4ae54-139">In this tutorial, your template folder is located at _working\templates\extensions\\_.</span></span>

<span data-ttu-id="4ae54-140">Quando você cria um modelo, todos os arquivos e pastas na pasta de modelos são incluídos como parte do modelo, exceto a pasta de configuração especial.</span><span class="sxs-lookup"><span data-stu-id="4ae54-140">When you create a template, all files and folders in the template folder are included as part of the template except for the special config folder.</span></span> <span data-ttu-id="4ae54-141">Esta pasta de configuração chama-se _.template.config_.</span><span class="sxs-lookup"><span data-stu-id="4ae54-141">This config folder is named _.template.config_.</span></span>

<span data-ttu-id="4ae54-142">Primeiro, crie uma nova subpasta chamada _.template.config_, insira-a.</span><span class="sxs-lookup"><span data-stu-id="4ae54-142">First, create a new subfolder named _.template.config_, enter it.</span></span> <span data-ttu-id="4ae54-143">Em seguida, crie um novo arquivo chamado _template.json_.</span><span class="sxs-lookup"><span data-stu-id="4ae54-143">Then, create a new file named _template.json_.</span></span> <span data-ttu-id="4ae54-144">A estrutura da pasta deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="4ae54-144">Your folder structure should look like this:</span></span>

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

<span data-ttu-id="4ae54-145">Abra o _template.json_ com seu editor de texto favorito, cole no seguinte código JSON e salve-o:</span><span class="sxs-lookup"><span data-stu-id="4ae54-145">Open the _template.json_ with your favorite text editor and paste in the following JSON code and save it:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

<span data-ttu-id="4ae54-146">Esse arquivo de configuração contém todas as configurações do modelo.</span><span class="sxs-lookup"><span data-stu-id="4ae54-146">This config file contains all the settings for your template.</span></span> <span data-ttu-id="4ae54-147">Você pode ver as configurações básicas, como `name` e `shortName`, mas também há um valor `tags/type` que está definido como `item`.</span><span class="sxs-lookup"><span data-stu-id="4ae54-147">You can see the basic settings, such as `name` and `shortName`, but there's also a `tags/type` value that is set to `item`.</span></span> <span data-ttu-id="4ae54-148">Isso categoriza seu modelo como um modelo de item.</span><span class="sxs-lookup"><span data-stu-id="4ae54-148">This categorizes your template as an item template.</span></span> <span data-ttu-id="4ae54-149">Não há restrições quanto ao tipo do modelo criado.</span><span class="sxs-lookup"><span data-stu-id="4ae54-149">There's no restriction on the type of template you create.</span></span> <span data-ttu-id="4ae54-150">Os valores `item` e `project` são nomes comuns que o .NET Core recomenda para que os usuários possam filtrar facilmente o tipo de modelo que eles pesquisam.</span><span class="sxs-lookup"><span data-stu-id="4ae54-150">The `item` and `project` values are common names that .NET Core recommends so that users can easily filter the type of template they're searching for.</span></span>

<span data-ttu-id="4ae54-151">O item `classifications` representa a coluna **marcações** que você vê quando executa `dotnet new` e obtém uma lista de modelos.</span><span class="sxs-lookup"><span data-stu-id="4ae54-151">The `classifications` item represents the **tags** column you see when you run `dotnet new` and get a list of templates.</span></span> <span data-ttu-id="4ae54-152">Os usuários também podem pesquisar com base nas marcações de classificação.</span><span class="sxs-lookup"><span data-stu-id="4ae54-152">Users can also search based on classification tags.</span></span> <span data-ttu-id="4ae54-153">Não confunda a propriedade `tags` no arquivo \*.json com a lista de marcações `classifications`.</span><span class="sxs-lookup"><span data-stu-id="4ae54-153">Don't confuse the `tags` property in the \*.json file with the `classifications` tags list.</span></span> <span data-ttu-id="4ae54-154">São duas coisas diferentes, mas, infelizmente, nomeadas da mesma forma.</span><span class="sxs-lookup"><span data-stu-id="4ae54-154">They're two different things unfortunately named similarly.</span></span> <span data-ttu-id="4ae54-155">O esquema completo do arquivo *template.json* é encontrado no [Repositório de Esquema JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="4ae54-155">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="4ae54-156">Para saber mais sobre o arquivo *template.json*, veja o [wiki de modelagem dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="4ae54-156">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="4ae54-157">Agora que você já tem um arquivo _.template.config/template.json_ válido, seu modelo está pronto para ser instalado.</span><span class="sxs-lookup"><span data-stu-id="4ae54-157">Now that you have a valid _.template.config/template.json_ file, your template is ready to be installed.</span></span> <span data-ttu-id="4ae54-158">No terminal, navegue até a pasta _extensions_ e execute o seguinte comando para instalar o modelo localizado na pasta atual:</span><span class="sxs-lookup"><span data-stu-id="4ae54-158">In your terminal, navigate to the  _extensions_ folder and run the following command to install the template located at the current folder:</span></span>

* <span data-ttu-id="4ae54-159">**No Windows**: `dotnet new -i .\`</span><span class="sxs-lookup"><span data-stu-id="4ae54-159">**On Windows**: `dotnet new -i .\`</span></span>
* <span data-ttu-id="4ae54-160">**No Linux ou macOS**: `dotnet new -i ./`</span><span class="sxs-lookup"><span data-stu-id="4ae54-160">**On Linux or macOS**: `dotnet new -i ./`</span></span>

<span data-ttu-id="4ae54-161">Esse comando gera a lista de modelos instalados que deve incluir o seu.</span><span class="sxs-lookup"><span data-stu-id="4ae54-161">This command outputs the list of templates installed, which should include yours.</span></span>

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a><span data-ttu-id="4ae54-162">Testar o modelo de item</span><span class="sxs-lookup"><span data-stu-id="4ae54-162">Test the item template</span></span>

<span data-ttu-id="4ae54-163">Agora que você tem um modelo de item instalado, teste-o.</span><span class="sxs-lookup"><span data-stu-id="4ae54-163">Now that you have an item template installed, test it.</span></span> <span data-ttu-id="4ae54-164">Navegue até a pasta _test/_ e crie um novo aplicativo de console com `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="4ae54-164">Navigate to the _test/_ folder and create a new console application with `dotnet new console`.</span></span> <span data-ttu-id="4ae54-165">Isso gera um projeto funcional que você pode testar facilmente com o comando `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="4ae54-165">This generates a working project you can easily test with the `dotnet run` command.</span></span>

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

<span data-ttu-id="4ae54-166">Em seguida, execute `dotnet new stringext` para gerar o _CommonExtensions.cs_ a partir do modelo.</span><span class="sxs-lookup"><span data-stu-id="4ae54-166">Next, run `dotnet new stringext` to generate the _CommonExtensions.cs_ from the template.</span></span>

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

<span data-ttu-id="4ae54-167">Altere o código em _Program.cs_ para inverter a cadeia de caracteres `"Hello World"` com o método de extensão fornecido pelo modelo.</span><span class="sxs-lookup"><span data-stu-id="4ae54-167">Change the code in _Program.cs_ to reverse the `"Hello World"` string with the extension method provided by the template.</span></span>

```csharp
Console.WriteLine("Hello World!".Reverse());
```

<span data-ttu-id="4ae54-168">Execute o programa novamente e você verá que o resultado foi invertido.</span><span class="sxs-lookup"><span data-stu-id="4ae54-168">Run the program again and you'll see that the result is reversed.</span></span>

```console
C:\test> dotnet run
!dlroW olleH
```

<span data-ttu-id="4ae54-169">Parabéns!</span><span class="sxs-lookup"><span data-stu-id="4ae54-169">Congratulations!</span></span> <span data-ttu-id="4ae54-170">Você criou e implantou um modelo de item com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4ae54-170">You created and deployed an item template with .NET Core.</span></span> <span data-ttu-id="4ae54-171">Para se preparar para a próxima parte desta série de tutoriais, você deverá desinstalar o modelo criado.</span><span class="sxs-lookup"><span data-stu-id="4ae54-171">In preparation for the next part of this tutorial series, you must uninstall the template you created.</span></span> <span data-ttu-id="4ae54-172">Lembre-se de também excluir todos os arquivos da pasta _test_.</span><span class="sxs-lookup"><span data-stu-id="4ae54-172">Make sure to delete all files from the _test_ folder too.</span></span> <span data-ttu-id="4ae54-173">Isso levará você de volta a um estado limpo, pronto para a próxima seção principal deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="4ae54-173">This will get you back to a clean state ready for the next major section of this tutorial.</span></span>

## <a name="uninstall-the-template"></a><span data-ttu-id="4ae54-174">Desinstalar o modelo</span><span class="sxs-lookup"><span data-stu-id="4ae54-174">Uninstall the template</span></span>

<span data-ttu-id="4ae54-175">Como você instalou o modelo com o caminho de arquivo, você deve desinstalá-lo com o caminho de arquivo **absoluto**.</span><span class="sxs-lookup"><span data-stu-id="4ae54-175">Because you installed the template by file path, you must uninstall it with the **absolute** file path.</span></span> <span data-ttu-id="4ae54-176">Você pode ver uma lista de modelos instalados executando o comando `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="4ae54-176">You can see a list of templates installed by running the `dotnet new -u` command.</span></span> <span data-ttu-id="4ae54-177">Seu modelo deve ser listado por último.</span><span class="sxs-lookup"><span data-stu-id="4ae54-177">Your template should be listed last.</span></span> <span data-ttu-id="4ae54-178">Use o caminho listado para desinstalar o modelo com o comando `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="4ae54-178">Use the path listed to uninstall your template with the `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` command.</span></span>

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a><span data-ttu-id="4ae54-179">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4ae54-179">Next steps</span></span>

<span data-ttu-id="4ae54-180">Neste tutorial, você criou um modelo de item.</span><span class="sxs-lookup"><span data-stu-id="4ae54-180">In this tutorial, you created an item template.</span></span> <span data-ttu-id="4ae54-181">Para saber como criar um modelo de projeto, continue a ver essa série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="4ae54-181">To learn how to create a project template, continue this tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ae54-182">Criar um modelo de projeto</span><span class="sxs-lookup"><span data-stu-id="4ae54-182">Create a project template</span></span>](cli-templates-create-project-template.md)
