---
title: "'<methodname>' tem várias definições com assinaturas idênticas"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: b884220053bbcec633c964a41892bc8df42f41c7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602436"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="80608-102">'\<methodname >' tem várias definições com assinaturas idênticas</span><span class="sxs-lookup"><span data-stu-id="80608-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="80608-103">Um `Function` ou `Sub` declaração de procedimento usa a lista de nome e o argumento de procedimento idêntica de uma declaração anterior.</span><span class="sxs-lookup"><span data-stu-id="80608-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="80608-104">Uma possível causa é uma tentativa de sobrecarregar o procedimento original.</span><span class="sxs-lookup"><span data-stu-id="80608-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="80608-105">Procedimentos sobrecarregados devem ter listas de argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="80608-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="80608-106">**ID do erro:** BC30269</span><span class="sxs-lookup"><span data-stu-id="80608-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="80608-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="80608-107">To correct this error</span></span>  
  
- <span data-ttu-id="80608-108">Alterar o nome do procedimento ou a lista de argumentos, ou remova a declaração duplicada.</span><span class="sxs-lookup"><span data-stu-id="80608-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80608-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80608-109">See also</span></span>

- [<span data-ttu-id="80608-110">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="80608-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="80608-111">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="80608-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
