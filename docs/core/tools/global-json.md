---
title: Visão geral do global.json
description: Saiba como usar o arquivo global.json para definir a versão do SDK do .NET Core ao executar comandos de CLI do .NET Core.
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 714e32ec841cee214f801de65bccf0041af66b0b
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281539"
---
# <a name="globaljson-overview"></a><span data-ttu-id="30520-103">Visão geral do global.json</span><span class="sxs-lookup"><span data-stu-id="30520-103">global.json overview</span></span>

<span data-ttu-id="30520-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="30520-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="30520-105">O arquivo *global.json* permite que você defina qual versão do SDK do .NET Core é usada ao executar comandos de CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30520-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="30520-106">A seleção do SDK do .NET Core não depende da especificação do runtime ao qual o projeto é direcionado.</span><span class="sxs-lookup"><span data-stu-id="30520-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="30520-107">A versão SDK do .NET Core indica quais versões do CLI do .NET Core são usadas.</span><span class="sxs-lookup"><span data-stu-id="30520-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="30520-108">Em geral, você deseja usar a versão mais recente das ferramentas do SDK, portanto, nenhum *global.jsno* arquivo é necessário.</span><span class="sxs-lookup"><span data-stu-id="30520-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="30520-109">Em alguns cenários avançados, talvez você queira controlar a versão das ferramentas do SDK, e este artigo explica como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="30520-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="30520-110">Para obter mais informações de como especificar o runtime nesse caso, confira [Estruturas de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="30520-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="30520-111">O SDK do .NET Core procura um arquivo *global.json* no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="30520-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="30520-112">Esquema do global.json</span><span class="sxs-lookup"><span data-stu-id="30520-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="30520-113">sdk</span><span class="sxs-lookup"><span data-stu-id="30520-113">sdk</span></span>

<span data-ttu-id="30520-114">Digite: `object`</span><span class="sxs-lookup"><span data-stu-id="30520-114">Type: `object`</span></span>

<span data-ttu-id="30520-115">Especifica as informações sobre o SDK do .NET Core a ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="30520-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="30520-116">version</span><span class="sxs-lookup"><span data-stu-id="30520-116">version</span></span>

- <span data-ttu-id="30520-117">Digite: `string`</span><span class="sxs-lookup"><span data-stu-id="30520-117">Type: `string`</span></span>

- <span data-ttu-id="30520-118">Disponível desde: SDK do .NET Core 1,0.</span><span class="sxs-lookup"><span data-stu-id="30520-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="30520-119">A versão do SDK do .NET Core a ser usada.</span><span class="sxs-lookup"><span data-stu-id="30520-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="30520-120">Este campo:</span><span class="sxs-lookup"><span data-stu-id="30520-120">This field:</span></span>

- <span data-ttu-id="30520-121">Não tem suporte a curinga, ou seja, o número de versão completo deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="30520-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="30520-122">Não dá suporte para intervalos de versão.</span><span class="sxs-lookup"><span data-stu-id="30520-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="30520-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="30520-123">allowPrerelease</span></span>

- <span data-ttu-id="30520-124">Digite: `boolean`</span><span class="sxs-lookup"><span data-stu-id="30520-124">Type: `boolean`</span></span>

- <span data-ttu-id="30520-125">Disponível desde: SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="30520-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="30520-126">Indica se o resolvedor do SDK deve considerar versões de pré-lançamento ao selecionar a versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="30520-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="30520-127">Se você não definir esse valor explicitamente, o valor padrão dependerá do fato de você estar executando a partir do Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="30520-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="30520-128">Se você **não** estiver no Visual Studio, o valor padrão será `true` .</span><span class="sxs-lookup"><span data-stu-id="30520-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="30520-129">Se você estiver no Visual Studio, ele usará o status de pré-lançamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="30520-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="30520-130">Ou seja, se você estiver usando uma versão de visualização do Visual Studio ou se definir a opção **usar visualizações da SDK do .NET Core** (em **ferramentas**  >  **Opções**  >  **Environment**  >  **recursos de visualização** do ambiente), o valor padrão será `true` ; caso contrário, `false` .</span><span class="sxs-lookup"><span data-stu-id="30520-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features** ), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="30520-131">Avanço</span><span class="sxs-lookup"><span data-stu-id="30520-131">rollForward</span></span>

