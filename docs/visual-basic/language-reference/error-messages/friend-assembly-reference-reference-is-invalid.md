---
title: A referência de assembly amigável <reference> é inválida.
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 0c1526e32ddc64cb4124c6f8205d58deef911dd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802459"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="58323-102">Referência de assembly Friend \<referência > é inválido</span><span class="sxs-lookup"><span data-stu-id="58323-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="58323-103">Referência de assembly Friend \<referência > é inválido.</span><span class="sxs-lookup"><span data-stu-id="58323-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="58323-104">O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="58323-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="58323-105">O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="58323-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="58323-106">**ID do erro:** BC31535</span><span class="sxs-lookup"><span data-stu-id="58323-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="58323-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="58323-107">To correct this error</span></span>  
  
1. <span data-ttu-id="58323-108">Determine a chave pública para o assembly de nome forte amigo.</span><span class="sxs-lookup"><span data-stu-id="58323-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="58323-109">Incluir a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> construtor de atributo usando o `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="58323-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58323-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58323-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="58323-111">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="58323-111">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
