---
title: Visão geral do global.json
description: Saiba como usar o arquivo global.json para definir a versão do SDK do .NET Core ao executar comandos de CLI do .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 07/30/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 05ec296c4c8210c63c7c1b5ce63ef598ca6ac719
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838072"
---
# <a name="globaljson-overview"></a><span data-ttu-id="c2463-103">Visão geral do global.json</span><span class="sxs-lookup"><span data-stu-id="c2463-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="c2463-104">O arquivo *global.json* permite que você defina qual versão do SDK do .NET Core é usada ao executar comandos de CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2463-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="c2463-105">A seleção do SDK do .NET Core não depende da especificação do tempo de execução ao qual o projeto é direcionado.</span><span class="sxs-lookup"><span data-stu-id="c2463-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="c2463-106">A versão do SDK do .NET Core indica quais versões das ferramentas de CLI do .NET Core são usadas.</span><span class="sxs-lookup"><span data-stu-id="c2463-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="c2463-107">Em geral, o ideal é usar a versão mais recente das ferramentas, portanto, não há necessidade de usar um arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c2463-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="c2463-108">Para obter mais informações de como especificar o tempo de execução nesse caso, confira [Estruturas de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c2463-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="c2463-109">O SDK do .NET Core procura um arquivo *global.json* no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="c2463-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="c2463-110">Esquema do global.json</span><span class="sxs-lookup"><span data-stu-id="c2463-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="c2463-111">sdk</span><span class="sxs-lookup"><span data-stu-id="c2463-111">sdk</span></span>

<span data-ttu-id="c2463-112">Tipo: Object</span><span class="sxs-lookup"><span data-stu-id="c2463-112">Type: Object</span></span>

<span data-ttu-id="c2463-113">Especifica as informações sobre o SDK do .NET Core a ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="c2463-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="c2463-114">version</span><span class="sxs-lookup"><span data-stu-id="c2463-114">version</span></span>

<span data-ttu-id="c2463-115">Tipo: String</span><span class="sxs-lookup"><span data-stu-id="c2463-115">Type: String</span></span>

<span data-ttu-id="c2463-116">A versão do SDK do .NET Core a ser usada.</span><span class="sxs-lookup"><span data-stu-id="c2463-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="c2463-117">Observe que esse campo:</span><span class="sxs-lookup"><span data-stu-id="c2463-117">Note that this field:</span></span>

