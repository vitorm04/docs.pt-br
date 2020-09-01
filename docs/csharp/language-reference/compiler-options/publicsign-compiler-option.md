---
description: -publicsign (opções do compilador C#)
title: -publicsign (opções do compilador C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124806"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="e7b9a-103">-publicsign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="e7b9a-103">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="e7b9a-104">Essa opção faz com que o compilador aplique uma chave pública, mas, na verdade, não assina o assembly.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-104">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="e7b9a-105">A opção **-publicsign** também define um bit no assembly que informa o runtime que o arquivo realmente já está assinado.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-105">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7b9a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7b9a-106">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="e7b9a-107">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e7b9a-107">Arguments</span></span>

<span data-ttu-id="e7b9a-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-108">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7b9a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7b9a-109">Remarks</span></span>

<span data-ttu-id="e7b9a-110">A opção **-publicsign** requer o uso de [-keyfile](keyfile-compiler-option.md) ou [-keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="e7b9a-110">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="e7b9a-111">As opções **keyfile** ou **keycontainer** especificam a chave pública.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-111">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="e7b9a-112">As opções **-publicsign** e **-delaysign** são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-112">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="e7b9a-113">Às vezes chamada de "assinatura falsa" ou "assinatura de OSS", a assinatura pública inclui a chave pública em um assembly de saída e define o sinalizador "assinado", mas, na verdade, não assina o assembly com uma chave privada.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-113">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="e7b9a-114">Isso é útil para projetos de software livre em que as pessoas desejam criar assemblies compatíveis com os assemblies "totalmente assinados" lançados, mas não têm acesso à chave privada usada para assinar os assemblies.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-114">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="e7b9a-115">Como quase nenhum consumidor precisa verificar realmente se o assembly está totalmente assinado, esses assemblies criados publicamente podem ser usados em quase todos os cenários nos quais o assembly totalmente assinado seria usado.</span><span class="sxs-lookup"><span data-stu-id="e7b9a-115">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a><span data-ttu-id="e7b9a-116">Para definir essa opção de compilador em um arquivo csproj</span><span class="sxs-lookup"><span data-stu-id="e7b9a-116">To set this compiler option in a csproj file</span></span>

<span data-ttu-id="e7b9a-117">Abra o arquivo. csproj de um projeto e adicione o seguinte elemento:</span><span class="sxs-lookup"><span data-stu-id="e7b9a-117">Open the .csproj file for a project, and add the following element:</span></span>

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a><span data-ttu-id="e7b9a-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="e7b9a-118">See also</span></span>

- [<span data-ttu-id="e7b9a-119">Opção -delaysign do compilador C#</span><span class="sxs-lookup"><span data-stu-id="e7b9a-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="e7b9a-120">Opção -keyfile do compilador C#</span><span class="sxs-lookup"><span data-stu-id="e7b9a-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="e7b9a-121">Opção -keycontainer do compilador C#</span><span class="sxs-lookup"><span data-stu-id="e7b9a-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="e7b9a-122">Opções do compilador C#</span><span class="sxs-lookup"><span data-stu-id="e7b9a-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="e7b9a-123">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="e7b9a-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
