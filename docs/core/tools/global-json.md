---
title: Visão geral do global.json
description: Saiba como usar o arquivo global.json para definir a versão do SDK do .NET Core ao executar comandos de CLI do .NET Core.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 8582c495be58e38ca19320f14e20f8c511a9c821
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920504"
---
# <a name="globaljson-overview"></a><span data-ttu-id="10623-103">Visão geral do global.json</span><span class="sxs-lookup"><span data-stu-id="10623-103">global.json overview</span></span>

<span data-ttu-id="10623-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="10623-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="10623-105">O arquivo *global.json* permite que você defina qual versão do SDK do .NET Core é usada ao executar comandos de CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10623-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="10623-106">A seleção do SDK do .NET Core não depende da especificação do runtime ao qual o projeto é direcionado.</span><span class="sxs-lookup"><span data-stu-id="10623-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="10623-107">A versão SDK do .NET Core indica quais versões do CLI do .NET Core são usadas.</span><span class="sxs-lookup"><span data-stu-id="10623-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="10623-108">Em geral, você deseja usar a versão mais recente das ferramentas do SDK, portanto, nenhum arquivo *global. JSON* é necessário.</span><span class="sxs-lookup"><span data-stu-id="10623-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="10623-109">Em alguns cenários avançados, talvez você queira controlar a versão das ferramentas do SDK, e este artigo explica como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="10623-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="10623-110">Para obter mais informações de como especificar o runtime nesse caso, confira [Estruturas de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="10623-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="10623-111">O SDK do .NET Core procura um arquivo *global.json* no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="10623-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="10623-112">Esquema do global.json</span><span class="sxs-lookup"><span data-stu-id="10623-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="10623-113">sdk</span><span class="sxs-lookup"><span data-stu-id="10623-113">sdk</span></span>

<span data-ttu-id="10623-114">Tipo: `object`</span><span class="sxs-lookup"><span data-stu-id="10623-114">Type: `object`</span></span>

<span data-ttu-id="10623-115">Especifica as informações sobre o SDK do .NET Core a ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="10623-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="10623-116">versão</span><span class="sxs-lookup"><span data-stu-id="10623-116">version</span></span>

- <span data-ttu-id="10623-117">Tipo: `string`</span><span class="sxs-lookup"><span data-stu-id="10623-117">Type: `string`</span></span>

- <span data-ttu-id="10623-118">Disponível desde: SDK do .NET Core 1,0.</span><span class="sxs-lookup"><span data-stu-id="10623-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="10623-119">A versão do SDK do .NET Core a ser usada.</span><span class="sxs-lookup"><span data-stu-id="10623-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="10623-120">Este campo:</span><span class="sxs-lookup"><span data-stu-id="10623-120">This field:</span></span>

- <span data-ttu-id="10623-121">Não tem suporte a curinga, ou seja, o número de versão completo deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="10623-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="10623-122">Não dá suporte para intervalos de versão.</span><span class="sxs-lookup"><span data-stu-id="10623-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="10623-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="10623-123">allowPrerelease</span></span>

- <span data-ttu-id="10623-124">Tipo: `boolean`</span><span class="sxs-lookup"><span data-stu-id="10623-124">Type: `boolean`</span></span>

- <span data-ttu-id="10623-125">Disponível desde: SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="10623-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="10623-126">Indica se o resolvedor do SDK deve considerar versões de pré-lançamento ao selecionar a versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="10623-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="10623-127">Se você não definir esse valor explicitamente, o valor padrão dependerá do fato de você estar executando a partir do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="10623-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="10623-128">Se você **não** estiver no Visual Studio, o valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="10623-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="10623-129">Se você estiver no Visual Studio, ele usará o status de pré-lançamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="10623-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="10623-130">Ou seja, se você estiver usando uma versão prévia do Visual Studio ou se definir a opção **usar visualizações da SDK do .NET Core** (em **ferramentas** > **Opções** > **ambiente** > **recursos de visualização**), o valor padrão será `true`; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="10623-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="10623-131">Avanço</span><span class="sxs-lookup"><span data-stu-id="10623-131">rollForward</span></span>

- <span data-ttu-id="10623-132">Tipo: `string`</span><span class="sxs-lookup"><span data-stu-id="10623-132">Type: `string`</span></span>

- <span data-ttu-id="10623-133">Disponível desde: SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="10623-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="10623-134">A política de roll-forward a ser usada ao selecionar uma versão do SDK, seja como um fallback quando uma versão específica do SDK estiver ausente ou como uma diretiva para usar uma versão superior.</span><span class="sxs-lookup"><span data-stu-id="10623-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="10623-135">Uma [versão](#version) deve ser especificada com um valor `rollForward`, a menos que você esteja definindo-a como `latestMajor`.</span><span class="sxs-lookup"><span data-stu-id="10623-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="10623-136">Para entender as políticas disponíveis e seu comportamento, considere as seguintes definições para uma versão do SDK no formato `x.y.znn`:</span><span class="sxs-lookup"><span data-stu-id="10623-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="10623-137">`x` é a versão principal.</span><span class="sxs-lookup"><span data-stu-id="10623-137">`x` is the major version.</span></span>
- <span data-ttu-id="10623-138">`y` é a versão secundária.</span><span class="sxs-lookup"><span data-stu-id="10623-138">`y` is the minor version.</span></span>
- <span data-ttu-id="10623-139">`z` é a faixa de recursos.</span><span class="sxs-lookup"><span data-stu-id="10623-139">`z` is the feature band.</span></span>
- <span data-ttu-id="10623-140">`nn` é a versão do patch.</span><span class="sxs-lookup"><span data-stu-id="10623-140">`nn` is the patch version.</span></span>

<span data-ttu-id="10623-141">A tabela a seguir mostra os valores possíveis para a chave de `rollForward`:</span><span class="sxs-lookup"><span data-stu-id="10623-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="10623-142">Value</span><span class="sxs-lookup"><span data-stu-id="10623-142">Value</span></span>         | <span data-ttu-id="10623-143">Comportamento</span><span class="sxs-lookup"><span data-stu-id="10623-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="10623-144">Usa a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="10623-144">Uses the specified version.</span></span> <br> <span data-ttu-id="10623-145">Se não for encontrado, roll forward para o último nível de patch.</span><span class="sxs-lookup"><span data-stu-id="10623-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="10623-146">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="10623-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="10623-147">Esse valor é o comportamento herdado das versões anteriores do SDK.</span><span class="sxs-lookup"><span data-stu-id="10623-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="10623-148">Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="10623-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="10623-149">Se não for encontrado, roll forward para a próxima faixa de recursos mais alta dentro do mesmo principal/secundário e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="10623-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="10623-150">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="10623-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="10623-151">Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="10623-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="10623-152">Se não for encontrado, roll forward para a próxima faixa de recursos mais alta na mesma versão principal/secundária e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="10623-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="10623-153">Se não for encontrado, roll forward para a próxima faixa secundária e de recurso na mesma principal e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="10623-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="10623-154">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="10623-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="10623-155">Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="10623-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="10623-156">Se não for encontrado, roll forward para a próxima faixa de recursos mais alta na mesma versão principal/secundária e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="10623-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="10623-157">Se não for encontrado, roll forward para a próxima faixa secundária e de recurso na mesma principal e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="10623-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="10623-158">Se não for encontrado, rola para a próxima faixa mais alta, secundária e de recurso e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="10623-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="10623-159">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="10623-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="10623-160">Usa o nível de patch mais recente instalado que corresponde à faixa principal, secundária e de recursos solicitada com um nível de patch e maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="10623-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="10623-161">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="10623-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="10623-162">Usa a faixa de recursos e o nível de patch mais alto instalados que coincidem com o principal e o secundário solicitados com uma faixa de recursos maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="10623-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="10623-163">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="10623-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="10623-164">Usa a maior versão instalada, a faixa de recursos e o nível de patch que corresponde à principal solicitada com um secundário que é maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="10623-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="10623-165">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="10623-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="10623-166">Usa o SDK do .NET Core mais alto instalado com uma grande maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="10623-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="10623-167">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="10623-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="10623-168">Não rola para frente.</span><span class="sxs-lookup"><span data-stu-id="10623-168">Doesn't roll forward.</span></span> <span data-ttu-id="10623-169">Correspondência exata necessária.</span><span class="sxs-lookup"><span data-stu-id="10623-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="10623-170">Exemplos</span><span class="sxs-lookup"><span data-stu-id="10623-170">Examples</span></span>

<span data-ttu-id="10623-171">O exemplo a seguir mostra como não usar versões de pré-lançamento:</span><span class="sxs-lookup"><span data-stu-id="10623-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="10623-172">O exemplo a seguir mostra como usar a versão mais recente instalada que é maior ou igual à versão especificada:</span><span class="sxs-lookup"><span data-stu-id="10623-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="10623-173">O exemplo a seguir mostra como usar a versão especificada exata:</span><span class="sxs-lookup"><span data-stu-id="10623-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="10623-174">O exemplo a seguir mostra como usar a versão de patch mais alta instalada de uma versão específica (no formato 3.1.1 XX):</span><span class="sxs-lookup"><span data-stu-id="10623-174">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="10623-175">global.json e CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="10623-175">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="10623-176">É útil saber quais versões do SDK estão instaladas em seu computador para definir uma no arquivo *global. JSON* .</span><span class="sxs-lookup"><span data-stu-id="10623-176">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="10623-177">Para obter mais informações sobre como fazer isso, consulte [como verificar se o .NET Core já está instalado](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="10623-177">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="10623-178">Para instalar versões adicionais do SDK do .NET Core em seu computador, visite a página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="10623-178">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="10623-179">Você pode criar um novo arquivo *global.json* no diretório atual executando o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="10623-179">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="10623-180">Regras de correspondência</span><span class="sxs-lookup"><span data-stu-id="10623-180">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="10623-181">As regras de correspondência são governadas pelo ponto de entrada de `dotnet.exe`, que é comum em todos os tempos de execução instalados do .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="10623-181">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="10623-182">As regras de correspondência para a versão mais recente instalada do tempo de execução do .NET Core são usadas quando você tem vários tempos de execução instalados lado a lado.</span><span class="sxs-lookup"><span data-stu-id="10623-182">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3xtabnetcore3x"></a>[<span data-ttu-id="10623-183">.NET Core 3. x</span><span class="sxs-lookup"><span data-stu-id="10623-183">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="10623-184">A partir do .NET Core 3,0, as seguintes regras se aplicam ao determinar qual versão do SDK usar:</span><span class="sxs-lookup"><span data-stu-id="10623-184">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="10623-185">Se nenhum arquivo *global. JSON* for encontrado ou *global. JSON* não especificar uma versão do sdk nem um valor `allowPrerelease`, a versão mais recente do SDK instalada será usada (equivalente a definir `rollForward` como `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="10623-185">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="10623-186">Se as versões de pré-lançamento do SDK são consideradas depende de como `dotnet` está sendo invocada.</span><span class="sxs-lookup"><span data-stu-id="10623-186">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="10623-187">Se você **não** estiver no Visual Studio, as versões de pré-lançamento serão consideradas.</span><span class="sxs-lookup"><span data-stu-id="10623-187">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="10623-188">Se você estiver no Visual Studio, ele usará o status de pré-lançamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="10623-188">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="10623-189">Ou seja, se você estiver usando uma versão prévia do Visual Studio ou se definir a opção **usar visualizações da SDK do .NET Core** (em **ferramentas** > **Opções** > **ambiente** > **recursos de visualização**), as versões de pré-lançamento serão consideradas; caso contrário, apenas versões de lançamento serão consideradas.</span><span class="sxs-lookup"><span data-stu-id="10623-189">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="10623-190">Se um arquivo *global. JSON* for encontrado e não especificar uma versão do SDK, mas especificar um valor `allowPrerelease`, a versão mais recente do SDK instalada será usada (equivalente a definir `rollForward` como `latestMajor`).</span><span class="sxs-lookup"><span data-stu-id="10623-190">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="10623-191">Se a versão mais recente do SDK pode ser Release ou pré-lançamento depende do valor de `allowPrerelease`.</span><span class="sxs-lookup"><span data-stu-id="10623-191">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="10623-192">`true` indica que as versões de pré-lançamento são consideradas; `false` indica que apenas versões de lançamento são consideradas.</span><span class="sxs-lookup"><span data-stu-id="10623-192">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="10623-193">Se um arquivo *global. JSON* for encontrado e ele especificar uma versão do SDK:</span><span class="sxs-lookup"><span data-stu-id="10623-193">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="10623-194">Se nenhum valor de `rollFoward` for definido, ele usará `latestPatch` como a política de `rollForward` padrão.</span><span class="sxs-lookup"><span data-stu-id="10623-194">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="10623-195">Caso contrário, verifique cada valor e seu comportamento na seção [avanço](#rollforward) .</span><span class="sxs-lookup"><span data-stu-id="10623-195">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="10623-196">Se as versões de pré-lançamento são consideradas e qual é o comportamento padrão quando `allowPrerelease` não está definido é descrito na seção [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="10623-196">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="10623-197">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="10623-197">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="10623-198">No SDK do .NET Core 2. x, as seguintes regras se aplicam ao determinar qual versão do SDK usar:</span><span class="sxs-lookup"><span data-stu-id="10623-198">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="10623-199">Se não for encontrado nenhum arquivo *global.json* ou se *global.json* não especificar uma versão do SDK, a última versão do SDK instalada será usada.</span><span class="sxs-lookup"><span data-stu-id="10623-199">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="10623-200">A versão mais recente do SDK pode ser Release ou pré-lançamento-o número de versão mais alto vence.</span><span class="sxs-lookup"><span data-stu-id="10623-200">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="10623-201">Se o *global.json* especificar uma versão do SDK:</span><span class="sxs-lookup"><span data-stu-id="10623-201">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="10623-202">Se a versão do SDK especificada for encontrada no computador, a versão exata será usada.</span><span class="sxs-lookup"><span data-stu-id="10623-202">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="10623-203">Se a versão do SDK especificada não for encontrada no computador, a **versão de patch** do SDK mais recente instalada dessa versão será usada.</span><span class="sxs-lookup"><span data-stu-id="10623-203">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="10623-204">A versão mais recente do **patch** do SDK instalado pode ser Release ou pré-lançamento-o número de versão mais alto vence.</span><span class="sxs-lookup"><span data-stu-id="10623-204">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="10623-205">No .NET Core 2.1 e nas versões posteriores, as **versões de patch** inferiores à **versão de patch** especificada são ignoradas na seleção do SDK.</span><span class="sxs-lookup"><span data-stu-id="10623-205">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="10623-206">Se a versão do SDK especificada e uma **versão de patch** adequada do SDK não forem encontradas, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="10623-206">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="10623-207">A versão do SDK é composta pelas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="10623-207">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="10623-208">A **versão de recursos** do SDK do .NET Core é representada pelo primeiro dígito (`x`) na última parte do número (`xyz`) para versões do SDK 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="10623-208">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="10623-209">Em geral, o SDK do .NET Core tem um ciclo de versão mais rápido que o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10623-209">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="10623-210">A **versão de patch** é definida pelos dois últimos dígitos (`yz`) na última parte do número (`xyz`) do SDK versões 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="10623-210">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="10623-211">Por exemplo, se você especificar `2.1.300` como a versão do SDK, a seleção de SDK localizará até a `2.1.399` mas a `2.1.400` não será considerada uma versão de patch para `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="10623-211">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="10623-212">As versões do SDK do .NET Core `2.1.100` até `2.1.201` foram lançadas durante a transição entre os esquemas de número de versão e não lidam corretamente com a notação `xyz`.</span><span class="sxs-lookup"><span data-stu-id="10623-212">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="10623-213">Se você especificar essas versões no arquivo *global.json*, será altamente recomendado verificar se as versões especificadas estão nos computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="10623-213">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="10623-214">Solucionando problemas de aviso de build</span><span class="sxs-lookup"><span data-stu-id="10623-214">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="10623-215">Você está trabalhando com uma versão prévia do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10623-215">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="10623-216">Você pode definir a versão do SDK por meio de um arquivo global.json no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="10623-216">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="10623-217">Saiba mais em <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="10623-217">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="10623-218">Esse aviso indica que seu projeto foi compilado usando uma versão de pré-lançamento do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10623-218">This warning indicates that your project was compiled using a prerelease version of the .NET Core SDK.</span></span> <span data-ttu-id="10623-219">As versões do SDK do .NET Core têm um histórico e o compromisso de manter a alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="10623-219">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="10623-220">No entanto, se você não quiser usar uma versão de pré-lançamento, verifique as diferentes estratégias que você pode usar com o SDK do .NET Core 3,0 ou uma versão posterior na seção [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="10623-220">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="10623-221">Para computadores que nunca tinham um .NET Core 3,0 ou um tempo de execução ou SDK superior instalado, você precisa criar um arquivo *global. JSON* e especificar a versão exata que deseja usar.</span><span class="sxs-lookup"><span data-stu-id="10623-221">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

> [!WARNING]
> <span data-ttu-id="10623-222">O projeto de inicialização '{startupProject}' é direcionado à estrutura '.NETCoreApp' versão '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="10623-222">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="10623-223">Essa versão das ferramentas de linha de comando do .NET do Entity Framework Core são compatíveis apenas com a versão 2.0 ou superiores.</span><span class="sxs-lookup"><span data-stu-id="10623-223">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="10623-224">Para obter informações de como usar as versões mais antigas das ferramentas, confira <https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="10623-224">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="10623-225">A partir do SDK do .NET Core 2.1 (versão 2.1.300), o comando `dotnet ef` vem incluído no SDK.</span><span class="sxs-lookup"><span data-stu-id="10623-225">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="10623-226">Este aviso indica que o projeto é direcionado ao EF Core 1.0 ou 1.1, que não é compatível com o SDk do .NET Core 2.1 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="10623-226">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="10623-227">Para compilar seu projeto, instale o SDK do .NET Core 2.0 (versão 2.1.201) e versões anteriores em seu computador e defina a versão do SDK desejada usando o arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="10623-227">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="10623-228">Para saber mais sobre o comando `dotnet ef`, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="10623-228">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="10623-229">Veja também</span><span class="sxs-lookup"><span data-stu-id="10623-229">See also</span></span>

- [<span data-ttu-id="10623-230">Como os SDKs do projeto são resolvidos</span><span class="sxs-lookup"><span data-stu-id="10623-230">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
