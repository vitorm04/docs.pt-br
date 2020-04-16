---
title: dotnet nuget comando fonte de atualização
description: O comando dotnet nuget update source atualiza uma fonte existente em seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463485"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="5653f-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="5653f-103">dotnet nuget update source</span></span>

<span data-ttu-id="5653f-104">**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5653f-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5653f-105">Nome</span><span class="sxs-lookup"><span data-stu-id="5653f-105">Name</span></span>

<span data-ttu-id="5653f-106">`dotnet nuget update source`- Atualize uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="5653f-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5653f-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5653f-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="5653f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5653f-108">Description</span></span>

<span data-ttu-id="5653f-109">O `dotnet nuget update source` comando atualiza uma fonte existente em seus arquivos de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="5653f-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="5653f-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="5653f-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="5653f-111">Nome da fonte.</span><span class="sxs-lookup"><span data-stu-id="5653f-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="5653f-112">Opções</span><span class="sxs-lookup"><span data-stu-id="5653f-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="5653f-113">O arquivo de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="5653f-113">The NuGet configuration file.</span></span> <span data-ttu-id="5653f-114">Se especificado, apenas as configurações deste arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="5653f-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="5653f-115">Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="5653f-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="5653f-116">Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="5653f-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="5653f-117">Senha a ser usada ao se conectar a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="5653f-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="5653f-118">Caminho para a fonte do pacote.</span><span class="sxs-lookup"><span data-stu-id="5653f-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="5653f-119">Permite armazenar credenciais de origem de pacote portátil desabilitando a criptografia de senha.</span><span class="sxs-lookup"><span data-stu-id="5653f-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="5653f-120">Nome de usuário a ser usado ao se conectar a uma fonte autenticada.</span><span class="sxs-lookup"><span data-stu-id="5653f-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="5653f-121">Lista separada por comma de tipos de autenticação válidos para esta fonte.</span><span class="sxs-lookup"><span data-stu-id="5653f-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="5653f-122">Defina `basic` isso para se o servidor anunciar NTLM ou Negociar e suas credenciais devem ser enviadas usando o mecanismo Básico, por exemplo, ao usar um PAT com o Azure DevOps Server no local.</span><span class="sxs-lookup"><span data-stu-id="5653f-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="5653f-123">Outros valores `negotiate` `kerberos`válidos incluem, `ntlm`e `digest`, mas esses valores são improváveis de serem úteis.</span><span class="sxs-lookup"><span data-stu-id="5653f-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="5653f-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5653f-124">Examples</span></span>

- <span data-ttu-id="5653f-125">Atualize uma fonte `mySource`com o nome de:</span><span class="sxs-lookup"><span data-stu-id="5653f-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="5653f-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="5653f-126">See also</span></span>

- [<span data-ttu-id="5653f-127">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="5653f-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="5653f-128">comando fontes (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="5653f-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
