---
title: comando dotnet NuGet Verify
description: O comando dotnet NuGet Verify verifica um pacote assinado.
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 6cb368e2b6c203f3774b4450c0831c5d6b2dc0e8
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957133"
---
# <a name="dotnet-nuget-verify"></a><span data-ttu-id="ef22d-103">verificação do NuGet do dotnet</span><span class="sxs-lookup"><span data-stu-id="ef22d-103">dotnet nuget verify</span></span>

<span data-ttu-id="ef22d-104">**Este artigo aplica-se a: ✔️ o** SDK do .NET 5.0.100-RC. 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ef22d-104">**This article applies to:** ✔️ .NET 5.0.100-rc.2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ef22d-105">Nome</span><span class="sxs-lookup"><span data-stu-id="ef22d-105">Name</span></span>

<span data-ttu-id="ef22d-106">`dotnet nuget verify` -Verifica um pacote NuGet assinado.</span><span class="sxs-lookup"><span data-stu-id="ef22d-106">`dotnet nuget verify` - Verifies a signed NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ef22d-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ef22d-107">Synopsis</span></span>

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a><span data-ttu-id="ef22d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef22d-108">Description</span></span>

<span data-ttu-id="ef22d-109">O `dotnet nuget verify` comando verifica um pacote NuGet assinado.</span><span class="sxs-lookup"><span data-stu-id="ef22d-109">The `dotnet nuget verify` command verifies a signed NuGet package.</span></span>

## <a name="arguments"></a><span data-ttu-id="ef22d-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="ef22d-110">Arguments</span></span>

- **`package-path(s)`**

  <span data-ttu-id="ef22d-111">Especifica o caminho de arquivo para os pacotes a serem verificados.</span><span class="sxs-lookup"><span data-stu-id="ef22d-111">Specifies the file path to the package(s) to be verified.</span></span> <span data-ttu-id="ef22d-112">Vários argumentos de posição podem ser passados para verificar vários pacotes.</span><span class="sxs-lookup"><span data-stu-id="ef22d-112">Multiple position arguments can be passed in to verify multiple packages.</span></span>

## <a name="options"></a><span data-ttu-id="ef22d-113">Opções</span><span class="sxs-lookup"><span data-stu-id="ef22d-113">Options</span></span>

- **`--all`**

  <span data-ttu-id="ef22d-114">Especifica que todas as verificações possíveis devem ser executadas nos pacotes.</span><span class="sxs-lookup"><span data-stu-id="ef22d-114">Specifies that all verifications possible should be performed on the package(s).</span></span> <span data-ttu-id="ef22d-115">Por padrão, somente `signatures` são verificados.</span><span class="sxs-lookup"><span data-stu-id="ef22d-115">By default, only `signatures` are verified.</span></span>

> [!NOTE]
> <span data-ttu-id="ef22d-116">Esse comando atualmente dá suporte apenas à `signature` verificação.</span><span class="sxs-lookup"><span data-stu-id="ef22d-116">This command currently supports only `signature` verification.</span></span>

- **`--certificate-fingerprint <FINGERPRINT>`**

  <span data-ttu-id="ef22d-117">Verifique se o certificado de signatário corresponde a uma das `SHA256` impressões digitais especificadas.</span><span class="sxs-lookup"><span data-stu-id="ef22d-117">Verify that the signer certificate matches with one of the specified `SHA256` fingerprints.</span></span> <span data-ttu-id="ef22d-118">Essa opção pode ser fornecida várias vezes para fornecer várias impressões digitais.</span><span class="sxs-lookup"><span data-stu-id="ef22d-118">This option can be supplied multiple times to provide multiple fingerprints.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ef22d-119">Define o nível de detalhamento do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ef22d-119">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="ef22d-120">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ef22d-120">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ef22d-121">O padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="ef22d-121">The default is `normal`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="ef22d-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="ef22d-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="ef22d-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ef22d-123">Examples</span></span>

- <span data-ttu-id="ef22d-124">Verifique *foo. nupkg*:</span><span class="sxs-lookup"><span data-stu-id="ef22d-124">Verify *foo.nupkg*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- <span data-ttu-id="ef22d-125">Verifique vários pacotes NuGet- *foo. nupkg* e *todos os arquivos. nupkg no diretório especificado*:</span><span class="sxs-lookup"><span data-stu-id="ef22d-125">Verify multiple NuGet packages - *foo.nupkg* and *all .nupkg files in the directory specified*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- <span data-ttu-id="ef22d-126">Verifique se a assinatura *foo. nupkg* corresponde à impressão digital do certificado especificado:</span><span class="sxs-lookup"><span data-stu-id="ef22d-126">Verify *foo.nupkg* signature matches with the specified certificate fingerprint:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- <span data-ttu-id="ef22d-127">Verifique se a assinatura *foo. nupkg* corresponde a uma das impressões digitais do certificado especificado:</span><span class="sxs-lookup"><span data-stu-id="ef22d-127">Verify *foo.nupkg* signature matches with one of the specified certificate fingerprints:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
