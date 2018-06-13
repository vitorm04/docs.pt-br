---
title: '&#39;&lt;MethodName&gt; &#39; tem várias definições com assinaturas idênticas'
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 059d152cf9c3fae77ab53a4a9248b36d99614c8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593724"
---
# <a name="39ltmethodnamegt39-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="cc68f-102">&#39;&lt;MethodName&gt; &#39; tem várias definições com assinaturas idênticas</span><span class="sxs-lookup"><span data-stu-id="cc68f-102">&#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures</span></span>
<span data-ttu-id="cc68f-103">Um `Function` ou `Sub` declaração de procedimento usa a lista de nome e o argumento de procedimento idêntica de uma declaração anterior.</span><span class="sxs-lookup"><span data-stu-id="cc68f-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="cc68f-104">Uma possível causa é uma tentativa para sobrecarregar o procedimento original.</span><span class="sxs-lookup"><span data-stu-id="cc68f-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="cc68f-105">Procedimentos sobrecarregados devem ter listas diferentes de argumentos.</span><span class="sxs-lookup"><span data-stu-id="cc68f-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="cc68f-106">**ID do erro:** BC30269</span><span class="sxs-lookup"><span data-stu-id="cc68f-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc68f-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cc68f-107">To correct this error</span></span>  
  
-   <span data-ttu-id="cc68f-108">Alterar o nome do procedimento ou a lista de argumentos, ou remova a declaração duplicada.</span><span class="sxs-lookup"><span data-stu-id="cc68f-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc68f-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc68f-109">See Also</span></span>  
 [<span data-ttu-id="cc68f-110">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="cc68f-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="cc68f-111">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="cc68f-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
