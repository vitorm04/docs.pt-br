---
title: Criar um modelo personalizado para dotnet new
description: Saiba como criar um modelo personalizado para o comando dotnet new neste divertido tutorial.
keywords: .NET, .NET Core, modelo, modelagem, tutorial, dotnet new
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 519b910a-6efe-4394-9b81-0546aa3e7462
ms.workload: dotnetcore
ms.openlocfilehash: 44b4ff6b870a6515f623c690ad722917c9ea5bd3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="e80f3-104">Criar um modelo personalizado para dotnet new</span><span class="sxs-lookup"><span data-stu-id="e80f3-104">Create a custom template for dotnet new</span></span>

<span data-ttu-id="e80f3-105">Este tutorial mostra como:</span><span class="sxs-lookup"><span data-stu-id="e80f3-105">This tutorial shows you how to:</span></span>

- <span data-ttu-id="e80f3-106">Criar um modelo básico com base em um projeto existente ou em um novo projeto de aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="e80f3-106">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="e80f3-107">Empacotar o modelo para distribuição em nuget.org ou de um arquivo *nupkg* local.</span><span class="sxs-lookup"><span data-stu-id="e80f3-107">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="e80f3-108">Instalar o modelo do nuget.org, de um arquivo *nupkg* local ou do sistema de arquivos local.</span><span class="sxs-lookup"><span data-stu-id="e80f3-108">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="e80f3-109">Desinstalar o modelo.</span><span class="sxs-lookup"><span data-stu-id="e80f3-109">Uninstall the template.</span></span>