- <span data-ttu-id="c2463-118">Não tem suporte para recurso de curinga, ou seja, o número de versão completo deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="c2463-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="c2463-119">Não dá suporte para intervalos de versão.</span><span class="sxs-lookup"><span data-stu-id="c2463-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="c2463-120">O exemplo a seguir mostra o conteúdo de um arquivo *global.json*:</span><span class="sxs-lookup"><span data-stu-id="c2463-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.1.300"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="c2463-121">global.json e CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="c2463-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="c2463-122">É bom saber quais versões estão disponíveis para definir um arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c2463-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="c2463-123">Encontre a lista completa de SDKs com suporte disponíveis no site [Downloads do .NET](https://www.microsoft.com/net/download/all).</span><span class="sxs-lookup"><span data-stu-id="c2463-123">You can find the full list of supported available SDKs at the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span> <span data-ttu-id="c2463-124">Começando com o .NET Core SDK 2.1, você pode executar o comando a seguir para verificar quais versões do SDK já estão instaladas em seu computador:</span><span class="sxs-lookup"><span data-stu-id="c2463-124">Starting with .NET Core SDK 2.1, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```console
dotnet --list-sdks
```

<span data-ttu-id="c2463-125">Para instalar versões adicionais do SDK do .NET Core em seu computador, visite o site [Downloads do .NET](https://www.microsoft.com/net/download/all).</span><span class="sxs-lookup"><span data-stu-id="c2463-125">To install additional .NET Core SDK versions on your machine, visit the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span>

<span data-ttu-id="c2463-126">Você pode criar um novo arquivo *global.json* no diretório atual executando o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c2463-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```console
dotnet new globaljson --sdk-version 2.1.300
```

## <a name="matching-rules"></a><span data-ttu-id="c2463-127">Regras de correspondência</span><span class="sxs-lookup"><span data-stu-id="c2463-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="c2463-128">As regras de correspondência são controladas pelo apphost, que faz parte do tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2463-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="c2463-129">A versão mais recente do host é usada quando há vários tempos de execução instalados lado a lado.</span><span class="sxs-lookup"><span data-stu-id="c2463-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="c2463-130">Começando com o .NET Core 2.0, as seguintes regras se aplicam ao determinar qual versão do SDK será usada:</span><span class="sxs-lookup"><span data-stu-id="c2463-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="c2463-131">Se não for encontrado nenhum arquivo *global.json* ou se *global.json* não especificar uma versão do SDK, a última versão do SDK instalada será usada.</span><span class="sxs-lookup"><span data-stu-id="c2463-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="c2463-132">A versão mais recente do SDK pode ser uma versão ou um pré-lançamento. Será usado aquele que tiver o número de versão mais alto.</span><span class="sxs-lookup"><span data-stu-id="c2463-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="c2463-133">Se o *global.json* especificar uma versão do SDK:</span><span class="sxs-lookup"><span data-stu-id="c2463-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="c2463-134">Se a versão do SDK especificada for encontrada no computador, a versão exata será usada.</span><span class="sxs-lookup"><span data-stu-id="c2463-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="c2463-135">Se a versão do SDK especificada não for encontrada no computador, a **versão de patch** do SDK mais recente instalada dessa versão será usada.</span><span class="sxs-lookup"><span data-stu-id="c2463-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="c2463-136">A **versão de patch** mais recente do SDK instalada pode ser uma versão ou um pré-lançamento. Será usado o número de versão mais alto.</span><span class="sxs-lookup"><span data-stu-id="c2463-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="c2463-137">No .NET Core 2.1 e nas versões posteriores, as **versões de patch** inferiores à **versão de patch** especificada são ignoradas na seleção do SDK.</span><span class="sxs-lookup"><span data-stu-id="c2463-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="c2463-138">Se a versão do SDK especificada e uma **versão de patch** adequada do SDK não forem encontradas, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="c2463-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="c2463-139">Atualmente, a versão do SDK é composta pelas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="c2463-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="c2463-140">A **versão de recursos** do SDK do .NET Core é representada pelo primeiro dígito (`x`) na última parte do número (`xyz`) para versões do SDK 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="c2463-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="c2463-141">Em geral, o SDK do .NET Core tem um ciclo de versão mais rápido que o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2463-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="c2463-142">A **versão de patch** é definida pelos dois últimos dígitos (`yz`) na última parte do número (`xyz`) do SDK versões 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="c2463-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="c2463-143">Por exemplo, se você especificar `2.1.300` como a versão do SDK, a seleção de SDK localizará até a `2.1.399` mas a `2.1.400` não será considerada uma versão de patch para `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="c2463-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="c2463-144">As versões do SDK do .NET Core `2.1.100` até `2.1.201` foram lançadas durante a transição entre os esquemas de número de versão e não lidam corretamente com a notação `xyz`.</span><span class="sxs-lookup"><span data-stu-id="c2463-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="c2463-145">Se você especificar essas versões no arquivo *global.json*, será altamente recomendado verificar se as versões especificadas estão nos computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="c2463-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="c2463-146">Com o SDK do .NET Core 1.x, se você especificar uma versão e nenhuma correspondência exata for encontrada, a última versão do SDK instalada será usada.</span><span class="sxs-lookup"><span data-stu-id="c2463-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="c2463-147">A versão mais recente do SDK pode ser uma versão ou um pré-lançamento. Será usado aquele que tiver o número de versão mais alto.</span><span class="sxs-lookup"><span data-stu-id="c2463-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="c2463-148">Solucionando problemas de aviso de build</span><span class="sxs-lookup"><span data-stu-id="c2463-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="c2463-149">Você está trabalhando com uma versão prévia do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c2463-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="c2463-150">Você pode definir a versão do SDK por meio de um arquivo global.json no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="c2463-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="c2463-151">Saiba mais em <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="c2463-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="c2463-152">Este aviso indica que seu projeto está sendo compilado usando uma versão prévia do SDK do .NET Core, conforme é explicado na seção [Regras de correspondência](#matching-rules).</span><span class="sxs-lookup"><span data-stu-id="c2463-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="c2463-153">As versões do SDK do .NET Core têm um histórico e o compromisso de manter a alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="c2463-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="c2463-154">No entanto, se você não quiser usar uma versão prévia, adicione um arquivo *global.json* à estrutura de hierarquia do projeto para especificar qual versão do SDK deve ser usada e, em seguida, use `dotnet --list-sdks` para confirmar se a versão está instalada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="c2463-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="c2463-155">Quando uma nova versão for lançada, para usá-la, remova o arquivo *global.json* ou atualize-o para usar a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="c2463-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="c2463-156">O projeto de inicialização '{startupProject}' é direcionado à estrutura '.NETCoreApp' versão '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="c2463-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="c2463-157">Essa versão das ferramentas de linha de comando do .NET do Entity Framework Core são compatíveis apenas com a versão 2.0 ou superiores.</span><span class="sxs-lookup"><span data-stu-id="c2463-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="c2463-158">Para obter informações de como usar as versões mais antigas das ferramentas, confira <https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="c2463-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="c2463-159">Começando com o SDK do .NET Core 2.1 (v.</span><span class="sxs-lookup"><span data-stu-id="c2463-159">Starting with .NET Core SDK 2.1 (v.</span></span> <span data-ttu-id="c2463-160">2.1.300), o comando `dotnet ef` vem incluído no SDK.</span><span class="sxs-lookup"><span data-stu-id="c2463-160">2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="c2463-161">Este aviso indica que o projeto é direcionado ao EF Core 1.0 ou 1.1, que não é compatível com o .NET Core SDK 2.1 e as versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="c2463-161">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core SDK 2.1 and later versions.</span></span> <span data-ttu-id="c2463-162">Para compilar seu projeto, instale o SDK do .NET Core 2.0 (v.</span><span class="sxs-lookup"><span data-stu-id="c2463-162">To compile your project, install .NET Core SDK 2.0 (v.</span></span> <span data-ttu-id="c2463-163">2.1.201) e versões anteriores em seu computador e defina a versão do SDK desejada usando o arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="c2463-163">2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="c2463-164">Para saber mais sobre o comando `dotnet ef`, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="c2463-164">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2463-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2463-165">See also</span></span>

* [<span data-ttu-id="c2463-166">Como os SDKs do projeto são resolvidos</span><span class="sxs-lookup"><span data-stu-id="c2463-166">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
