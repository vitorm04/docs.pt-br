---
title: -publicsign (opções do compilador C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: de7d9c98b0f279b52bc93711c5b986a2b2e57215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61662524"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="966a9-102">-publicsign (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="966a9-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="966a9-103">Essa opção faz com que o compilador aplique uma chave pública, mas, na verdade, não assina o assembly.</span><span class="sxs-lookup"><span data-stu-id="966a9-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="966a9-104">A opção **-publicsign** também define um bit no assembly que informa o runtime que o arquivo realmente já está assinado.</span><span class="sxs-lookup"><span data-stu-id="966a9-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="966a9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="966a9-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="966a9-106">Argumentos</span><span class="sxs-lookup"><span data-stu-id="966a9-106">Arguments</span></span>

<span data-ttu-id="966a9-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="966a9-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="966a9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="966a9-108">Remarks</span></span>

<span data-ttu-id="966a9-109">A opção **-publicsign** requer o uso de [-keyfile](keyfile-compiler-option.md) ou [-keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="966a9-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="966a9-110">As opções **keyfile** ou **keycontainer** especificam a chave pública.</span><span class="sxs-lookup"><span data-stu-id="966a9-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="966a9-111">As opções **-publicsign** e **-delaysign** são mutuamente exclusivas.</span><span class="sxs-lookup"><span data-stu-id="966a9-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="966a9-112">Às vezes chamada de "assinatura falsa" ou "assinatura de OSS", a assinatura pública inclui a chave pública em um assembly de saída e define o sinalizador "assinado", mas, na verdade, não assina o assembly com uma chave privada.</span><span class="sxs-lookup"><span data-stu-id="966a9-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="966a9-113">Isso é útil para projetos de software livre em que as pessoas desejam criar assemblies compatíveis com os assemblies "totalmente assinados" lançados, mas não têm acesso à chave privada usada para assinar os assemblies.</span><span class="sxs-lookup"><span data-stu-id="966a9-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="966a9-114">Como quase nenhum consumidor precisa verificar realmente se o assembly está totalmente assinado, esses assemblies criados publicamente podem ser usados em quase todos os cenários nos quais o assembly totalmente assinado seria usado.</span><span class="sxs-lookup"><span data-stu-id="966a9-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="966a9-115">Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="966a9-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="966a9-116">Abra a página **Propriedades** do projeto.</span><span class="sxs-lookup"><span data-stu-id="966a9-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="966a9-117">Modifique a propriedade **Apenas adiar a assinatura**.</span><span class="sxs-lookup"><span data-stu-id="966a9-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="966a9-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="966a9-118">See also</span></span>

- [<span data-ttu-id="966a9-119">Opção -delaysign do compilador C#</span><span class="sxs-lookup"><span data-stu-id="966a9-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="966a9-120">Opção -keyfile do compilador C#</span><span class="sxs-lookup"><span data-stu-id="966a9-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="966a9-121">Opção -keycontainer do compilador C#</span><span class="sxs-lookup"><span data-stu-id="966a9-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="966a9-122">C# Opções de compilador</span><span class="sxs-lookup"><span data-stu-id="966a9-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="966a9-123">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="966a9-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