<span data-ttu-id="e80f3-110">Se você preferir acompanhar o tutorial com um exemplo completo, baixe o [exemplo de modelo de projeto](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span><span class="sxs-lookup"><span data-stu-id="e80f3-110">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="e80f3-111">O exemplo de modelo é configurado para distribuição no NuGet.</span><span class="sxs-lookup"><span data-stu-id="e80f3-111">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="e80f3-112">Se você desejar usar o exemplo baixado com a distribuição do sistema de arquivos, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e80f3-112">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="e80f3-113">Mova o conteúdo da pasta *conteúdo* do exemplo um nível para cima para a pasta *GarciaSoftware.ConsoleTemplate.CSharp*.</span><span class="sxs-lookup"><span data-stu-id="e80f3-113">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="e80f3-114">Exclua a pasta *conteúdo* vazia.</span><span class="sxs-lookup"><span data-stu-id="e80f3-114">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="e80f3-115">Exclua o arquivo *nuspec*.</span><span class="sxs-lookup"><span data-stu-id="e80f3-115">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e80f3-116">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="e80f3-116">Prerequisites</span></span>

- <span data-ttu-id="e80f3-117">Instalar o [SDK 2.0 do .NET Core](https://www.microsoft.com/net/core) ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="e80f3-117">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="e80f3-118">Leia o tópico de referência [Custom templates for dotnet new](../tools/custom-templates.md) (Modelos personalizados para dotnet new).</span><span class="sxs-lookup"><span data-stu-id="e80f3-118">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="e80f3-119">Criar um modelo com base em um projeto</span><span class="sxs-lookup"><span data-stu-id="e80f3-119">Create a template from a project</span></span>

<span data-ttu-id="e80f3-120">Use um projeto existente que você confirmou que compila e executa ou crie um novo projeto de aplicativo de console em uma pasta no disco rígido.</span><span class="sxs-lookup"><span data-stu-id="e80f3-120">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="e80f3-121">Este tutorial pressupõe que o nome da pasta do projeto é *GarciaSoftware.ConsoleTemplate.CSharp* armazenado em *Documentos/Modelos* no perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="e80f3-121">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents/Templates* in the user's profile.</span></span> <span data-ttu-id="e80f3-122">O nome do modelo de projeto do tutorial está no formato *\<Nome da empresa>.\<Tipo de modelo>.\<Linguagem de programação>*, mas é livre para nomear seu projeto e o modelo que você deseja.</span><span class="sxs-lookup"><span data-stu-id="e80f3-122">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="e80f3-123">Adicione uma pasta à raiz do projeto chamado *.template.config*.</span><span class="sxs-lookup"><span data-stu-id="e80f3-123">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="e80f3-124">Dentro da pasta *.template.config*, crie um arquivo *template.json* para configurar o modelo.</span><span class="sxs-lookup"><span data-stu-id="e80f3-124">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="e80f3-125">Para obter mais informações e definições de membro para o arquivo *template.json*, consulte o tópico [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) (Modelos personalizados para dotnet new) e o esquema [*template.json* esquema no Repositório de Esquema JSON](http://json.schemastore.org/template).</span><span class="sxs-lookup"><span data-stu-id="e80f3-125">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

<span data-ttu-id="e80f3-126">O modelo foi concluído.</span><span class="sxs-lookup"><span data-stu-id="e80f3-126">The template is finished.</span></span> <span data-ttu-id="e80f3-127">Neste momento, você tem duas opções para a distribuição de modelos.</span><span class="sxs-lookup"><span data-stu-id="e80f3-127">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="e80f3-128">Para continuar neste tutorial, escolha um caminho ou outro:</span><span class="sxs-lookup"><span data-stu-id="e80f3-128">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="e80f3-129">[Distribuição do NuGet](#use-nuget-distribution): instale o modelo do NuGet ou do arquivo *nupkg* local e use o modelo instalado.</span><span class="sxs-lookup"><span data-stu-id="e80f3-129">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="e80f3-130">[Distribuição de sistema de arquivos](#use-file-system-distribution).</span><span class="sxs-lookup"><span data-stu-id="e80f3-130">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="e80f3-131">Usar a distribuição do NuGet</span><span class="sxs-lookup"><span data-stu-id="e80f3-131">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="e80f3-132">Empacotar o modelo em um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="e80f3-132">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="e80f3-133">Crie uma pasta para o pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="e80f3-133">Create a folder for the NuGet package.</span></span> <span data-ttu-id="e80f3-134">Para o tutorial, o nome da pasta *GarciaSoftware.ConsoleTemplate.CSharp* é usado e a pasta é criada dentro de uma pasta *Documentos/NuGetTemplates* no perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="e80f3-134">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents/NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="e80f3-135">Crie uma pasta chamada *conteúdo* dentro da nova pasta de modelo para guardar os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="e80f3-135">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="e80f3-136">Copie o conteúdo da pasta do seu projeto, juntamente com seu arquivo *.template.config/template.json* para a pasta *conteúdo* criada.</span><span class="sxs-lookup"><span data-stu-id="e80f3-136">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="e80f3-137">Ao lado da pasta *conteúdo*, adicione um arquivo [*nuspec*](/nuget/create-packages/creating-a-package).</span><span class="sxs-lookup"><span data-stu-id="e80f3-137">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="e80f3-138">O arquivo nuspec é um arquivo de manifesto XML que descreve o conteúdo de um pacote e orienta o processo de criação do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="e80f3-138">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>
   
   ![Estrutura de diretórios que mostra o layout do pacote NuGet](./media/create-custom-template/nugetdirectorylayout.png)

1. <span data-ttu-id="e80f3-140">Dentro de um elemento **\<packageTypes>** no arquivo *nuspec*, inclua um elemento **\<packageType>** com um valor de atributo `name` de `Template`.</span><span class="sxs-lookup"><span data-stu-id="e80f3-140">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="e80f3-141">Tanto a pasta *conteúdo* quanto o arquivo *nuspec* devem residir no mesmo diretório.</span><span class="sxs-lookup"><span data-stu-id="e80f3-141">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="e80f3-142">A tabela mostra os elementos mínimos do arquivo *nuspec* necessários para produzir um modelo como um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="e80f3-142">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="e80f3-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="e80f3-143">Element</span></span>            | <span data-ttu-id="e80f3-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="e80f3-144">Type</span></span>   | <span data-ttu-id="e80f3-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="e80f3-145">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="e80f3-146">**\<authors>**</span><span class="sxs-lookup"><span data-stu-id="e80f3-146">**\<authors>**</span></span>     | <span data-ttu-id="e80f3-147">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e80f3-147">string</span></span> | <span data-ttu-id="e80f3-148">Uma lista separada por vírgulas de autores de pacotes, que correspondem aos nomes de perfil em nuget.org. Os autores são exibidos na Galeria do NuGet em nuget.org e são usados para fazer referência cruzada aos pacotes dos mesmos autores.</span><span class="sxs-lookup"><span data-stu-id="e80f3-148">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="e80f3-149">**\<description>**</span><span class="sxs-lookup"><span data-stu-id="e80f3-149">**\<description>**</span></span> | <span data-ttu-id="e80f3-150">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e80f3-150">string</span></span> | <span data-ttu-id="e80f3-151">Uma descrição longa do pacote para exibição de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="e80f3-151">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="e80f3-152">**\<id>**</span><span class="sxs-lookup"><span data-stu-id="e80f3-152">**\<id>**</span></span>          | <span data-ttu-id="e80f3-153">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e80f3-153">string</span></span> | <span data-ttu-id="e80f3-154">O identificador do pacote que não diferencia maiúsculas de minúsculas, que deve ser exclusivo no nuget.org ou qualquer galeria na qual o pacote resida.</span><span class="sxs-lookup"><span data-stu-id="e80f3-154">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="e80f3-155">As IDs não podem conter espaços nem caracteres que não sejam válidos para uma URL e geralmente seguem as regras de namespace do .NET.</span><span class="sxs-lookup"><span data-stu-id="e80f3-155">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="e80f3-156">Consulte [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) (Escolhendo um identificador de pacote único e definindo o número de versão) para obter orientação.</span><span class="sxs-lookup"><span data-stu-id="e80f3-156">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="e80f3-157">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="e80f3-157">**\<packageType>**</span></span> | <span data-ttu-id="e80f3-158">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e80f3-158">string</span></span> | <span data-ttu-id="e80f3-159">Coloque esse elemento dentro de um elemento **\<packageTypes>** entre os elementos **\<metadata>**.</span><span class="sxs-lookup"><span data-stu-id="e80f3-159">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="e80f3-160">Defina o atributo `name` do elemento **\<packageType>** como `Template`.</span><span class="sxs-lookup"><span data-stu-id="e80f3-160">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="e80f3-161">**\<version>**</span><span class="sxs-lookup"><span data-stu-id="e80f3-161">**\<version>**</span></span>     | <span data-ttu-id="e80f3-162">cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e80f3-162">string</span></span> | <span data-ttu-id="e80f3-163">A versão do pacote, seguindo o padrão principal.secundário.patch.</span><span class="sxs-lookup"><span data-stu-id="e80f3-163">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="e80f3-164">Os números de versão podem incluir um sufixo de pré-lançamento, conforme descrito em [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning) (Versões de pré-lançamento).</span><span class="sxs-lookup"><span data-stu-id="e80f3-164">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="e80f3-165">Consulte o esquema de arquivo completo [nuspec](/nuget/schema/nuspec) na *referência do .nuspec*.</span><span class="sxs-lookup"><span data-stu-id="e80f3-165">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="e80f3-166">O arquivo *nuspec* do tutorial é chamado *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* e contém o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="e80f3-166">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. <span data-ttu-id="e80f3-167">[Crie o pacote](/nuget/create-packages/creating-a-package#creating-the-package) usando o comando `nuget pack <PATH_TO_NUSPEC_FILE>`.</span><span class="sxs-lookup"><span data-stu-id="e80f3-167">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="e80f3-168">O comando a seguir pressupõe que a pasta que contém os ativos do NuGet está em *C:/Usuários/\<USUÁRIO> /Documentos/Templates/GarciaSoftware.ConsoleTemplate.CSharp/*.</span><span class="sxs-lookup"><span data-stu-id="e80f3-168">The following command assumes that the folder that holds the NuGet assets is at *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp/*.</span></span> <span data-ttu-id="e80f3-169">Mas sempre que você colocar a pasta em seu sistema, o comando `nuget pack` aceita o caminho para o arquivo *nuspec*:</span><span class="sxs-lookup"><span data-stu-id="e80f3-169">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:/Users/<USER>/Documents/NuGetTemplates/GarciaSoftware.ConsoleTemplate.CSharp/GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="e80f3-170">Publicação do pacote em nuget.org</span><span class="sxs-lookup"><span data-stu-id="e80f3-170">Publishing the package to nuget.org</span></span>

<span data-ttu-id="e80f3-171">Para publicar um pacote NuGet, siga as instruções no tópico [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) (Criar e publicar um pacote).</span><span class="sxs-lookup"><span data-stu-id="e80f3-171">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="e80f3-172">No entanto, é recomendável que você não publique o modelo de tutorial no NuGet, pois ele nunca poderá ser excluído depois de publicado, somente removido da lista.</span><span class="sxs-lookup"><span data-stu-id="e80f3-172">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="e80f3-173">Agora que você tem o pacote NuGet na forma de um arquivo *nupkg*, sugerimos que você siga as instruções abaixo para instalar o modelo diretamente do arquivo *nupkg* local.</span><span class="sxs-lookup"><span data-stu-id="e80f3-173">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="e80f3-174">Instalar o modelo de um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="e80f3-174">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="e80f3-175">Instalar o modelo do arquivo *nupkg* local</span><span class="sxs-lookup"><span data-stu-id="e80f3-175">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="e80f3-176">Para instalar o modelo do arquivo *nupkg* produzido, use o comando `dotnet new` com a opção `-i|--install` e forneça o caminho para o arquivo *nupkg*:</span><span class="sxs-lookup"><span data-stu-id="e80f3-176">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:/Users/<USER>/GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="e80f3-177">Instalar o modelo de um pacote NuGet armazenado em nuget.org</span><span class="sxs-lookup"><span data-stu-id="e80f3-177">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="e80f3-178">Se você desejar instalar um modelo de um pacote do NuGet armazenado em nuget.org, use o comando `dotnet new` com a opção `-i|--install` e forneça o nome do pacote NuGet:</span><span class="sxs-lookup"><span data-stu-id="e80f3-178">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="e80f3-179">O exemplo tem fins apenas demonstrativos.</span><span class="sxs-lookup"><span data-stu-id="e80f3-179">The example is for demonstration purposes only.</span></span> <span data-ttu-id="e80f3-180">Não há um pacote NuGet `GarciaSoftware.ConsoleTemplate.CSharp` em nuget.org e não é recomendável que você publique e consuma modelos de teste do NuGet.</span><span class="sxs-lookup"><span data-stu-id="e80f3-180">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="e80f3-181">Se você executar o comando, nenhum modelo será instalado.</span><span class="sxs-lookup"><span data-stu-id="e80f3-181">If you run the command, no template is installed.</span></span> <span data-ttu-id="e80f3-182">No entanto, é possível instalar um modelo que não tenha sido publicado em nuget.org referenciando o arquivo *nupkg* diretamente no seu sistema de arquivos local, conforme mostrado na seção anterior [Install the template from the local nupgk file](#install-the-template-from-the-local-nupkg-file) (Instalar o modelo do arquivo nupkg local).</span><span class="sxs-lookup"><span data-stu-id="e80f3-182">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="e80f3-183">Se você quiser um exemplo dinâmico de como instalar um modelo de um pacote em nuget.org, será possível usar o [modelo NUnit 3 para dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span><span class="sxs-lookup"><span data-stu-id="e80f3-183">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="e80f3-184">Este modelo configura um projeto para usar testes de unidade do NUnit.</span><span class="sxs-lookup"><span data-stu-id="e80f3-184">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="e80f3-185">Use o seguinte comando para instalá-lo:</span><span class="sxs-lookup"><span data-stu-id="e80f3-185">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="e80f3-186">Quando você lista os modelos com `dotnet new -l`, você vê o *Projeto de teste do NUnit 3* com um nome curto de *nunit* na lista de modelos.</span><span class="sxs-lookup"><span data-stu-id="e80f3-186">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="e80f3-187">Você está pronto para usar o modelo na próxima seção.</span><span class="sxs-lookup"><span data-stu-id="e80f3-187">You're ready to use the template in the next section.</span></span>

![Janela do console que mostra o modelo do NUnit listado com outros modelos instalados](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="e80f3-189">Criar um projeto com base no modelo</span><span class="sxs-lookup"><span data-stu-id="e80f3-189">Create a project from the template</span></span>

<span data-ttu-id="e80f3-190">Depois que o modelo for instalado do NuGet, use o modelo executando o comando `dotnet new <TEMPLATE>` do diretório em que você deseja colocar a saída do mecanismo de modelo (a menos que você esteja usando a opção `-o|--output` para especificar um diretório específico).</span><span class="sxs-lookup"><span data-stu-id="e80f3-190">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="e80f3-191">Para obter mais informações, consulte [Opções `dotnet new`](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="e80f3-191">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="e80f3-192">Forneça o nome curto do modelo diretamente para o comando `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="e80f3-192">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="e80f3-193">Para criar um projeto do modelo NUnit, execute o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e80f3-193">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="e80f3-194">O console mostra que o projeto é criado e que os pacotes do projeto são restaurados.</span><span class="sxs-lookup"><span data-stu-id="e80f3-194">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="e80f3-195">Depois que o comando for executado, o projeto estará pronto para uso.</span><span class="sxs-lookup"><span data-stu-id="e80f3-195">After the command is run, the project is ready for use.</span></span>

![Janela do console que mostra a saída do comando dotnet new enquanto ela cria o projeto NUnit e restaura as dependências do projeto](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="e80f3-197">Para desinstalar um modelo de um pacote NuGet armazenado em nuget.org</span><span class="sxs-lookup"><span data-stu-id="e80f3-197">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="e80f3-198">O exemplo tem fins apenas demonstrativos.</span><span class="sxs-lookup"><span data-stu-id="e80f3-198">The example is for demonstration purposes only.</span></span> <span data-ttu-id="e80f3-199">Não há um pacote NuGet `GarciaSoftware.ConsoleTemplate.CSharp` em nuget.org ou instalado com o SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e80f3-199">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="e80f3-200">Se você executar o comando, nenhum pacote/modelo será desinstalado e você receberá a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="e80f3-200">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
> 
> > <span data-ttu-id="e80f3-201">Não foi possível encontrar algo para desinstalar o 'GarciaSoftware.ConsoleTemplate.CSharp' chamado.</span><span class="sxs-lookup"><span data-stu-id="e80f3-201">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="e80f3-202">Se você tiver instalado o [modelo NUnit 3 para dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) e desejar desinstalá-lo, use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e80f3-202">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="e80f3-203">Desinstalar o modelo de um arquivo nupkg local</span><span class="sxs-lookup"><span data-stu-id="e80f3-203">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="e80f3-204">Quando você desejar desinstalar o modelo, não tente usar o caminho para o arquivo *nupkg*.</span><span class="sxs-lookup"><span data-stu-id="e80f3-204">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="e80f3-205">*A tentativa de desinstalar um modelo usando `dotnet new -u <PATH_TO_NUPKG_FILE>` falha.*</span><span class="sxs-lookup"><span data-stu-id="e80f3-205">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="e80f3-206">Referencie o pacote por seu `id`:</span><span class="sxs-lookup"><span data-stu-id="e80f3-206">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="e80f3-207">Distribuição do sistema de arquivos</span><span class="sxs-lookup"><span data-stu-id="e80f3-207">Use file system distribution</span></span>

<span data-ttu-id="e80f3-208">Para distribuir o modelo, coloque a pasta de modelos de projeto em um local acessível aos usuários em sua rede.</span><span class="sxs-lookup"><span data-stu-id="e80f3-208">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="e80f3-209">Use o comando `dotnet new` com a opção `-i|--install` e especifique o caminho para a pasta de modelo (a pasta de projeto que contém o projeto e a pasta *.template.config*).</span><span class="sxs-lookup"><span data-stu-id="e80f3-209">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="e80f3-210">O tutorial pressupõe que o modelo de projeto está armazenado na pasta *Documentos/Modelos* do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="e80f3-210">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="e80f3-211">Nesse local, instale o modelo com o seguinte comando substituindo \<USUÁRIO> pelo nome do perfil do usuário:</span><span class="sxs-lookup"><span data-stu-id="e80f3-211">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:/Users/<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="e80f3-212">Criar um projeto com base no modelo</span><span class="sxs-lookup"><span data-stu-id="e80f3-212">Create a project from the template</span></span>

<span data-ttu-id="e80f3-213">Depois que o modelo for instalado do sistema de arquivos, use o modelo executando o comando `dotnet new <TEMPLATE>` do diretório em que você deseja colocar a saída do mecanismo de modelo (a menos que você esteja usando a opção `-o|--output` para especificar um diretório específico).</span><span class="sxs-lookup"><span data-stu-id="e80f3-213">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="e80f3-214">Para obter mais informações, consulte [Opções `dotnet new`](~/docs/core/tools/dotnet-new.md#options).</span><span class="sxs-lookup"><span data-stu-id="e80f3-214">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="e80f3-215">Forneça o nome curto do modelo diretamente para o comando `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="e80f3-215">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="e80f3-216">Em uma nova pasta de projeto criada em *C:/Usuários/\<USUÁRIO>/Documents/Projects/MyConsoleApp*, crie um projeto do modelo `garciaconsole`:</span><span class="sxs-lookup"><span data-stu-id="e80f3-216">From a new project folder created at *C:/Users/\<USER>/Documents/Projects/MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="e80f3-217">Desinstalar o modelo</span><span class="sxs-lookup"><span data-stu-id="e80f3-217">Uninstall the template</span></span>

<span data-ttu-id="e80f3-218">Se você tiver criado o modelo no seu sistema de arquivos local em *C:/Usuários/\<USUÁRIO>/Documentos/Templates/GarciaSoftware.ConsoleTemplate.CSharp*, desinstale-o com a opção `-u|--uninstall` e com o caminho para a pasta do modelo:</span><span class="sxs-lookup"><span data-stu-id="e80f3-218">If you created the template on your local file system at *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:/Users/<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="e80f3-219">Para desinstalar o modelo do seu sistema de arquivos local, você precisa qualificar totalmente o caminho.</span><span class="sxs-lookup"><span data-stu-id="e80f3-219">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="e80f3-220">Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.</span><span class="sxs-lookup"><span data-stu-id="e80f3-220">For example, *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="e80f3-221">Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.</span><span class="sxs-lookup"><span data-stu-id="e80f3-221">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="e80f3-222">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e80f3-222">See also</span></span>

[<span data-ttu-id="e80f3-223">Wiki do repositório GitHub dotnet/modelagem</span><span class="sxs-lookup"><span data-stu-id="e80f3-223">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)  
[<span data-ttu-id="e80f3-224">Repositório do GitHub de dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="e80f3-224">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="e80f3-225">Como criar seus próprios modelos para dotnet new</span><span class="sxs-lookup"><span data-stu-id="e80f3-225">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[<span data-ttu-id="e80f3-226">Esquema *template.json* no Repositório de Esquema JSON</span><span class="sxs-lookup"><span data-stu-id="e80f3-226">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)  
