---
title: O construtor '<name>' não pode se chamar
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 8459ee7fec6d761161a721c88ccdc88e513fc95f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324377"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="e723c-102">Construtor '\<nome >' não pode chamar a mesmo</span><span class="sxs-lookup"><span data-stu-id="e723c-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="e723c-103">Um `Sub New` procedimento em uma classe ou estrutura chama a mesmo.</span><span class="sxs-lookup"><span data-stu-id="e723c-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="e723c-104">A finalidade de um construtor é inicializar uma instância de uma classe ou estrutura quando ele é o primeiro é criado.</span><span class="sxs-lookup"><span data-stu-id="e723c-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="e723c-105">Uma classe ou estrutura pode ter vários construtores, desde que todos eles tenham listas de parâmetros diferentes.</span><span class="sxs-lookup"><span data-stu-id="e723c-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="e723c-106">Um construtor pode chamar outro construtor para executar sua funcionalidade, além de seu próprio.</span><span class="sxs-lookup"><span data-stu-id="e723c-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="e723c-107">Mas não faz sentido para um construtor chamar a mesmo e, na verdade ele resultaria em recursão infinita se permitido.</span><span class="sxs-lookup"><span data-stu-id="e723c-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="e723c-108">**ID do erro:** BC30298</span><span class="sxs-lookup"><span data-stu-id="e723c-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e723c-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e723c-109">To correct this error</span></span>  
  
1. <span data-ttu-id="e723c-110">Verifique a lista de parâmetros do construtor que está sendo chamado.</span><span class="sxs-lookup"><span data-stu-id="e723c-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="e723c-111">Ele deve ser diferente do construtor fazendo a chamada.</span><span class="sxs-lookup"><span data-stu-id="e723c-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="e723c-112">Se você não pretende chamar um construtor diferente, remova o `Sub New` chamar inteiramente.</span><span class="sxs-lookup"><span data-stu-id="e723c-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e723c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e723c-113">See also</span></span>

- [<span data-ttu-id="e723c-114">Tempo de vida do objeto: Como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="e723c-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
