---
title: A referência de assembly amigável <reference> é inválida.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: a42dd99ffaa06dce4823ce5d022fac02ae99c6bd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160705"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="d54e0-102">BC31535: a referência do assembly Friend \<reference> é inválida</span><span class="sxs-lookup"><span data-stu-id="d54e0-102">BC31535: Friend assembly reference \<reference> is invalid</span></span>

<span data-ttu-id="d54e0-103">A referência do assembly Friend \<reference> é inválida.</span><span class="sxs-lookup"><span data-stu-id="d54e0-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="d54e0-104">O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="d54e0-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>

 <span data-ttu-id="d54e0-105">O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo identifica um assembly de nome forte, mas não inclui um `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="d54e0-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>

 <span data-ttu-id="d54e0-106">**ID do erro:** BC31535</span><span class="sxs-lookup"><span data-stu-id="d54e0-106">**Error ID:** BC31535</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d54e0-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d54e0-107">To correct this error</span></span>

1. <span data-ttu-id="d54e0-108">Determine a chave pública para o assembly Friend de nome forte.</span><span class="sxs-lookup"><span data-stu-id="d54e0-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="d54e0-109">Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Construtor de atributo usando o `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="d54e0-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="d54e0-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="d54e0-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="d54e0-111">Assemblies amigáveis</span><span class="sxs-lookup"><span data-stu-id="d54e0-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
