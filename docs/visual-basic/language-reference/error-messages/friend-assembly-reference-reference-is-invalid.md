---
title: "Referência de assembly Friend &lt;referência&gt; é inválido"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="29229-102">Referência de assembly Friend &lt;referência&gt; é inválido</span><span class="sxs-lookup"><span data-stu-id="29229-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="29229-103">Referência de assembly Friend \<referência > é inválido.</span><span class="sxs-lookup"><span data-stu-id="29229-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="29229-104">O nome forte assinado em assemblies deve especificar uma chave pública em suas declarações InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="29229-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="29229-105">O nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo identifica um assembly de nome forte, mas ele não inclui um `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="29229-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="29229-106">**ID do erro:** BC31535</span><span class="sxs-lookup"><span data-stu-id="29229-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29229-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="29229-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="29229-108">Determine a chave pública do assembly friend com nome forte.</span><span class="sxs-lookup"><span data-stu-id="29229-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="29229-109">Inclua a chave pública como parte do nome do assembly passado para o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> o construtor de atributo usando o `PublicKey` atributo.</span><span class="sxs-lookup"><span data-stu-id="29229-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29229-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29229-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="29229-111">Assemblies Amigáveis</span><span class="sxs-lookup"><span data-stu-id="29229-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

