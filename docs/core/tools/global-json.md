---
title: Visão geral do global.json
description: Saiba como usar o arquivo global.json para definir a versão do SDK do .NET Core ao executar comandos de CLI do .NET Core.
ms.date: 04/21/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5384b59cccb629a5409d26a8df7c81b3999fc95f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021343"
---
# <a name="globaljson-overview"></a><span data-ttu-id="74d3f-103">Visão geral do global.json</span><span class="sxs-lookup"><span data-stu-id="74d3f-103">global.json overview</span></span>

<span data-ttu-id="74d3f-104">**Este artigo se aplica a:** ✔️ .NET Core 2.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="74d3f-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="74d3f-105">O arquivo *global.json* permite que você defina qual versão do SDK do .NET Core é usada ao executar comandos de CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d3f-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="74d3f-106">A seleção do SDK do .NET Core não depende da especificação do runtime ao qual o projeto é direcionado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="74d3f-107">A versão .NET Core SDK indica quais versões do .NET Core CLI é usada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="74d3f-108">Em geral, você deseja usar a versão mais recente das ferramentas SDK, de modo que nenhum arquivo *global.json* é necessário.</span><span class="sxs-lookup"><span data-stu-id="74d3f-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="74d3f-109">Em alguns cenários avançados, você pode querer controlar a versão das ferramentas sdk, e este artigo explica como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="74d3f-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="74d3f-110">Para obter mais informações de como especificar o runtime nesse caso, confira [Estruturas de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="74d3f-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="74d3f-111">O SDK do .NET Core procura um arquivo *global.json* no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="74d3f-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="74d3f-112">Esquema do global.json</span><span class="sxs-lookup"><span data-stu-id="74d3f-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="74d3f-113">sdk</span><span class="sxs-lookup"><span data-stu-id="74d3f-113">sdk</span></span>

<span data-ttu-id="74d3f-114">Digite: `object`</span><span class="sxs-lookup"><span data-stu-id="74d3f-114">Type: `object`</span></span>

<span data-ttu-id="74d3f-115">Especifica as informações sobre o SDK do .NET Core a ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="74d3f-116">version</span><span class="sxs-lookup"><span data-stu-id="74d3f-116">version</span></span>

- <span data-ttu-id="74d3f-117">Digite: `string`</span><span class="sxs-lookup"><span data-stu-id="74d3f-117">Type: `string`</span></span>

- <span data-ttu-id="74d3f-118">Disponível desde: .NET Core 1.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="74d3f-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="74d3f-119">A versão do SDK do .NET Core a ser usada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="74d3f-120">Este campo:</span><span class="sxs-lookup"><span data-stu-id="74d3f-120">This field:</span></span>

- <span data-ttu-id="74d3f-121">Não tem suporte a curinga, ou seja, o número completo da versão tem que ser especificado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="74d3f-122">Não dá suporte para intervalos de versão.</span><span class="sxs-lookup"><span data-stu-id="74d3f-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="74d3f-123">permitirPré-lançamento</span><span class="sxs-lookup"><span data-stu-id="74d3f-123">allowPrerelease</span></span>

- <span data-ttu-id="74d3f-124">Digite: `boolean`</span><span class="sxs-lookup"><span data-stu-id="74d3f-124">Type: `boolean`</span></span>

- <span data-ttu-id="74d3f-125">Disponível desde: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="74d3f-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="74d3f-126">Indica se o resolver SDK deve considerar as versões de pré-lançamento ao selecionar a versão SDK para usar.</span><span class="sxs-lookup"><span data-stu-id="74d3f-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="74d3f-127">Se você não definir esse valor explicitamente, o valor padrão depende se você está executando do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="74d3f-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="74d3f-128">Se você **não** estiver no Visual Studio, o valor padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="74d3f-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="74d3f-129">Se você estiver no Visual Studio, ele usa o status de pré-lançamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="74d3f-130">Ou seja, se você estiver usando uma versão preview do Visual Studio ou definir as visualizações de uso da opção `true` **.NET Core SDK** (em **Recursos** > de visualização do**ambiente** > de**opções** > de**ferramentas),** o valor padrão é ; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="74d3f-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="74d3f-131">rollForward</span><span class="sxs-lookup"><span data-stu-id="74d3f-131">rollForward</span></span>

