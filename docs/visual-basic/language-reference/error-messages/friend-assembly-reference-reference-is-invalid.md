---
title: "Referência de assembly Friend &lt;referência&gt; é inválido"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="cc96f-102">Referência de assembly Friend &lt;referência&gt; é inválido</span><span class="sxs-lookup"><span data-stu-id="cc96f-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="cc96f-103">Referência de assembly Friend \<referência > é inválido.</span><span class="sxs-lookup"><span data-stu-id="cc96f-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="cc96f-104">O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="cc96f-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="cc96f-105">O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="cc96f-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="cc96f-106">**ID do erro:** BC31535</span><span class="sxs-lookup"><span data-stu-id="cc96f-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc96f-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cc96f-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc96f-108">Determine a chave pública do assembly friend com nome forte.</span><span class="sxs-lookup"><span data-stu-id="cc96f-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="cc96f-109">Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo usando o `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="cc96f-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc96f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc96f-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="cc96f-111">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="cc96f-111">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [<span data-ttu-id="cc96f-112">Como criar assemblies amigáveis assinados</span><span class="sxs-lookup"><span data-stu-id="cc96f-112">How to: Create Signed Friend Assemblies</span></span>](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
