---
title: Modelos personalizados para dotnet new
description: Saiba mais sobre modelos personalizados para qualquer tipo de projeto ou de arquivos do .NET.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 738c6b07f77bdbf6fd946253f95c8691e4172f31
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410345"
---
# <a name="custom-templates-for-dotnet-new"></a><span data-ttu-id="02305-103">Modelos personalizados para dotnet new</span><span class="sxs-lookup"><span data-stu-id="02305-103">Custom templates for dotnet new</span></span>

<span data-ttu-id="02305-104">O [SDK do .NET Core](https://www.microsoft.com/net/download/core) apresenta muitos modelos já instalados e prontos para uso.</span><span class="sxs-lookup"><span data-stu-id="02305-104">The [.NET Core SDK](https://www.microsoft.com/net/download/core) comes with many templates already installed and ready for you to use.</span></span> <span data-ttu-id="02305-105">O [comando `dotnet new`](dotnet-new.md) não é apenas sobre como usar um modelo, mas também como instalar e desinstalar os modelos.</span><span class="sxs-lookup"><span data-stu-id="02305-105">The [`dotnet new` command](dotnet-new.md) isn't only the way to use a template, but also how to install and uninstall templates.</span></span> <span data-ttu-id="02305-106">A partir do .NET Core 2.0, é possível criar seus próprios modelos personalizados para qualquer tipo de projeto, como um aplicativo, serviço, ferramenta ou biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="02305-106">Starting with .NET Core 2.0, you can create your own custom templates for any type of project, such as an app, service, tool, or class library.</span></span> <span data-ttu-id="02305-107">É possível, inclusive, criar um modelo que gere um ou mais arquivos independentes, como um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="02305-107">You can even create a template that outputs one or more independent files, such as a configuration file.</span></span>

<span data-ttu-id="02305-108">É possível instalar modelos personalizados a partir de um pacote NuGet em qualquer feed do NuGet, bastando para isso fazer referência a um arquivo *.nupkg* do NuGet diretamente ou especificando um diretório de sistema de arquivos que contenha o modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-108">You can install custom templates from a NuGet package on any NuGet feed, by referencing a NuGet *.nupkg* file directly, or by specifying a file system directory that contains the template.</span></span> <span data-ttu-id="02305-109">O mecanismo de modelo oferece recursos que permitem substituir valores, incluir e excluir arquivos e executar operações de processamento personalizadas quando seu modelo é usado.</span><span class="sxs-lookup"><span data-stu-id="02305-109">The template engine offers features that allow you to replace values, include and exclude files, and execute custom processing operations when your template is used.</span></span>

<span data-ttu-id="02305-110">O mecanismo de modelo é um software livre e o repositório de código online fica em [dotnet/modelagem](https://github.com/dotnet/templating/) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="02305-110">The template engine is open source, and the online code repository is at [dotnet/templating](https://github.com/dotnet/templating/) on GitHub.</span></span> <span data-ttu-id="02305-111">Acesse o repositório [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) para obter exemplos de modelos.</span><span class="sxs-lookup"><span data-stu-id="02305-111">Visit the [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) repo for samples of templates.</span></span> <span data-ttu-id="02305-112">Mais modelos, incluindo modelos de terceiros, são encontrados em [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (Modelos disponíveis para dotnet new) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="02305-112">More templates, including templates from third parties, are found at [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) on GitHub.</span></span> <span data-ttu-id="02305-113">Para obter mais informações sobre a criação e o uso de modelos personalizados, consulte [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) (Como criar seus próprios modelos para dotnet new) e o [Wiki do repositório GitHub dotnet/modelagem](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="02305-113">For more information about creating and using custom templates, see [How to create your own templates for dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) and the [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki).</span></span>

<span data-ttu-id="02305-114">Para seguir um passo a passo e criar um modelo, consulte o tutorial [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="02305-114">To follow a walkthrough and create a template, see the [Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) tutorial.</span></span>

### <a name="net-default-templates"></a><span data-ttu-id="02305-115">Modelos padrão do .NET</span><span class="sxs-lookup"><span data-stu-id="02305-115">.NET default templates</span></span>

<span data-ttu-id="02305-116">Quando você instala o [SDK do .NET Core](https://www.microsoft.com/net/download/core), você recebe dezenas de modelos internos para criar projetos e arquivos, incluindo aplicativos de console, bibliotecas de classes, projetos de teste de unidade, aplicativos ASP.NET Core (incluindo projetos [Angulares](https://angular.io/) e de [Reação](https://facebook.github.io/react/)) e arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="02305-116">When you install the [.NET Core SDK](https://www.microsoft.com/net/download/core), you receive over a dozen built-in templates for creating projects and files, including console apps, class libraries, unit test projects, ASP.NET Core apps (including [Angular](https://angular.io/) and [React](https://facebook.github.io/react/) projects), and configuration files.</span></span> <span data-ttu-id="02305-117">Para listar os modelos internos, execute o comando `dotnet new` com a opção `-l|--list`:</span><span class="sxs-lookup"><span data-stu-id="02305-117">To list the built-in templates, run the `dotnet new` command with the `-l|--list` option:</span></span>

```console
dotnet new --list
```

## <a name="configuration"></a><span data-ttu-id="02305-118">Configuração</span><span class="sxs-lookup"><span data-stu-id="02305-118">Configuration</span></span>

<span data-ttu-id="02305-119">O modelo é composto pelas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="02305-119">A template is composed of the following parts:</span></span>

- <span data-ttu-id="02305-120">Arquivos e pastas de origem.</span><span class="sxs-lookup"><span data-stu-id="02305-120">Source files and folders.</span></span>
- <span data-ttu-id="02305-121">Um arquivo de configuração (*template.json*).</span><span class="sxs-lookup"><span data-stu-id="02305-121">A configuration file (*template.json*).</span></span>

### <a name="source-files-and-folders"></a><span data-ttu-id="02305-122">Arquivos e pastas de origem</span><span class="sxs-lookup"><span data-stu-id="02305-122">Source files and folders</span></span>

<span data-ttu-id="02305-123">Os arquivos e pastas de origem incluem os arquivos e pastas que você desejar que o mecanismo de modelo use quando o comando `dotnet new <TEMPLATE>` for executado.</span><span class="sxs-lookup"><span data-stu-id="02305-123">The source files and folders include whatever files and folders you want the template engine to use when the `dotnet new <TEMPLATE>` command is run.</span></span> <span data-ttu-id="02305-124">O mecanismo de modelo foi desenvolvido para usar *projetos executáveis* como código-fonte para produzir os projetos.</span><span class="sxs-lookup"><span data-stu-id="02305-124">The template engine is designed to use *runnable projects* as source code to produce projects.</span></span> <span data-ttu-id="02305-125">Isso tem várias vantagens:</span><span class="sxs-lookup"><span data-stu-id="02305-125">This has several benefits:</span></span>

- <span data-ttu-id="02305-126">O mecanismo de modelo não exige que você insira tokens especiais no código-fonte do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="02305-126">The template engine doesn't require you to inject special tokens into your project's source code.</span></span>
- <span data-ttu-id="02305-127">Os arquivos de código não são arquivos especiais nem modificados de nenhuma maneira para trabalhar com o mecanismo de modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-127">The code files aren't special files or modified in any way to work with the template engine.</span></span> <span data-ttu-id="02305-128">Portanto, as ferramentas que você normalmente usa ao trabalhar com projetos também funcionam com o conteúdo do modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-128">So, the tools you normally use when working with projects also work with template content.</span></span>
- <span data-ttu-id="02305-129">Compile, execute e depurar seus projetos de modelo assim como você faz com quaisquer outros projetos.</span><span class="sxs-lookup"><span data-stu-id="02305-129">You build, run, and debug your template projects just like you do for any of your other projects.</span></span>
- <span data-ttu-id="02305-130">É possível criar rapidamente um modelo com base em um projeto existente simplesmente adicionando um arquivo de configuração *./.template.config/template.json* ao projeto.</span><span class="sxs-lookup"><span data-stu-id="02305-130">You can quickly create a template from an existing project just by adding a *./.template.config/template.json* configuration file to the project.</span></span>

<span data-ttu-id="02305-131">Os arquivos e pastas armazenados no modelo não são limitados aos tipos de projeto .NET formais.</span><span class="sxs-lookup"><span data-stu-id="02305-131">Files and folders stored in the template aren't limited to formal .NET project types.</span></span> <span data-ttu-id="02305-132">Os arquivos e pastas de origem podem ser compostos por qualquer conteúdo que você queira criar quando o modelo é usado, mesmo se o mecanismo do modelo produzir apenas um arquivo para sua saída.</span><span class="sxs-lookup"><span data-stu-id="02305-132">Source files and folders may consist of any content that you wish to create when the template is used, even if the template engine produces just one file as its output.</span></span>

<span data-ttu-id="02305-133">Os arquivos gerados pelo modelo podem ser modificados com base na lógica e nas configurações que você forneceu no arquivo de configuração *template.json*.</span><span class="sxs-lookup"><span data-stu-id="02305-133">Files generated by the template can be modified based on logic and settings you've provided in the *template.json* configuration file.</span></span> <span data-ttu-id="02305-134">O usuário pode substituir essas configurações transmitindo opções para o comando `dotnet new <TEMPLATE>`.</span><span class="sxs-lookup"><span data-stu-id="02305-134">The user can override these settings by passing options to the `dotnet new <TEMPLATE>` command.</span></span> <span data-ttu-id="02305-135">Um exemplo comum de lógica personalizada é fornecer o nome de uma classe ou variável no arquivo de código que é implantado por um modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-135">A common example of custom logic is providing a name for a class or variable in the code file that's deployed by a template.</span></span>

### <a name="templatejson"></a><span data-ttu-id="02305-136">template.json</span><span class="sxs-lookup"><span data-stu-id="02305-136">template.json</span></span>

<span data-ttu-id="02305-137">O arquivo *template.json* é colocado em uma pasta *.template.config* no diretório raiz do modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-137">The *template.json* file is placed in a *.template.config* folder in the root directory of the template.</span></span> <span data-ttu-id="02305-138">O arquivo fornece informações de configuração para o mecanismo de modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-138">The file provides configuration information to the template engine.</span></span> <span data-ttu-id="02305-139">A configuração mínima requer os membros mostrados na tabela a seguir, suficiente para criar um modelo funcional.</span><span class="sxs-lookup"><span data-stu-id="02305-139">The minimum configuration requires the members shown in the following table, which is sufficient to create a functional template.</span></span>

| <span data-ttu-id="02305-140">Membro</span><span class="sxs-lookup"><span data-stu-id="02305-140">Member</span></span>            | <span data-ttu-id="02305-141">Tipo</span><span class="sxs-lookup"><span data-stu-id="02305-141">Type</span></span>          | <span data-ttu-id="02305-142">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="02305-142">Description</span></span> |
| ----------------- | ------------- | ----------- |
| `$schema`         | <span data-ttu-id="02305-143">URI</span><span class="sxs-lookup"><span data-stu-id="02305-143">URI</span></span>           | <span data-ttu-id="02305-144">O esquema JSON do arquivo *template.json*.</span><span class="sxs-lookup"><span data-stu-id="02305-144">The JSON schema for the *template.json* file.</span></span> <span data-ttu-id="02305-145">Os editores que dão suporte a esquemas JSON habilitam recursos de edição de JSON quando o esquema é especificado.</span><span class="sxs-lookup"><span data-stu-id="02305-145">Editors that support JSON schemas enable JSON-editing features when the schema is specified.</span></span> <span data-ttu-id="02305-146">Por exemplo, o [Visual Studio Code](https://code.visualstudio.com/) requer que esse membro habilite o IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="02305-146">For example, [Visual Studio Code](https://code.visualstudio.com/) requires this member to enable IntelliSense.</span></span> <span data-ttu-id="02305-147">Use um valor de `http://json.schemastore.org/template`.</span><span class="sxs-lookup"><span data-stu-id="02305-147">Use a value of `http://json.schemastore.org/template`.</span></span> |
| `author`          | <span data-ttu-id="02305-148">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02305-148">string</span></span>        | <span data-ttu-id="02305-149">O autor do modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-149">The author of the template.</span></span> |
| `classifications` | <span data-ttu-id="02305-150">array(string)</span><span class="sxs-lookup"><span data-stu-id="02305-150">array(string)</span></span> | <span data-ttu-id="02305-151">Zero ou mais características do modelo que um usuário pode usar para localizá-lo ao procurá-lo.</span><span class="sxs-lookup"><span data-stu-id="02305-151">Zero or more characteristics of the template that a user might use to find the template when searching for it.</span></span> <span data-ttu-id="02305-152">As classificações também são exibidas na coluna *Marcas* quando ela é exibida em uma lista de modelos produzida usando o comando `dotnet new -l|--list`.</span><span class="sxs-lookup"><span data-stu-id="02305-152">The classifications also appear in the *Tags* column when it appears in a list of templates produced by using the `dotnet new -l|--list` command.</span></span> |
| `identity`        | <span data-ttu-id="02305-153">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02305-153">string</span></span>        | <span data-ttu-id="02305-154">Um nome exclusivo para este modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-154">A unique name for this template.</span></span> |
| `name`            | <span data-ttu-id="02305-155">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02305-155">string</span></span>        | <span data-ttu-id="02305-156">O nome do modelo que os usuários devem ver.</span><span class="sxs-lookup"><span data-stu-id="02305-156">The name for the template that users should see.</span></span> |
| `shortName`       | <span data-ttu-id="02305-157">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="02305-157">string</span></span>        | <span data-ttu-id="02305-158">Um nome abreviado padrão para seleção do modelo aplicável aos ambientes em que o nome do modelo é especificado pelo usuário, não selecionado por uma GUI.</span><span class="sxs-lookup"><span data-stu-id="02305-158">A default shorthand name for selecting the template that applies to environments where the template name is specified by the user, not selected via a GUI.</span></span> <span data-ttu-id="02305-159">Por exemplo, o nome curto é útil ao usar os modelos em um prompt de comando com comandos CLI.</span><span class="sxs-lookup"><span data-stu-id="02305-159">For example, the short name is useful when using templates from a command prompt with CLI commands.</span></span> |

<span data-ttu-id="02305-160">O esquema completo do arquivo *template.json* é encontrado no [Repositório de Esquema JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="02305-160">The full schema for the *template.json* file is found at the [JSON Schema Store](http://json.schemastore.org/template).</span></span> <span data-ttu-id="02305-161">Para saber mais sobre o arquivo *template.json*, veja o [wiki de modelagem dotnet](https://github.com/dotnet/templating/wiki).</span><span class="sxs-lookup"><span data-stu-id="02305-161">For more information about the *template.json* file, see the [dotnet templating wiki](https://github.com/dotnet/templating/wiki).</span></span>

#### <a name="example"></a><span data-ttu-id="02305-162">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02305-162">Example</span></span>

<span data-ttu-id="02305-163">Veja a seguir um exemplo de pasta de modelo que contém dois arquivos de conteúdo: *console.cs* e *readme.txt*.</span><span class="sxs-lookup"><span data-stu-id="02305-163">For example, here is a template folder that contains two content files: *console.cs* and *readme.txt*.</span></span> <span data-ttu-id="02305-164">Observe que há uma pasta obrigatória chamada *.template.config* que contém o arquivo *template.json*.</span><span class="sxs-lookup"><span data-stu-id="02305-164">Take notice that there is the required folder named *.template.config* that contains the *template.json* file.</span></span>

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

<span data-ttu-id="02305-165">O arquivo *template.json* será parecido com este:</span><span class="sxs-lookup"><span data-stu-id="02305-165">The *template.json* file looks like the following:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

<span data-ttu-id="02305-166">A pasta *mytemplate* é um pacote de modelo que pode ser instalado.</span><span class="sxs-lookup"><span data-stu-id="02305-166">The *mytemplate* folder is an installable template pack.</span></span> <span data-ttu-id="02305-167">Depois que o pacote estiver instalado, o `shortName` poderá ser usado com o comando `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="02305-167">Once the pack is installed, the `shortName` can be used with the `dotnet new` command.</span></span> <span data-ttu-id="02305-168">Por exemplo, `dotnet new adatumconsole` resultaria nos arquivos `console.cs` e `readme.txt` para a pasta atual.</span><span class="sxs-lookup"><span data-stu-id="02305-168">For example, `dotnet new adatumconsole` would output the `console.cs` and `readme.txt` files to the current folder.</span></span>

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a><span data-ttu-id="02305-169">Empacotamento de um modelo em um pacote NuGet (arquivo nupkg)</span><span class="sxs-lookup"><span data-stu-id="02305-169">Packing a template into a NuGet package (nupkg file)</span></span>

<span data-ttu-id="02305-170">Um modelo personalizado é fornecido com o comando [dotnet pack](dotnet-pack.md) e um arquivo *csproj*.</span><span class="sxs-lookup"><span data-stu-id="02305-170">A custom template is packed with the [dotnet pack](dotnet-pack.md) command and a *.csproj* file.</span></span> <span data-ttu-id="02305-171">Como alternativa, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) pode ser usado com o comando [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) com um arquivo *.nuspec*.</span><span class="sxs-lookup"><span data-stu-id="02305-171">Alternatively, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) can be used with the [nuget pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) command along with a *.nuspec* file.</span></span> <span data-ttu-id="02305-172">No entanto, o NuGet requer o .NET Framework no Windows e o [Mono](https://www.mono-project.com/) no Linux e MacOS.</span><span class="sxs-lookup"><span data-stu-id="02305-172">However, NuGet requires the .NET Framework on Windows and [Mono](https://www.mono-project.com/) on Linux and MacOS.</span></span>

<span data-ttu-id="02305-173">O arquivo *.csproj* é ligeiramente diferente de um arquivo *.csproj* de projeto de código tradicional.</span><span class="sxs-lookup"><span data-stu-id="02305-173">The *.csproj* file is slightly different from a traditional code-project *.csproj* file.</span></span> <span data-ttu-id="02305-174">Observe as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="02305-174">Note the following settings:</span></span>

01. <span data-ttu-id="02305-175">A configuração `<PackageType>` é adicionada e definida como `Template`.</span><span class="sxs-lookup"><span data-stu-id="02305-175">The `<PackageType>` setting is added and set to `Template`.</span></span>
01. <span data-ttu-id="02305-176">A configuração `<PackageVersion>` é adicionada e definida como um [número de versão do NuGet](/nuget/reference/package-versioning) válido.</span><span class="sxs-lookup"><span data-stu-id="02305-176">The `<PackageVersion>` setting is added and set to a valid [NuGet version number](/nuget/reference/package-versioning).</span></span>
01. <span data-ttu-id="02305-177">A configuração `<PackageId>` é adicionada e definida como um identificador exclusivo.</span><span class="sxs-lookup"><span data-stu-id="02305-177">The `<PackageId>` setting is added and set to a unique identifier.</span></span> <span data-ttu-id="02305-178">Esse identificador é usado para desinstalar o pacote de modelo e também pelos feeds do NuGet para registrar seu pacote de modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-178">This identifier is used to uninstall the template pack and is used by NuGet feeds to register your template pack.</span></span>
01. <span data-ttu-id="02305-179">As configurações genéricas de metadados devem ser definidas: `<Title>`, `<Authors>`, `<Description>` e `<PackageTags>`.</span><span class="sxs-lookup"><span data-stu-id="02305-179">Generic metadata settings should be set: `<Title>`, `<Authors>`, `<Description>`, and `<PackageTags>`.</span></span>
01. <span data-ttu-id="02305-180">A configuração `<TargetFramework>` deve ser definida, mesmo que o binário produzido pelo processo de modelo não seja usado.</span><span class="sxs-lookup"><span data-stu-id="02305-180">The `<TargetFramework>` setting must be set, even though the binary produced by the template process isn't used.</span></span> <span data-ttu-id="02305-181">No exemplo abaixo, ela é definida como `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="02305-181">In the example below it's set to `netstandard2.0`.</span></span>

<span data-ttu-id="02305-182">Um pacote de modelo, na forma de um pacote NuGet *.nupkg*, requer que todos os modelos sejam armazenados na pasta *content* dentro do pacote.</span><span class="sxs-lookup"><span data-stu-id="02305-182">A template pack, in the form of a *.nupkg* NuGet package, requires that all templates be stored in the *content* folder within the package.</span></span> <span data-ttu-id="02305-183">Há mais algumas configurações a serem adicionadas a um arquivo *.csproj* para garantir que o *.nupkg* gerado possa ser instalado como um pacote de modelo:</span><span class="sxs-lookup"><span data-stu-id="02305-183">There are a few more settings to add to a *.csproj* file to ensure that the generated *.nupkg* can be installed as a template pack:</span></span>

01. <span data-ttu-id="02305-184">A configuração `<IncludeContentInPack>` é definida como `true` para incluir qualquer arquivo de projeto defina como **conteúdo** no pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="02305-184">The `<IncludeContentInPack>` setting is set to `true` to include any file the project sets as **content** in the NuGet package.</span></span>
01. <span data-ttu-id="02305-185">A configuração `<IncludeBuildOutput>` é definida como `false` para excluir todos os binários gerados pelo compilador do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="02305-185">The `<IncludeBuildOutput>` setting is set to `false` to exclude all binaries generated by the compiler from the NuGet package.</span></span>
01. <span data-ttu-id="02305-186">A configuração `<ContentTargetFolders>` é definida como `content`.</span><span class="sxs-lookup"><span data-stu-id="02305-186">The `<ContentTargetFolders>` setting is set to `content`.</span></span> <span data-ttu-id="02305-187">Isso garante que os arquivos definidos como **conteúdo** sejam armazenadas na pasta *content* do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="02305-187">This makes sure that the files set as **content** are stored in the *content* folder in the NuGet package.</span></span> <span data-ttu-id="02305-188">Essa pasta no pacote NuGet é analisada pelo sistema de modelo do dotnet.</span><span class="sxs-lookup"><span data-stu-id="02305-188">This folder in the NuGet package is parsed by the dotnet template system.</span></span>

<span data-ttu-id="02305-189">Uma maneira fácil de impedir que todos os arquivos de código sejam compilados pelo seu projeto de modelo é usar o item `<Compile Remove="**\*" />` em seu arquivo de projeto, dentro de um elemento `<ItemGroup>`.</span><span class="sxs-lookup"><span data-stu-id="02305-189">An easy way to exclude all code files from being compiled by your template project is by using the `<Compile Remove="**\*" />` item in your project file, inside an `<ItemGroup>` element.</span></span>

<span data-ttu-id="02305-190">Uma maneira fácil de estruturar seu pacote de modelo é colocar todos os modelos em pastas individuais e, em seguida, cada pasta de modelo dentro de uma pasta *templates* que está localizada no mesmo diretório que seu arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="02305-190">An easy way to structure your template pack is to put all templates in individual folders, and then each template folder inside of a *templates* folder that is located in the same directory as your *.csproj* file.</span></span> <span data-ttu-id="02305-191">Dessa forma, você pode usar um único item de projeto para incluir todos os arquivos e pastas nos *modelos* como **conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="02305-191">This way, you can use a single project item to include all files and folders in the *templates* as **content**.</span></span> <span data-ttu-id="02305-192">Dentro de um elemento `<ItemGroup>`, crie um item `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />`.</span><span class="sxs-lookup"><span data-stu-id="02305-192">Inside of an `<ItemGroup>` element, create a `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` item.</span></span>

<span data-ttu-id="02305-193">Veja a seguir um exemplo de arquivo *.csproj* que segue todas as diretrizes acima.</span><span class="sxs-lookup"><span data-stu-id="02305-193">Here is an example *.csproj* file that follows all of the guidelines above.</span></span> <span data-ttu-id="02305-194">Ele empacota a pasta filho *templates* na pasta do pacote *content* e impede que qualquer arquivo de código seja compilado.</span><span class="sxs-lookup"><span data-stu-id="02305-194">It packs the *templates* child folder to the *content* package folder and excludes any code file from being compiled.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>
    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="02305-195">O exemplo abaixo demonstra a estrutura de arquivos e pastas ao usar um *.csproj* para criar um pacote de modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-195">The example below demonstrates the file and folder structure of using a *.csproj* to create a template pack.</span></span> <span data-ttu-id="02305-196">O arquivo *MyDotnetTemplates.csproj* e a pasta *templates* estão localizados na raiz de um diretório chamado *project_folder*.</span><span class="sxs-lookup"><span data-stu-id="02305-196">The *MyDotnetTemplates.csproj* file and *templates* folder are both located at the root of a directory named *project_folder*.</span></span> <span data-ttu-id="02305-197">A pasta *templates* contém dois modelos, *mytemplate1* e *mytemplate2*.</span><span class="sxs-lookup"><span data-stu-id="02305-197">The *templates* folder contains two templates, *mytemplate1* and *mytemplate2*.</span></span> <span data-ttu-id="02305-198">Cada modelo tem arquivos de conteúdo e uma pasta *.template.config* com um arquivo de configuração *template.json*.</span><span class="sxs-lookup"><span data-stu-id="02305-198">Each template has content files and a *.template.config* folder with a *template.json* config file.</span></span>

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a><span data-ttu-id="02305-199">Instalação de um modelo</span><span class="sxs-lookup"><span data-stu-id="02305-199">Installing a template</span></span>

<span data-ttu-id="02305-200">Use o comando [dotnet new -i|--install](dotnet-new.md) para instalar um pacote.</span><span class="sxs-lookup"><span data-stu-id="02305-200">Use the [dotnet new -i|--install](dotnet-new.md) command to install a package.</span></span>

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="02305-201">Para instalar um modelo de um pacote NuGet armazenado em nuget.org</span><span class="sxs-lookup"><span data-stu-id="02305-201">To install a template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="02305-202">Use o identificador do pacote NuGet para instalar um pacote de modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-202">Use the NuGet package identifier to install a template package.</span></span>

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a><span data-ttu-id="02305-203">Para instalar um modelo de um arquivo nupkg local</span><span class="sxs-lookup"><span data-stu-id="02305-203">To install a template from a local nupkg file</span></span>

<span data-ttu-id="02305-204">Forneça o caminho para um arquivo de pacote NuGet *.nupkg*.</span><span class="sxs-lookup"><span data-stu-id="02305-204">Provide the path to a *.nupkg* NuGet package file.</span></span>

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a><span data-ttu-id="02305-205">Para instalar um modelo de um diretório de sistema de arquivos</span><span class="sxs-lookup"><span data-stu-id="02305-205">To install a template from a file system directory</span></span>

<span data-ttu-id="02305-206">Os modelos podem ser instalados de uma pasta de modelo, como a pasta *mytemplate1* do exemplo acima.</span><span class="sxs-lookup"><span data-stu-id="02305-206">Templates can be installed from a template folder, such as the *mytemplate1* folder from the example above.</span></span> <span data-ttu-id="02305-207">Especifique o caminho da pasta *.template.config*.</span><span class="sxs-lookup"><span data-stu-id="02305-207">Specify the folder path of the *.template.config* folder.</span></span> <span data-ttu-id="02305-208">O caminho para o diretório de modelo não precisa ser absoluto.</span><span class="sxs-lookup"><span data-stu-id="02305-208">The path to the template directory does not need to be absolute.</span></span> <span data-ttu-id="02305-209">No entanto, um caminho absoluto é necessário para desinstalar um modelo que foi instalado de uma pasta.</span><span class="sxs-lookup"><span data-stu-id="02305-209">However, an absolute path is required to uninstall a template that is installed from a folder.</span></span>

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a><span data-ttu-id="02305-210">Obter uma lista de modelos instalados</span><span class="sxs-lookup"><span data-stu-id="02305-210">Get a list of installed templates</span></span>

<span data-ttu-id="02305-211">O comando de desinstalação, sem quaisquer outros parâmetros, listará todos os modelos.</span><span class="sxs-lookup"><span data-stu-id="02305-211">The uninstall command, without any other parameters, will list all installed templates.</span></span>

```console
dotnet new -u
```

<span data-ttu-id="02305-212">Esse comando retorna algo semelhante à seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="02305-212">That command returns something similar to the following output:</span></span>

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

<span data-ttu-id="02305-213">O primeiro nível de itens após `Currently installed items:` são os identificadores usados na desinstalação de um modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-213">The first level of items after `Currently installed items:` are the identifiers used in uninstalling a template.</span></span> <span data-ttu-id="02305-214">E, no exemplo acima, são listados `Microsoft.DotNet.Common.ItemTemplates` e `Microsoft.DotNet.Common.ProjectTemplates.3.0`.</span><span class="sxs-lookup"><span data-stu-id="02305-214">And in the example above, `Microsoft.DotNet.Common.ItemTemplates` and `Microsoft.DotNet.Common.ProjectTemplates.3.0` are listed.</span></span> <span data-ttu-id="02305-215">Se o modelo foi instalado usando um caminho do sistema de arquivos, esse identificador será o caminho da pasta *.template.config*.</span><span class="sxs-lookup"><span data-stu-id="02305-215">If the template was installed by using a file system path, this identifier will the folder path of the *.template.config* folder.</span></span>

## <a name="uninstalling-a-template"></a><span data-ttu-id="02305-216">Desinstalação de um modelo</span><span class="sxs-lookup"><span data-stu-id="02305-216">Uninstalling a template</span></span>

<span data-ttu-id="02305-217">Use o comando [dotnet new -u|--uninstall](dotnet-new.md) para desinstalar um pacote.</span><span class="sxs-lookup"><span data-stu-id="02305-217">Use the [dotnet new -u|--uninstall](dotnet-new.md) command to uninstall a package.</span></span>

<span data-ttu-id="02305-218">Se o pacote foi instalado por um feed do NuGet ou por um arquivo *.nupkg* diretamente, forneça o identificador.</span><span class="sxs-lookup"><span data-stu-id="02305-218">If the package was installed by either a NuGet feed or by a *.nupkg* file directly, provide the identifier.</span></span>

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

<span data-ttu-id="02305-219">Se o pacote foi instalado com a especificação de um caminho para a pasta *.template.config*, use esse caminho **absoluto** para desinstalar o pacote.</span><span class="sxs-lookup"><span data-stu-id="02305-219">If the package was installed by specifying a path to the *.template.config* folder, use that **absolute** path to uninstall the package.</span></span> <span data-ttu-id="02305-220">Você pode ver o caminho absoluto do modelo na saída fornecida pelo comando `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="02305-220">You can see the absolute path of the template in the output provided by the `dotnet new -u` command.</span></span> <span data-ttu-id="02305-221">Para saber mais, confira a seção [Obter uma lista de modelos instalados](#get-a-list-of-installed-templates) acima.</span><span class="sxs-lookup"><span data-stu-id="02305-221">For more information, see the [Get a list of installed templates](#get-a-list-of-installed-templates) section above.</span></span>

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a><span data-ttu-id="02305-222">Criar um projeto usando um modelo personalizado</span><span class="sxs-lookup"><span data-stu-id="02305-222">Create a project using a custom template</span></span>

<span data-ttu-id="02305-223">Depois que um modelo é instalado, use o modelo executando o comando `dotnet new <TEMPLATE>` como você faria com qualquer outro modelo pré-instalado.</span><span class="sxs-lookup"><span data-stu-id="02305-223">After a template is installed, use the template by executing the `dotnet new <TEMPLATE>` command as you would with any other pre-installed template.</span></span> <span data-ttu-id="02305-224">Também é possível especificar [opções](dotnet-new.md#options) para o comando `dotnet new`, incluindo opções específicas do modelo definidas nas configurações de modelo.</span><span class="sxs-lookup"><span data-stu-id="02305-224">You can also specify [options](dotnet-new.md#options) to the `dotnet new` command, including template-specific options you configured in the template settings.</span></span> <span data-ttu-id="02305-225">Forneça o nome curto do modelo diretamente no comando:</span><span class="sxs-lookup"><span data-stu-id="02305-225">Supply the template's short name directly to the command:</span></span>

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a><span data-ttu-id="02305-226">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02305-226">See also</span></span>

- [<span data-ttu-id="02305-227">Criar um modelo personalizado para dotnet new (tutorial)</span><span class="sxs-lookup"><span data-stu-id="02305-227">Create a custom template for dotnet new (tutorial)</span></span>](../tutorials/create-custom-template.md)
- [<span data-ttu-id="02305-228">Wiki do repositório GitHub dotnet/modelagem</span><span class="sxs-lookup"><span data-stu-id="02305-228">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
- [<span data-ttu-id="02305-229">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="02305-229">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
- [<span data-ttu-id="02305-230">Como criar seus próprios modelos para dotnet new</span><span class="sxs-lookup"><span data-stu-id="02305-230">How to create your own templates for dotnet new</span></span>](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [<span data-ttu-id="02305-231">Esquema *template.json* no Repositório de Esquema JSON</span><span class="sxs-lookup"><span data-stu-id="02305-231">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)
