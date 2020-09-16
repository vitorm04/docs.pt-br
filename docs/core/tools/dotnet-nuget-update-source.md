---
title: comando de origem de atualização do NuGet do dotnet
description: O comando dotnet NuGet Update Source atualiza uma fonte existente nos arquivos de configuração do NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: a8658c78c095ad4b9272d97200e1d6466cbe658b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537848"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="c8d03-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="c8d03-103">dotnet nuget update source</span></span>

<span data-ttu-id="c8d03-104">**Este artigo aplica-se a:** ✔️ SDK 3.1.200 do .NET Core e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c8d03-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c8d03-105">Name</span><span class="sxs-lookup"><span data-stu-id="c8d03-105">Name</span></span>

<span data-ttu-id="c8d03-106">`dotnet nuget update source` -Atualizar uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8d03-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8d03-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c8d03-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="c8d03-108">Description</span><span class="sxs-lookup"><span data-stu-id="c8d03-108">Description</span></span>

<span data-ttu-id="c8d03-109">O `dotnet nuget update source` comando atualiza uma origem existente nos arquivos de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8d03-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="c8d03-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c8d03-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="c8d03-111">Nome da origem.</span><span class="sxs-lookup"><span data-stu-id="c8d03-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="c8d03-112">Opções</span><span class="sxs-lookup"><span data-stu-id="c8d03-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="c8d03-113">O arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8d03-113">The NuGet configuration file.</span></span> <span data-ttu-id="c8d03-114">Se especificado, somente as configurações desse arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="c8d03-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="c8d03-115">Se não for especificado, a hierarquia de arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="c8d03-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="c8d03-116">Para obter mais informações, consulte [configurações comuns do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="c8d03-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="c8d03-117">Senha a ser usada ao conectar-se a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="c8d03-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="c8d03-118">Caminho para a origem do pacote.</span><span class="sxs-lookup"><span data-stu-id="c8d03-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="c8d03-119">Habilita o armazenamento de credenciais de origem do pacote portátil desabilitando a criptografia de senha.</span><span class="sxs-lookup"><span data-stu-id="c8d03-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="c8d03-120">Nome de usuário a ser usado ao conectar a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="c8d03-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="c8d03-121">Lista separada por vírgulas de tipos de autenticação válidos para esta fonte.</span><span class="sxs-lookup"><span data-stu-id="c8d03-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="c8d03-122">Defina isso como `basic` se o servidor anunciar NTLM ou negociar e suas credenciais devem ser enviadas usando o mecanismo básico, por exemplo, ao usar uma Pat com Azure DevOps Server locais.</span><span class="sxs-lookup"><span data-stu-id="c8d03-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="c8d03-123">Outros valores válidos incluem `negotiate` , `kerberos` , `ntlm` e `digest` , mas esses valores são improvável de ser úteis.</span><span class="sxs-lookup"><span data-stu-id="c8d03-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="c8d03-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c8d03-124">Examples</span></span>

- <span data-ttu-id="c8d03-125">Atualize uma fonte com o nome de `mySource` :</span><span class="sxs-lookup"><span data-stu-id="c8d03-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="c8d03-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="c8d03-126">See also</span></span>

- [<span data-ttu-id="c8d03-127">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="c8d03-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="c8d03-128">comando Sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="c8d03-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
