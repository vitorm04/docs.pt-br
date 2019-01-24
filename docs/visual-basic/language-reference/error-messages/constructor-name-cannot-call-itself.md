---
title: Construtor &#39; &lt;nome&gt; &#39; não é possível chamar a mesmo
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 4a02277893147716098a3dcc327e221e0775d476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662719"
---
# <a name="constructor-39ltnamegt39-cannot-call-itself"></a><span data-ttu-id="225f9-102">Construtor &#39; &lt;nome&gt; &#39; não é possível chamar a mesmo</span><span class="sxs-lookup"><span data-stu-id="225f9-102">Constructor &#39;&lt;name&gt;&#39; cannot call itself</span></span>
<span data-ttu-id="225f9-103">Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.</span><span class="sxs-lookup"><span data-stu-id="225f9-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="225f9-104">A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ele é o primeiro é criado.</span><span class="sxs-lookup"><span data-stu-id="225f9-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="225f9-105">Uma classe ou estrutura pode ter vários construtores, desde que todos eles tenham listas de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="225f9-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="225f9-106">Um construtor pode chamar outro construtor para executar sua funcionalidade, além de seu próprio.</span><span class="sxs-lookup"><span data-stu-id="225f9-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="225f9-107">Mas não faz sentido para um construtor chamar a mesmo e, na verdade ele resultaria em recursão infinita se permitido.</span><span class="sxs-lookup"><span data-stu-id="225f9-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="225f9-108">**ID do erro:** BC30298</span><span class="sxs-lookup"><span data-stu-id="225f9-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="225f9-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="225f9-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="225f9-110">Verifique a lista de parâmetros do construtor que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="225f9-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="225f9-111">Ele deve ser diferente do construtor fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="225f9-111">It should be different from that of the constructor making the call.</span></span>  
  
2.  <span data-ttu-id="225f9-112">Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.</span><span class="sxs-lookup"><span data-stu-id="225f9-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="225f9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="225f9-113">See also</span></span>
- [<span data-ttu-id="225f9-114">Tempo de vida do objeto: Como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="225f9-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