- <span data-ttu-id="74d3f-132">Digite: `string`</span><span class="sxs-lookup"><span data-stu-id="74d3f-132">Type: `string`</span></span>

- <span data-ttu-id="74d3f-133">Disponível desde: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="74d3f-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="74d3f-134">A política de encaminhamento para usar ao selecionar uma versão SDK, seja como um recuo quando uma versão específica do SDK está faltando ou como uma diretiva para usar uma versão superior.</span><span class="sxs-lookup"><span data-stu-id="74d3f-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="74d3f-135">Uma [versão](#version) deve ser `rollForward` especificada com um valor, `latestMajor`a menos que você esteja definindo-a para .</span><span class="sxs-lookup"><span data-stu-id="74d3f-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="74d3f-136">Para entender as políticas disponíveis e seu comportamento, considere as seguintes `x.y.znn`definições para uma versão SDK no formato :</span><span class="sxs-lookup"><span data-stu-id="74d3f-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="74d3f-137">`x`é a versão principal.</span><span class="sxs-lookup"><span data-stu-id="74d3f-137">`x` is the major version.</span></span>
- <span data-ttu-id="74d3f-138">`y`é a versão menor.</span><span class="sxs-lookup"><span data-stu-id="74d3f-138">`y` is the minor version.</span></span>
- <span data-ttu-id="74d3f-139">`z`é a banda de recursos.</span><span class="sxs-lookup"><span data-stu-id="74d3f-139">`z` is the feature band.</span></span>
- <span data-ttu-id="74d3f-140">`nn`é a versão de patch.</span><span class="sxs-lookup"><span data-stu-id="74d3f-140">`nn` is the patch version.</span></span>

<span data-ttu-id="74d3f-141">A tabela a seguir mostra `rollForward` os valores possíveis para a chave:</span><span class="sxs-lookup"><span data-stu-id="74d3f-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="74d3f-142">Valor</span><span class="sxs-lookup"><span data-stu-id="74d3f-142">Value</span></span>         | <span data-ttu-id="74d3f-143">Comportamento</span><span class="sxs-lookup"><span data-stu-id="74d3f-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="74d3f-144">Usa a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-144">Uses the specified version.</span></span> <br> <span data-ttu-id="74d3f-145">Se não for encontrado, avança para o nível de patch mais recente.</span><span class="sxs-lookup"><span data-stu-id="74d3f-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="74d3f-146">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="74d3f-147">Este valor é o comportamento legado das versões anteriores do SDK.</span><span class="sxs-lookup"><span data-stu-id="74d3f-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="74d3f-148">Usa o nível de patch mais recente para a banda principal, menor e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="74d3f-149">Se não for encontrado, rola para a próxima faixa de recurso superior dentro do mesmo maior/menor e usa o nível de patch mais recente para essa banda de recursos.</span><span class="sxs-lookup"><span data-stu-id="74d3f-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="74d3f-150">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="74d3f-151">Usa o nível de patch mais recente para a banda principal, menor e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="74d3f-152">Se não for encontrado, rola para a próxima banda de recursos mais alto dentro da mesma versão principal/menor e usa o nível de patch mais recente para essa banda de recursos.</span><span class="sxs-lookup"><span data-stu-id="74d3f-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="74d3f-153">Se não for encontrado, rola para a próxima faixa menor mais alta e de recurso dentro do mesmo major e usa o nível de patch mais recente para essa banda de recursos.</span><span class="sxs-lookup"><span data-stu-id="74d3f-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="74d3f-154">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="74d3f-155">Usa o nível de patch mais recente para a banda principal, menor e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="74d3f-156">Se não for encontrado, rola para a próxima banda de recursos mais alto dentro da mesma versão principal/menor e usa o nível de patch mais recente para essa banda de recursos.</span><span class="sxs-lookup"><span data-stu-id="74d3f-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="74d3f-157">Se não for encontrado, rola para a próxima faixa menor mais alta e de recurso dentro do mesmo major e usa o nível de patch mais recente para essa banda de recursos.</span><span class="sxs-lookup"><span data-stu-id="74d3f-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="74d3f-158">Se não for encontrado, rola para a próxima banda maior, menor e característica e usa o nível de patch mais recente para essa banda de recursos.</span><span class="sxs-lookup"><span data-stu-id="74d3f-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="74d3f-159">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="74d3f-160">Usa o nível de patch instalado mais recente que corresponde à faixa principal, menor e de recurso solicitada com um nível de patch e que é maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="74d3f-161">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="74d3f-162">Usa a faixa de recurso mais alta instalada e o nível de patch que corresponde ao maior e menor solicitado com uma faixa de recurso maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="74d3f-163">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="74d3f-164">Usa o menor mais alto instalado, banda de recurso e nível de patch que corresponde ao principal solicitado com um menor que é maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="74d3f-165">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="74d3f-166">Usa o SDK de núcleo .NET mais alto instalado com um maior que é maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="74d3f-167">Se não for encontrado, falhe.</span><span class="sxs-lookup"><span data-stu-id="74d3f-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="74d3f-168">Não rola para a frente.</span><span class="sxs-lookup"><span data-stu-id="74d3f-168">Doesn't roll forward.</span></span> <span data-ttu-id="74d3f-169">Correspondência exata necessária.</span><span class="sxs-lookup"><span data-stu-id="74d3f-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="74d3f-170">Exemplos</span><span class="sxs-lookup"><span data-stu-id="74d3f-170">Examples</span></span>

<span data-ttu-id="74d3f-171">O exemplo a seguir mostra como não usar versões de pré-lançamento:</span><span class="sxs-lookup"><span data-stu-id="74d3f-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="74d3f-172">O exemplo a seguir mostra como usar a versão mais alta instalada que é maior ou igual à versão especificada:</span><span class="sxs-lookup"><span data-stu-id="74d3f-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="74d3f-173">O exemplo a seguir mostra como usar a versão exata especificada:</span><span class="sxs-lookup"><span data-stu-id="74d3f-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="74d3f-174">O exemplo a seguir mostra como usar a última faixa de recurso e a versão de patch instalada de uma versão específica principal e menor:</span><span class="sxs-lookup"><span data-stu-id="74d3f-174">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="74d3f-175">O exemplo a seguir mostra como usar a versão de patch mais alta instalada de uma versão específica (no formulário, 3.1.1xx):</span><span class="sxs-lookup"><span data-stu-id="74d3f-175">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="74d3f-176">global.json e CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="74d3f-176">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="74d3f-177">É útil saber quais versões SDK estão instaladas em sua máquina para definir uma no arquivo *global.json.*</span><span class="sxs-lookup"><span data-stu-id="74d3f-177">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="74d3f-178">Para obter mais informações sobre como fazer isso, consulte [Como verificar se o .NET Core já está instalado](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="74d3f-178">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="74d3f-179">Para instalar versões adicionais do .NET Core SDK na máquina, visite a página [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="74d3f-179">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="74d3f-180">Você pode criar um novo arquivo *global.json* no diretório atual executando o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="74d3f-180">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="74d3f-181">Regras de correspondência</span><span class="sxs-lookup"><span data-stu-id="74d3f-181">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="74d3f-182">As regras de correspondência `dotnet.exe` são regidas pelo ponto de entrada, que é comum em todos os tempos de execução instalados do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d3f-182">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="74d3f-183">As regras de correspondência para a versão mais recente instalada do .NET Core Runtime são usadas quando você tem vários tempos de execução instalados lado a lado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-183">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="74d3f-184">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="74d3f-184">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="74d3f-185">A partir do .NET Core 3.0, as seguintes regras se aplicam ao determinar qual versão do SDK usar:</span><span class="sxs-lookup"><span data-stu-id="74d3f-185">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="74d3f-186">Se nenhum arquivo *global.json* for encontrado ou *o global.json* não `allowPrerelease` especificar uma versão SDK nem um valor, `rollForward` `latestMajor`a versão sDK mais alta será usada (equivalente à configuração de ).</span><span class="sxs-lookup"><span data-stu-id="74d3f-186">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="74d3f-187">Se as versões sdk de `dotnet` pré-lançamento são consideradas depende de como está sendo invocada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-187">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="74d3f-188">Se você **não** está no Visual Studio, as versões de pré-lançamento são consideradas.</span><span class="sxs-lookup"><span data-stu-id="74d3f-188">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="74d3f-189">Se você estiver no Visual Studio, ele usa o status de pré-lançamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-189">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="74d3f-190">Ou seja, se você estiver usando uma versão preview do Visual Studio ou definir as visualizações de uso da opção **.NET Core SDK** (em **Recursos** > de**visualização\*\*\*\*do ambiente** > **de ferramentas),** > as versões de pré-lançamento são consideradas; caso contrário, apenas versões de versão são consideradas.</span><span class="sxs-lookup"><span data-stu-id="74d3f-190">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="74d3f-191">Se for encontrado um arquivo *global.json* que não especifique `allowPrerelease` uma versão do SDK, mas especificar um `rollForward` `latestMajor`valor, a versão sDK mais alta instalada será usada (equivalente à configuração de ).</span><span class="sxs-lookup"><span data-stu-id="74d3f-191">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="74d3f-192">Se a versão mais recente do SDK pode ser `allowPrerelease`lançada ou pré-lançamento depende do valor de .</span><span class="sxs-lookup"><span data-stu-id="74d3f-192">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="74d3f-193">`true`indica que as versões de pré-lançamento são consideradas; `false` indica que apenas versões de versão são consideradas.</span><span class="sxs-lookup"><span data-stu-id="74d3f-193">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="74d3f-194">Se um arquivo *global.json* for encontrado e ele especificar uma versão SDK:</span><span class="sxs-lookup"><span data-stu-id="74d3f-194">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="74d3f-195">Se `rollFoward` nenhum valor for `latestPatch` definido, `rollForward` ele usará como política padrão.</span><span class="sxs-lookup"><span data-stu-id="74d3f-195">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="74d3f-196">Caso contrário, verifique cada valor e seu comportamento na seção [rollForward.](#rollforward)</span><span class="sxs-lookup"><span data-stu-id="74d3f-196">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="74d3f-197">Se as versões de pré-lançamento `allowPrerelease` são consideradas e qual é o comportamento padrão quando não está definido é descrito na seção [permitirPré-lançamento.](#allowprerelease)</span><span class="sxs-lookup"><span data-stu-id="74d3f-197">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="74d3f-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="74d3f-198">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="74d3f-199">No .NET Core 2.x SDK, as seguintes regras se aplicam ao determinar qual versão do SDK usar:</span><span class="sxs-lookup"><span data-stu-id="74d3f-199">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="74d3f-200">Se não for encontrado nenhum arquivo *global.json* ou se *global.json* não especificar uma versão do SDK, a última versão do SDK instalada será usada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-200">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="74d3f-201">A versão mais recente do SDK pode ser lançada ou pré-lançada - o número mais alto da versão ganha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-201">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="74d3f-202">Se o *global.json* especificar uma versão do SDK:</span><span class="sxs-lookup"><span data-stu-id="74d3f-202">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="74d3f-203">Se a versão do SDK especificada for encontrada no computador, a versão exata será usada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-203">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="74d3f-204">Se a versão do SDK especificada não for encontrada no computador, a **versão de patch** do SDK mais recente instalada dessa versão será usada.</span><span class="sxs-lookup"><span data-stu-id="74d3f-204">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="74d3f-205">A versão mais recente do **patch** sdk instalada pode ser lançada ou pré-lançamento - o número mais alto da versão ganha.</span><span class="sxs-lookup"><span data-stu-id="74d3f-205">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="74d3f-206">No .NET Core 2.1 e nas versões posteriores, as **versões de patch** inferiores à **versão de patch** especificada são ignoradas na seleção do SDK.</span><span class="sxs-lookup"><span data-stu-id="74d3f-206">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="74d3f-207">Se a versão do SDK especificada e uma **versão de patch** adequada do SDK não forem encontradas, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="74d3f-207">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="74d3f-208">A versão SDK é composta pelas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="74d3f-208">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="74d3f-209">A **versão de recursos** do SDK do .NET Core é representada pelo primeiro dígito (`x`) na última parte do número (`xyz`) para versões do SDK 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="74d3f-209">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="74d3f-210">Em geral, o SDK do .NET Core tem um ciclo de versão mais rápido que o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d3f-210">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="74d3f-211">A **versão de patch** é definida pelos dois últimos dígitos (`yz`) na última parte do número (`xyz`) do SDK versões 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="74d3f-211">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="74d3f-212">Por exemplo, se você especificar `2.1.300` como a versão do SDK, a seleção de SDK localizará até a `2.1.399` mas a `2.1.400` não será considerada uma versão de patch para `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="74d3f-212">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="74d3f-213">As versões do SDK do .NET Core `2.1.100` até `2.1.201` foram lançadas durante a transição entre os esquemas de número de versão e não lidam corretamente com a notação `xyz`.</span><span class="sxs-lookup"><span data-stu-id="74d3f-213">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="74d3f-214">Se você especificar essas versões no arquivo *global.json*, será altamente recomendado verificar se as versões especificadas estão nos computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="74d3f-214">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="74d3f-215">Solucionar problemas de construção de avisos</span><span class="sxs-lookup"><span data-stu-id="74d3f-215">Troubleshoot build warnings</span></span>

* <span data-ttu-id="74d3f-216">O seguinte aviso indica que seu projeto foi compilado usando uma versão de pré-lançamento do .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="74d3f-216">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="74d3f-217">Você está trabalhando com uma versão prévia do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74d3f-217">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="74d3f-218">Você pode definir a versão do SDK por meio de um arquivo global.json no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="74d3f-218">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="74d3f-219">Mais <https://go.microsoft.com/fwlink/?linkid=869452>em .</span><span class="sxs-lookup"><span data-stu-id="74d3f-219">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="74d3f-220">As versões do SDK do .NET Core têm um histórico e o compromisso de manter a alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="74d3f-220">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="74d3f-221">No entanto, se você não quiser usar uma versão de pré-lançamento, verifique as diferentes estratégias que você pode usar com o .NET Core 3.0 SDK ou uma versão posterior na seção [allowPrerelease.](#allowprerelease)</span><span class="sxs-lookup"><span data-stu-id="74d3f-221">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="74d3f-222">Para máquinas que nunca tiveram um .NET Core 3.0 ou um Runtime ou SDK superior instalado, você precisa criar um arquivo *global.json* e especificar a versão exata que deseja usar.</span><span class="sxs-lookup"><span data-stu-id="74d3f-222">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="74d3f-223">O aviso a seguir indica que seu projeto tem como alvo o EF Core 1.0 ou 1.1, que não é compatível com o .NET Core 2.1 SDK e versões posteriores:</span><span class="sxs-lookup"><span data-stu-id="74d3f-223">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="74d3f-224">O projeto de inicialização '{startupProject}' é direcionado à estrutura '.NETCoreApp' versão '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="74d3f-224">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="74d3f-225">Essa versão das ferramentas de linha de comando do .NET do Entity Framework Core são compatíveis apenas com a versão 2.0 ou superiores.</span><span class="sxs-lookup"><span data-stu-id="74d3f-225">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="74d3f-226">Para obter informações sobre o uso <https://go.microsoft.com/fwlink/?linkid=871254>de versões mais antigas das ferramentas, consulte .</span><span class="sxs-lookup"><span data-stu-id="74d3f-226">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="74d3f-227">A partir do SDK do .NET Core 2.1 (versão 2.1.300), o comando `dotnet ef` vem incluído no SDK.</span><span class="sxs-lookup"><span data-stu-id="74d3f-227">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="74d3f-228">Para compilar seu projeto, instale o .NET Core 2.0 SDK (versão 2.1.201) ou anteriormente em sua máquina e defina a versão sdk desejada usando o arquivo *global.json.*</span><span class="sxs-lookup"><span data-stu-id="74d3f-228">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="74d3f-229">Para saber mais sobre o comando `dotnet ef`, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="74d3f-229">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="74d3f-230">Confira também</span><span class="sxs-lookup"><span data-stu-id="74d3f-230">See also</span></span>

- [<span data-ttu-id="74d3f-231">Como os SDKs de projeto são resolvidos</span><span class="sxs-lookup"><span data-stu-id="74d3f-231">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
