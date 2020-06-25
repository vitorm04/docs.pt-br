---
title: Instalar e gerenciar modelos de SDK-.NET Core
description: Saiba como instalar modelos do .NET Core no Windows, Linux e macOS.
author: adegeo
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 09acae1409eb0492be10bd3a61b14da5be57c6c7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324492"
---
# <a name="manage-net-project-and-item-templates"></a><span data-ttu-id="b6b4c-103">Gerenciar modelos de projeto e item do .NET</span><span class="sxs-lookup"><span data-stu-id="b6b4c-103">Manage .NET project and item templates</span></span>

<span data-ttu-id="b6b4c-104">O .NET Core fornece um sistema de modelo que permite aos usuários instalar ou desinstalar modelos do NuGet, um arquivo de pacote NuGet ou um diretório do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-104">.NET Core provides a template system that enables users to install or uninstall templates from NuGet, a NuGet package file, or a file system directory.</span></span> <span data-ttu-id="b6b4c-105">Este artigo descreve como gerenciar modelos do .NET Core por meio da CLI do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-105">This article describes how to manage .NET Core templates through the .NET Core SDK CLI.</span></span>

<span data-ttu-id="b6b4c-106">Para obter mais informações sobre como criar modelos, consulte [tutorial: criar modelos](../tutorials/cli-templates-create-item-template.md).</span><span class="sxs-lookup"><span data-stu-id="b6b4c-106">For more information about creating templates, see [Tutorial: Create templates](../tutorials/cli-templates-create-item-template.md).</span></span>

## <a name="install-template"></a><span data-ttu-id="b6b4c-107">Instalar modelo</span><span class="sxs-lookup"><span data-stu-id="b6b4c-107">Install template</span></span>

<span data-ttu-id="b6b4c-108">Os modelos são instalados por meio do [dotnet new](../tools/dotnet-new.md) comando do SDK com o `-i` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-108">Templates are installed through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-i` parameter.</span></span> <span data-ttu-id="b6b4c-109">Você pode fornecer o identificador de pacote NuGet de um modelo ou uma pasta que contém os arquivos de modelo.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-109">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-hosted-package"></a><span data-ttu-id="b6b4c-110">Pacote hospedado do NuGet</span><span class="sxs-lookup"><span data-stu-id="b6b4c-110">NuGet hosted package</span></span>

