---
title: dotnet NuGet Adicionar comando de origem
description: O comando dotnet NuGet Add Source adiciona uma nova origem de pacote aos arquivos de configuração do NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b847d987de2d88cb3452d32d1bc84232a1e20b6e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537967"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="3974c-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="3974c-103">dotnet nuget add source</span></span>

<span data-ttu-id="3974c-104">**Este artigo aplica-se a:** ✔️ SDK 3.1.200 do .NET Core e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="3974c-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3974c-105">Name</span><span class="sxs-lookup"><span data-stu-id="3974c-105">Name</span></span>

<span data-ttu-id="3974c-106">`dotnet nuget add source` -Adicionar uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="3974c-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3974c-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="3974c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="3974c-108">Description</span><span class="sxs-lookup"><span data-stu-id="3974c-108">Description</span></span>

<span data-ttu-id="3974c-109">O `dotnet nuget add source` comando adiciona uma nova origem de pacote aos arquivos de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="3974c-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="3974c-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3974c-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="3974c-111">Caminho para a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="3974c-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="3974c-112">Opções</span><span class="sxs-lookup"><span data-stu-id="3974c-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="3974c-113">O arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="3974c-113">The NuGet configuration file.</span></span> <span data-ttu-id="3974c-114">Se especificado, somente as configurações desse arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="3974c-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="3974c-115">Se não for especificado, a hierarquia de arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="3974c-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="3974c-116">Para obter mais informações, consulte [configurações comuns do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="3974c-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="3974c-117">Nome da origem.</span><span class="sxs-lookup"><span data-stu-id="3974c-117">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="3974c-118">Senha a ser usada ao conectar-se a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="3974c-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="3974c-119">Habilita o armazenamento de credenciais de origem do pacote portátil desabilitando a criptografia de senha.</span><span class="sxs-lookup"><span data-stu-id="3974c-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="3974c-120">Nome de usuário a ser usado ao conectar a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="3974c-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="3974c-121">Lista separada por vírgulas de tipos de autenticação válidos para esta fonte.</span><span class="sxs-lookup"><span data-stu-id="3974c-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="3974c-122">Defina isso como `basic` se o servidor anunciar NTLM ou negociar e suas credenciais devem ser enviadas usando o mecanismo básico, por exemplo, ao usar uma Pat com Azure DevOps Server locais.</span><span class="sxs-lookup"><span data-stu-id="3974c-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="3974c-123">Outros valores válidos incluem `negotiate` , `kerberos` , `ntlm` e `digest` , mas esses valores são improvável de ser úteis.</span><span class="sxs-lookup"><span data-stu-id="3974c-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="3974c-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3974c-124">Examples</span></span>

- <span data-ttu-id="3974c-125">Adicionar `nuget.org` como uma fonte:</span><span class="sxs-lookup"><span data-stu-id="3974c-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="3974c-126">Adicionar `c:\packages` como uma fonte local:</span><span class="sxs-lookup"><span data-stu-id="3974c-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="3974c-127">Adicione uma fonte que precisa de autenticação:</span><span class="sxs-lookup"><span data-stu-id="3974c-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="3974c-128">Adicione uma fonte que precisa de autenticação (em seguida, instale o provedor de credenciais):</span><span class="sxs-lookup"><span data-stu-id="3974c-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="3974c-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="3974c-129">See also</span></span>

- [<span data-ttu-id="3974c-130">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="3974c-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="3974c-131">comando Sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="3974c-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
