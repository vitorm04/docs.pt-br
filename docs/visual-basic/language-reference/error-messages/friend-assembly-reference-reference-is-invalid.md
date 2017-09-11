---
title: "Referência de assembly Friend &lt;referência&gt; inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
dev_langs:
- VB
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: daf65d4372e633c68f75aa2624afab010048dff8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="40dc0-102">Referência de assembly Friend &lt;referência&gt; é inválido</span><span class="sxs-lookup"><span data-stu-id="40dc0-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="40dc0-103">Referência de assembly Friend \<referência > é inválido.</span><span class="sxs-lookup"><span data-stu-id="40dc0-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="40dc0-104">Assemblies assinados com nome forte devem especificar uma chave pública em suas declarações InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="40dc0-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="40dc0-105">O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>Construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="40dc0-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="40dc0-106">**ID do erro:** BC31535</span><span class="sxs-lookup"><span data-stu-id="40dc0-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40dc0-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="40dc0-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="40dc0-108">Determine a chave pública do assembly de nome forte amigo.</span><span class="sxs-lookup"><span data-stu-id="40dc0-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="40dc0-109">Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>Construtor de atributo usando o `PublicKey` atributo.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="40dc0-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40dc0-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40dc0-110">See Also</span></span>  
 <span data-ttu-id="40dc0-111"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="40dc0-111"><xref:System.Reflection.AssemblyName></span></span>   
<span data-ttu-id="40dc0-112"> [Assemblies amigáveis](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055) </span><span class="sxs-lookup"><span data-stu-id="40dc0-112"> [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055) </span></span>  
<span data-ttu-id="40dc0-113"> [Como criar assemblies amigáveis assinados](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)</span><span class="sxs-lookup"><span data-stu-id="40dc0-113"> [How to: Create Signed Friend Assemblies](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)</span></span>
