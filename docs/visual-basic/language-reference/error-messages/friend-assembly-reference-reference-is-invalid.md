---
title: Referência de assembly Friend &lt;referência&gt; é inválido
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: cdedcc18aa82f6efd8c52cdca5d915d7d78e269f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611924"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="81d43-102">Referência de assembly Friend &lt;referência&gt; é inválido</span><span class="sxs-lookup"><span data-stu-id="81d43-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="81d43-103">Referência de assembly Friend \<referência > é inválido.</span><span class="sxs-lookup"><span data-stu-id="81d43-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="81d43-104">O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="81d43-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="81d43-105">O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="81d43-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="81d43-106">**ID do erro:** BC31535</span><span class="sxs-lookup"><span data-stu-id="81d43-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="81d43-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="81d43-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="81d43-108">Determine a chave pública para o assembly de nome forte amigo.</span><span class="sxs-lookup"><span data-stu-id="81d43-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="81d43-109">Incluir a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> construtor de atributo usando o `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="81d43-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81d43-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81d43-110">See also</span></span>
- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="81d43-111">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="81d43-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