- <span data-ttu-id="30520-132">Digite: `string`</span><span class="sxs-lookup"><span data-stu-id="30520-132">Type: `string`</span></span>

- <span data-ttu-id="30520-133">Disponível desde: SDK do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="30520-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="30520-134">A política de roll-forward a ser usada ao selecionar uma versão do SDK, seja como um fallback quando uma versão específica do SDK estiver ausente ou como uma diretiva para usar uma versão superior.</span><span class="sxs-lookup"><span data-stu-id="30520-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="30520-135">Uma [versão](#version) deve ser especificada com um `rollForward` valor, a menos que você esteja definindo-a como `latestMajor` .</span><span class="sxs-lookup"><span data-stu-id="30520-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>
<span data-ttu-id="30520-136">O comportamento de roll-forward padrão é determinado pelas [regras de correspondência](#matching-rules).</span><span class="sxs-lookup"><span data-stu-id="30520-136">The default roll forward behavior is determined by the [matching rules](#matching-rules).</span></span>

<span data-ttu-id="30520-137">Para entender as políticas disponíveis e seu comportamento, considere as seguintes definições para uma versão do SDK no formato `x.y.znn` :</span><span class="sxs-lookup"><span data-stu-id="30520-137">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="30520-138">`x` é a versão principal.</span><span class="sxs-lookup"><span data-stu-id="30520-138">`x` is the major version.</span></span>
- <span data-ttu-id="30520-139">`y` é a versão secundária.</span><span class="sxs-lookup"><span data-stu-id="30520-139">`y` is the minor version.</span></span>
- <span data-ttu-id="30520-140">`z` é a faixa de recursos.</span><span class="sxs-lookup"><span data-stu-id="30520-140">`z` is the feature band.</span></span>
- <span data-ttu-id="30520-141">`nn` é a versão do patch.</span><span class="sxs-lookup"><span data-stu-id="30520-141">`nn` is the patch version.</span></span>

<span data-ttu-id="30520-142">A tabela a seguir mostra os valores possíveis para a `rollForward` chave:</span><span class="sxs-lookup"><span data-stu-id="30520-142">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="30520-143">Valor</span><span class="sxs-lookup"><span data-stu-id="30520-143">Value</span></span>         | <span data-ttu-id="30520-144">Comportamento</span><span class="sxs-lookup"><span data-stu-id="30520-144">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="30520-145">Usa a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="30520-145">Uses the specified version.</span></span> <br> <span data-ttu-id="30520-146">Se não for encontrado, roll forward para o último nível de patch.</span><span class="sxs-lookup"><span data-stu-id="30520-146">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="30520-147">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="30520-147">If not found, fails.</span></span> <br><br> <span data-ttu-id="30520-148">Esse valor é o comportamento herdado das versões anteriores do SDK.</span><span class="sxs-lookup"><span data-stu-id="30520-148">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="30520-149">Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="30520-149">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="30520-150">Se não for encontrado, roll forward para a próxima faixa de recursos mais alta dentro do mesmo principal/secundário e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="30520-150">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="30520-151">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="30520-151">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="30520-152">Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="30520-152">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="30520-153">Se não for encontrado, roll forward para a próxima faixa de recursos mais alta na mesma versão principal/secundária e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="30520-153">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="30520-154">Se não for encontrado, roll forward para a próxima faixa secundária e de recurso na mesma principal e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="30520-154">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="30520-155">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="30520-155">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="30520-156">Usa o nível de patch mais recente para a faixa primária, secundária e de recurso especificada.</span><span class="sxs-lookup"><span data-stu-id="30520-156">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="30520-157">Se não for encontrado, roll forward para a próxima faixa de recursos mais alta na mesma versão principal/secundária e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="30520-157">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="30520-158">Se não for encontrado, roll forward para a próxima faixa secundária e de recurso na mesma principal e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="30520-158">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="30520-159">Se não for encontrado, rola para a próxima faixa mais alta, secundária e de recurso e usa o nível de patch mais recente para essa faixa de recurso.</span><span class="sxs-lookup"><span data-stu-id="30520-159">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="30520-160">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="30520-160">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="30520-161">Usa o nível de patch mais recente instalado que corresponde à faixa principal, secundária e de recursos solicitada com um nível de patch e maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="30520-161">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="30520-162">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="30520-162">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="30520-163">Usa a faixa de recursos e o nível de patch mais alto instalados que corresponde ao principal e secundário solicitados com uma faixa de recursos e um nível de patch que é maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="30520-163">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="30520-164">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="30520-164">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="30520-165">Usa a maior versão instalada, a faixa de recursos e o nível de patch que corresponde à principal solicitada com um nível secundário, de faixa de recursos e de patch que é maior ou igual ao valor especificado.</span><span class="sxs-lookup"><span data-stu-id="30520-165">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor, feature band, and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="30520-166">Se não for encontrado, falhará.</span><span class="sxs-lookup"><span data-stu-id="30520-166">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="30520-167">Usa o SDK do .NET Core mais alto instalado com uma versão maior ou igual à do valor especificado.</span><span class="sxs-lookup"><span data-stu-id="30520-167">Uses the highest installed .NET Core SDK with a version that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="30520-168">Se não for encontrado, falha.</span><span class="sxs-lookup"><span data-stu-id="30520-168">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="30520-169">Não rola para frente.</span><span class="sxs-lookup"><span data-stu-id="30520-169">Doesn't roll forward.</span></span> <span data-ttu-id="30520-170">Correspondência exata necessária.</span><span class="sxs-lookup"><span data-stu-id="30520-170">Exact match required.</span></span> |

### <a name="msbuild-sdks"></a><span data-ttu-id="30520-171">MSBuild-SDKs</span><span class="sxs-lookup"><span data-stu-id="30520-171">msbuild-sdks</span></span>

<span data-ttu-id="30520-172">Digite: `object`</span><span class="sxs-lookup"><span data-stu-id="30520-172">Type: `object`</span></span>

<span data-ttu-id="30520-173">Permite controlar a versão do SDK do projeto em um único lugar em vez de em cada projeto individual.</span><span class="sxs-lookup"><span data-stu-id="30520-173">Lets you control the project SDK version in one place rather than in each individual project.</span></span> <span data-ttu-id="30520-174">Para obter mais informações, consulte [como os SDKs do projeto são resolvidos](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span><span class="sxs-lookup"><span data-stu-id="30520-174">For more information, see [How project SDKs are resolved](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span></span>

## <a name="examples"></a><span data-ttu-id="30520-175">Exemplos</span><span class="sxs-lookup"><span data-stu-id="30520-175">Examples</span></span>

<span data-ttu-id="30520-176">O exemplo a seguir mostra como não usar versões de pré-lançamento:</span><span class="sxs-lookup"><span data-stu-id="30520-176">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="30520-177">O exemplo a seguir mostra como usar a versão mais recente instalada que é maior ou igual à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="30520-177">The following example shows how to use the highest version installed that is greater or equal than the specified version.</span></span> <span data-ttu-id="30520-178">O JSON mostrado não permite qualquer versão do SDK anterior à 2.2.200 e permite o 2.2.200 ou qualquer versão posterior, incluindo 3.0.xxx e 3.1.xxx.</span><span class="sxs-lookup"><span data-stu-id="30520-178">The JSON shown disallows any SDK version earlier than 2.2.200 and allows 2.2.200 or any later version, including 3.0.xxx and 3.1.xxx.</span></span>

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="30520-179">O exemplo a seguir mostra como usar a versão especificada exata:</span><span class="sxs-lookup"><span data-stu-id="30520-179">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="30520-180">O exemplo a seguir mostra como usar a faixa de recursos e a versão de patch mais recentes instalados de uma versão principal e secundária específica.</span><span class="sxs-lookup"><span data-stu-id="30520-180">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version.</span></span> <span data-ttu-id="30520-181">O JSON mostrado não permite qualquer versão do SDK anterior à 3.1.102 e permite o 3.1.102 ou qualquer versão 3.1.xxx posterior, como 3.1.103 ou 3.1.200.</span><span class="sxs-lookup"><span data-stu-id="30520-181">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.xxx version, such as 3.1.103 or 3.1.200.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="30520-182">O exemplo a seguir mostra como usar a versão de patch mais alta instalada de uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="30520-182">The following example shows how to use the highest patch version installed of a specific version.</span></span> <span data-ttu-id="30520-183">O JSON mostrado não permite qualquer versão do SDK anterior à 3.1.102 e permite 3.1.102 ou qualquer versão mais recente do 3.1.1 XX, como 3.1.103 ou 3.1.199.</span><span class="sxs-lookup"><span data-stu-id="30520-183">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.1xx version, such as 3.1.103 or 3.1.199.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="30520-184">global.json e CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="30520-184">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="30520-185">É útil saber quais versões do SDK estão instaladas em seu computador para definir uma na *global.jsno* arquivo.</span><span class="sxs-lookup"><span data-stu-id="30520-185">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="30520-186">Para obter mais informações sobre como fazer isso, consulte [como verificar se o .NET Core já está instalado](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="30520-186">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="30520-187">Para instalar versões adicionais do SDK do .NET Core em seu computador, visite a página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="30520-187">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="30520-188">Você pode criar um novo arquivo *global.json* no diretório atual executando o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="30520-188">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="30520-189">Regras de correspondência</span><span class="sxs-lookup"><span data-stu-id="30520-189">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="30520-190">As regras de correspondência são governadas pelo `dotnet.exe` ponto de entrada, que é comum em todos os tempos de execução instalados do .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="30520-190">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="30520-191">As regras de correspondência para a versão mais recente instalada do tempo de execução do .NET Core são usadas quando você tem vários tempos de execução instalados lado a lado ou se estiver usando um *global.jsno* arquivo.</span><span class="sxs-lookup"><span data-stu-id="30520-191">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side or if or you're using a *global.json* file.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="30520-192">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="30520-192">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="30520-193">A partir do .NET Core 3,0, as seguintes regras se aplicam ao determinar qual versão do SDK usar:</span><span class="sxs-lookup"><span data-stu-id="30520-193">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="30520-194">Se nenhum *global.jsno* arquivo for encontrado ou *global.jsem* não especificar uma versão do SDK nem um `allowPrerelease` valor, a versão mais recente do SDK será usada (equivalente a definir `rollForward` como `latestMajor` ).</span><span class="sxs-lookup"><span data-stu-id="30520-194">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="30520-195">Se as versões de pré-lançamento do SDK são consideradas depende de como o `dotnet` está sendo invocado.</span><span class="sxs-lookup"><span data-stu-id="30520-195">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="30520-196">Se você **não** estiver no Visual Studio, as versões de pré-lançamento serão consideradas.</span><span class="sxs-lookup"><span data-stu-id="30520-196">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="30520-197">Se você estiver no Visual Studio, ele usará o status de pré-lançamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="30520-197">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="30520-198">Ou seja, se você estiver usando uma versão prévia do Visual Studio ou se definir a opção **usar visualizações da SDK do .NET Core** (em **ferramentas**  >  **Opções**  >  recursos de visualização do **ambiente**  >  **Preview Features** ), as versões de pré-lançamento serão consideradas; caso contrário, apenas as versões de lançamento serão consideradas.</span><span class="sxs-lookup"><span data-stu-id="30520-198">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features** ), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="30520-199">Se um *global.jsno* arquivo for encontrado e não especificar uma versão do SDK, mas especificar um `allowPrerelease` valor, a versão mais recente do SDK instalada será usada (equivalente a definir `rollForward` como `latestMajor` ).</span><span class="sxs-lookup"><span data-stu-id="30520-199">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="30520-200">Se a versão mais recente do SDK pode ser Release ou pré-lançamento depende do valor de `allowPrerelease` .</span><span class="sxs-lookup"><span data-stu-id="30520-200">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="30520-201">`true` indica que as versões de pré-lançamento são consideradas; `false` indica que apenas versões de lançamento são consideradas.</span><span class="sxs-lookup"><span data-stu-id="30520-201">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="30520-202">Se um *global.jsno* arquivo for encontrado e ele especificar uma versão do SDK:</span><span class="sxs-lookup"><span data-stu-id="30520-202">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="30520-203">Se nenhum `rollForward` valor for definido, ele será usado `latestPatch` como a `rollForward` política padrão.</span><span class="sxs-lookup"><span data-stu-id="30520-203">If no `rollForward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="30520-204">Caso contrário, verifique cada valor e seu comportamento na seção [avanço](#rollforward) .</span><span class="sxs-lookup"><span data-stu-id="30520-204">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="30520-205">Se as versões de pré-lançamento são consideradas e qual é o comportamento padrão quando `allowPrerelease` não está definido, é descrito na seção [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="30520-205">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="30520-206">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="30520-206">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="30520-207">No SDK do .NET Core 2. x, as seguintes regras se aplicam ao determinar qual versão do SDK usar:</span><span class="sxs-lookup"><span data-stu-id="30520-207">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="30520-208">Se não for encontrado nenhum arquivo *global.json* ou se *global.json* não especificar uma versão do SDK, a última versão do SDK instalada será usada.</span><span class="sxs-lookup"><span data-stu-id="30520-208">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="30520-209">A versão mais recente do SDK pode ser Release ou pré-lançamento-o número de versão mais alto vence.</span><span class="sxs-lookup"><span data-stu-id="30520-209">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="30520-210">Se o *global.json* especificar uma versão do SDK:</span><span class="sxs-lookup"><span data-stu-id="30520-210">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="30520-211">Se a versão do SDK especificada for encontrada no computador, a versão exata será usada.</span><span class="sxs-lookup"><span data-stu-id="30520-211">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="30520-212">Se a versão do SDK especificada não for encontrada no computador, a **versão de patch** do SDK mais recente instalada dessa versão será usada.</span><span class="sxs-lookup"><span data-stu-id="30520-212">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="30520-213">A versão mais recente do **patch** do SDK instalado pode ser Release ou pré-lançamento-o número de versão mais alto vence.</span><span class="sxs-lookup"><span data-stu-id="30520-213">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="30520-214">No .NET Core 2.1 e nas versões posteriores, as **versões de patch** inferiores à **versão de patch** especificada são ignoradas na seleção do SDK.</span><span class="sxs-lookup"><span data-stu-id="30520-214">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="30520-215">Se a versão do SDK especificada e uma **versão de patch** adequada do SDK não forem encontradas, um erro será gerado.</span><span class="sxs-lookup"><span data-stu-id="30520-215">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="30520-216">A versão do SDK é composta pelas seguintes partes:</span><span class="sxs-lookup"><span data-stu-id="30520-216">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="30520-217">A **versão de recursos** do SDK do .NET Core é representada pelo primeiro dígito (`x`) na última parte do número (`xyz`) para versões do SDK 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="30520-217">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="30520-218">Em geral, o SDK do .NET Core tem um ciclo de versão mais rápido que o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30520-218">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="30520-219">A **versão de patch** é definida pelos dois últimos dígitos (`yz`) na última parte do número (`xyz`) do SDK versões 2.1.100 e superiores.</span><span class="sxs-lookup"><span data-stu-id="30520-219">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="30520-220">Por exemplo, se você especificar `2.1.300` como a versão do SDK, a seleção de SDK localizará até a `2.1.399` mas a `2.1.400` não será considerada uma versão de patch para `2.1.300`.</span><span class="sxs-lookup"><span data-stu-id="30520-220">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="30520-221">As versões do SDK do .NET Core `2.1.100` até `2.1.201` foram lançadas durante a transição entre os esquemas de número de versão e não lidam corretamente com a notação `xyz`.</span><span class="sxs-lookup"><span data-stu-id="30520-221">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="30520-222">Se você especificar essas versões no arquivo *global.json* , será altamente recomendado verificar se as versões especificadas estão nos computadores de destino.</span><span class="sxs-lookup"><span data-stu-id="30520-222">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="30520-223">Solucionar problemas de avisos de compilação</span><span class="sxs-lookup"><span data-stu-id="30520-223">Troubleshoot build warnings</span></span>

* <span data-ttu-id="30520-224">O seguinte aviso indica que seu projeto foi compilado usando uma versão de pré-lançamento do SDK do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="30520-224">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="30520-225">Você está trabalhando com uma versão prévia do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30520-225">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="30520-226">Você pode definir a versão do SDK por meio de um arquivo global.json no projeto atual.</span><span class="sxs-lookup"><span data-stu-id="30520-226">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="30520-227">Mais em <https://go.microsoft.com/fwlink/?linkid=869452> .</span><span class="sxs-lookup"><span data-stu-id="30520-227">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="30520-228">As versões do SDK do .NET Core têm um histórico e o compromisso de manter a alta qualidade.</span><span class="sxs-lookup"><span data-stu-id="30520-228">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="30520-229">No entanto, se você não quiser usar uma versão de pré-lançamento, verifique as diferentes estratégias que você pode usar com o SDK do .NET Core 3,0 ou uma versão posterior na seção [allowPrerelease](#allowprerelease) .</span><span class="sxs-lookup"><span data-stu-id="30520-229">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="30520-230">Para computadores que nunca tinham um .NET Core 3,0 ou um tempo de execução ou SDK superior instalado, você precisa criar um *global.jsno* arquivo e especificar a versão exata que deseja usar.</span><span class="sxs-lookup"><span data-stu-id="30520-230">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="30520-231">O aviso a seguir indica que seu projeto tem como alvo EF Core 1,0 ou 1,1, que não é compatível com o SDK do .NET Core 2,1 e versões posteriores:</span><span class="sxs-lookup"><span data-stu-id="30520-231">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="30520-232">O projeto de inicialização '{startupProject}' é direcionado à estrutura '.NETCoreApp' versão '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="30520-232">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="30520-233">Essa versão das ferramentas de linha de comando do .NET do Entity Framework Core são compatíveis apenas com a versão 2.0 ou superiores.</span><span class="sxs-lookup"><span data-stu-id="30520-233">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="30520-234">Para obter informações sobre como usar versões mais antigas das ferramentas, consulte <https://go.microsoft.com/fwlink/?linkid=871254> .</span><span class="sxs-lookup"><span data-stu-id="30520-234">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="30520-235">A partir do SDK do .NET Core 2.1 (versão 2.1.300), o comando `dotnet ef` vem incluído no SDK.</span><span class="sxs-lookup"><span data-stu-id="30520-235">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="30520-236">Para compilar seu projeto, instale o SDK do .NET Core 2,0 (versão 2.1.201) ou anterior em seu computador e defina a versão do SDK desejada usando o *global.jsno* arquivo.</span><span class="sxs-lookup"><span data-stu-id="30520-236">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="30520-237">Para saber mais sobre o comando `dotnet ef`, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="30520-237">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="30520-238">Veja também</span><span class="sxs-lookup"><span data-stu-id="30520-238">See also</span></span>

- [<span data-ttu-id="30520-239">Como os SDKs de projeto são resolvidos</span><span class="sxs-lookup"><span data-stu-id="30520-239">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
