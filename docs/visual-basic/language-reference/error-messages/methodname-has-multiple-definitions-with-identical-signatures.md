---
title: "'<methodname>' tem várias definições com assinaturas idênticas"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 97113227591c40f302d3d1a08a4248a8199817bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285422"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="b6327-102">'\<methodname >' tem várias definições com assinaturas idênticas</span><span class="sxs-lookup"><span data-stu-id="b6327-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="b6327-103">Um `Function` ou `Sub` declaração de procedimento usa a lista de nome e o argumento de procedimento idêntica de uma declaração anterior.</span><span class="sxs-lookup"><span data-stu-id="b6327-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="b6327-104">Uma possível causa é uma tentativa de sobrecarregar o procedimento original.</span><span class="sxs-lookup"><span data-stu-id="b6327-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="b6327-105">Procedimentos sobrecarregados devem ter listas de argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b6327-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="b6327-106">**ID do erro:** BC30269</span><span class="sxs-lookup"><span data-stu-id="b6327-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6327-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b6327-107">To correct this error</span></span>  
  
-   <span data-ttu-id="b6327-108">Alterar o nome do procedimento ou a lista de argumentos, ou remova a declaração duplicada.</span><span class="sxs-lookup"><span data-stu-id="b6327-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6327-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6327-109">See also</span></span>
- [<span data-ttu-id="b6327-110">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="b6327-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="b6327-111">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="b6327-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
