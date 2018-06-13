---
title: Referência de assembly Friend &lt;referência&gt; é inválido
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587365"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="2b281-102">Referência de assembly Friend &lt;referência&gt; é inválido</span><span class="sxs-lookup"><span data-stu-id="2b281-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="2b281-103">Referência de assembly Friend \<referência > é inválido.</span><span class="sxs-lookup"><span data-stu-id="2b281-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="2b281-104">O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="2b281-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="2b281-105">O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="2b281-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="2b281-106">**ID do erro:** BC31535</span><span class="sxs-lookup"><span data-stu-id="2b281-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2b281-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2b281-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="2b281-108">Determine a chave pública do assembly friend com nome forte.</span><span class="sxs-lookup"><span data-stu-id="2b281-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="2b281-109">Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo usando o `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="2b281-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b281-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b281-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="2b281-111">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="2b281-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