<span data-ttu-id="b6b4c-111">Os modelos da CLI do .NET são carregados no [NuGet](https://www.nuget.org/) para ampla distribuição.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-111">.NET CLI templates are uploaded to [NuGet](https://www.nuget.org/) for wide distribution.</span></span> <span data-ttu-id="b6b4c-112">Os modelos também podem ser instalados de um feed particular.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-112">Templates can also be installed from a private feed.</span></span> <span data-ttu-id="b6b4c-113">Em vez de carregar um modelo em um feed do NuGet, os arquivos de modelo *nupkg* podem ser distribuídos e instalados manualmente, conforme descrito na seção [pacote do NuGet local](#local-nuget-package) .</span><span class="sxs-lookup"><span data-stu-id="b6b4c-113">Instead of uploading a template to a NuGet feed, *nupkg* template files can be distributed and manually installed, as described in the [Local NuGet package](#local-nuget-package) section.</span></span>

<span data-ttu-id="b6b4c-114">Para obter mais informações sobre a configuração de feeds do NuGet, consulte [dotnet nuget add source](../tools/dotnet-nuget-add-source.md) .</span><span class="sxs-lookup"><span data-stu-id="b6b4c-114">For more information about configuring NuGet feeds, see [dotnet nuget add source](../tools/dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="b6b4c-115">Para instalar um pacote de modelos do feed do NuGet padrão, use o `dotnet new -i {package-id}` comando:</span><span class="sxs-lookup"><span data-stu-id="b6b4c-115">To install a template pack from the default NuGet feed, use the `dotnet new -i {package-id}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

<span data-ttu-id="b6b4c-116">Para instalar um pacote de modelos do feed do NuGet padrão com uma versão específica, use o `dotnet new -i {package-id}::{version}` comando:</span><span class="sxs-lookup"><span data-stu-id="b6b4c-116">To install a template pack from the default NuGet feed with a specific version, use the `dotnet new -i {package-id}::{version}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a><span data-ttu-id="b6b4c-117">Pacote NuGet local</span><span class="sxs-lookup"><span data-stu-id="b6b4c-117">Local NuGet package</span></span>

<span data-ttu-id="b6b4c-118">Quando um pacote de modelos é criado, um arquivo *nupkg* é gerado.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-118">When a template pack is created, a *nupkg* file is generated.</span></span> <span data-ttu-id="b6b4c-119">Se você tiver um arquivo *nupkg* contendo modelos, poderá instalá-lo com o `dotnet new -i {path-to-package}` comando:</span><span class="sxs-lookup"><span data-stu-id="b6b4c-119">If you have a *nupkg* file containing templates, you can install it with the `dotnet new -i {path-to-package}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a><span data-ttu-id="b6b4c-120">Pasta</span><span class="sxs-lookup"><span data-stu-id="b6b4c-120">Folder</span></span>

<span data-ttu-id="b6b4c-121">Como alternativa à instalação do modelo a partir de um arquivo *nupkg* , você também pode instalar modelos de uma pasta diretamente com o `dotnet new -i {folder-path}` comando.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-121">As an alternative to installing template from a *nupkg* file, you can also install templates from a folder directly with the `dotnet new -i {folder-path}` command.</span></span> <span data-ttu-id="b6b4c-122">A pasta especificada é tratada como o identificador do pacote de modelos para qualquer modelo encontrado.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-122">The folder specified is treated as the template pack identifier for any template found.</span></span> <span data-ttu-id="b6b4c-123">Qualquer modelo encontrado na hierarquia da pasta especificada é instalado.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-123">Any template found in the specified folder's hierarchy is installed.</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

<span data-ttu-id="b6b4c-124">O `{folder-path}` especificado no comando torna-se o identificador do pacote de modelos para todos os modelos encontrados.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-124">The `{folder-path}` specified on the command becomes the template pack identifier for all templates found.</span></span> <span data-ttu-id="b6b4c-125">Conforme especificado na seção [modelos de lista](#list-templates) , você pode obter uma lista de modelos instalados com o `dotnet new -u` comando.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-125">As specified in the [List templates](#list-templates) section, you can get a list of templates installed with the `dotnet new -u` command.</span></span> <span data-ttu-id="b6b4c-126">Neste exemplo, o identificador do pacote de modelos é mostrado como a pasta usada para instalação:</span><span class="sxs-lookup"><span data-stu-id="b6b4c-126">In this example, the template pack identifier is shown as the folder used for install:</span></span>

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a><span data-ttu-id="b6b4c-127">Desinstalar modelo</span><span class="sxs-lookup"><span data-stu-id="b6b4c-127">Uninstall template</span></span>

<span data-ttu-id="b6b4c-128">Os modelos são desinstalados por meio do [dotnet new](../tools/dotnet-new.md) comando do SDK com o `-u` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-128">Templates are uninstalled through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-u` parameter.</span></span> <span data-ttu-id="b6b4c-129">Você pode fornecer o identificador de pacote NuGet de um modelo ou uma pasta que contém os arquivos de modelo.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-129">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-package"></a><span data-ttu-id="b6b4c-130">Pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="b6b4c-130">NuGet package</span></span>

<span data-ttu-id="b6b4c-131">Depois que um pacote de modelos NuGet é instalado, de um feed NuGet ou de um arquivo *nupkg* , você pode desinstalá-lo referenciando o identificador do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-131">After a NuGet template pack is installed, either from a NuGet feed or a *nupkg* file, you can uninstall it by referencing the NuGet package identifier.</span></span>

<span data-ttu-id="b6b4c-132">Para desinstalar um pacote de modelos, use o `dotnet new -u {package-id}` comando:</span><span class="sxs-lookup"><span data-stu-id="b6b4c-132">To uninstall a template pack, use the `dotnet new -u {package-id}` command:</span></span>

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a><span data-ttu-id="b6b4c-133">Pasta</span><span class="sxs-lookup"><span data-stu-id="b6b4c-133">Folder</span></span>

<span data-ttu-id="b6b4c-134">Quando os modelos são instalados por meio de um [caminho de pasta](#folder), o caminho da pasta se torna o identificador do pacote de modelos.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-134">When templates are installed through a [folder path](#folder), the folder path becomes the template pack identifier.</span></span>

<span data-ttu-id="b6b4c-135">Para desinstalar um pacote de modelos, use o `dotnet new -u {package-folder-path}` comando:</span><span class="sxs-lookup"><span data-stu-id="b6b4c-135">To uninstall a template pack, use the `dotnet new -u {package-folder-path}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a><span data-ttu-id="b6b4c-136">Listar modelos</span><span class="sxs-lookup"><span data-stu-id="b6b4c-136">List templates</span></span>

<span data-ttu-id="b6b4c-137">Usando o comando de desinstalação padrão sem um identificador de pacote, você pode ver uma lista de modelos instalados junto com o comando que desinstala cada modelo.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-137">By using the standard uninstall command without a package identifier, you can see a list of installed templates along with the command that uninstalls each template.</span></span>

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a><span data-ttu-id="b6b4c-138">Instalar modelos de outros SDKs</span><span class="sxs-lookup"><span data-stu-id="b6b4c-138">Install templates from other SDKs</span></span>

<span data-ttu-id="b6b4c-139">Se você instalou cada versão do SDK em sequência, por exemplo, instalou o SDK 2,0, o SDK 2,1 e assim por diante, terá todos os modelos do SDK instalados.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-139">If you've installed each version of the SDK sequentially, for example you installed SDK 2.0, then SDK 2.1, and so on, you'll have every SDK's templates installed.</span></span> <span data-ttu-id="b6b4c-140">No entanto, se você começar com uma versão mais recente do SDK, como 3,1, somente os modelos para [versões LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) serão incluídos, que no momento da versão do SDK 3,1 é SDK 2,1 e SDK 3,1.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-140">However, if you start with a later SDK version, like 3.1, only the templates for [LTS (long term support) releases](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) are included, which at the time of the SDK 3.1 release is SDK 2.1 and SDK 3.1.</span></span> <span data-ttu-id="b6b4c-141">Os modelos para qualquer outra versão não estão incluídos.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-141">Templates for any other release aren't included.</span></span>

<span data-ttu-id="b6b4c-142">Os modelos do .NET Core estão disponíveis no NuGet e você pode instalá-los como qualquer outro modelo.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-142">The .NET Core templates are available on NuGet, and you can install them like any other template.</span></span> <span data-ttu-id="b6b4c-143">Para obter mais informações, consulte [instalar o pacote hospedado do NuGet](#nuget-hosted-package).</span><span class="sxs-lookup"><span data-stu-id="b6b4c-143">For more information, see [Install NuGet hosted package](#nuget-hosted-package).</span></span>

| <span data-ttu-id="b6b4c-144">.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-144">SDK</span></span>              | <span data-ttu-id="b6b4c-145">Identificador do pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="b6b4c-145">NuGet Package Identifier</span></span>                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b6b4c-146">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b6b4c-146">.NET Core 2.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| <span data-ttu-id="b6b4c-147">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="b6b4c-147">.NET Core 2.2</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| <span data-ttu-id="b6b4c-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b6b4c-148">.NET Core 3.0</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| <span data-ttu-id="b6b4c-149">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b6b4c-149">.NET Core 3.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| <span data-ttu-id="b6b4c-150">ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b6b4c-150">ASP.NET Core 2.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| <span data-ttu-id="b6b4c-151">ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="b6b4c-151">ASP.NET Core 2.2</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| <span data-ttu-id="b6b4c-152">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="b6b4c-152">ASP.NET Core 3.0</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| <span data-ttu-id="b6b4c-153">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b6b4c-153">ASP.NET Core 3.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

<span data-ttu-id="b6b4c-154">Por exemplo, a SDK do .NET Core inclui modelos para um aplicativo de console destinado ao .NET Core 2,1 e ao .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-154">For example, the .NET Core SDK includes templates for a console app targeting .NET Core 2.1 and .NET Core 3.1.</span></span> <span data-ttu-id="b6b4c-155">Se você quisesse direcionar o .NET Core 3,0, precisaria instalar os modelos de 3,0.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-155">If you wanted to target .NET Core 3.0, you would need to install the 3.0 templates.</span></span>

01. <span data-ttu-id="b6b4c-156">Tente criar um aplicativo que tenha como destino o .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-156">Try creating an app that targets .NET Core 3.0.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="b6b4c-157">Se você vir uma mensagem de erro, precisará instalar os modelos.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-157">If you see an error message, you need to install the templates.</span></span>

    > <span data-ttu-id="b6b4c-158">Não foi possível encontrar um modelo instalado que corresponda à entrada, pesquisando online para um que faça isso...</span><span class="sxs-lookup"><span data-stu-id="b6b4c-158">Couldn't find an installed template that matches the input, searching online for one that does...</span></span>

01. <span data-ttu-id="b6b4c-159">Instale os modelos de projeto do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-159">Install the .NET Core 3.0 project templates.</span></span>

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. <span data-ttu-id="b6b4c-160">Tente criar o aplicativo uma segunda vez.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-160">Try creating the app a second time.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="b6b4c-161">E você deverá ver uma mensagem indicando que o projeto foi criado.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-161">And you should see a message indicating the project was created.</span></span>

    > <span data-ttu-id="b6b4c-162">O modelo "aplicativo de console" foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-162">The template "Console Application" was created successfully.</span></span>
    >
    > <span data-ttu-id="b6b4c-163">Processando ações de pós-criação... Executando ' dotnet restore ' em path-to-Project-File. csproj... Determinando os projetos a serem restaurados... Restauração concluída em 1, 5 s para Path-to-Project-File. csproj.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-163">Processing post-creation actions... Running 'dotnet restore' on path-to-project-file.csproj... Determining projects to restore... Restore completed in 1.05 sec for path-to-project-file.csproj.</span></span>
    >
    > <span data-ttu-id="b6b4c-164">Restauração bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b6b4c-164">Restore succeeded.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6b4c-165">Veja também</span><span class="sxs-lookup"><span data-stu-id="b6b4c-165">See also</span></span>

- [<span data-ttu-id="b6b4c-166">Tutorial: criar um modelo de item</span><span class="sxs-lookup"><span data-stu-id="b6b4c-166">Tutorial: Create an item template</span></span>](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
