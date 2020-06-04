---
title: "'<methodname>' tem várias definições com assinaturas idênticas"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 3b397711cc2fb1fd0c1dfd76899b162ab5fc1542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397227"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="88a40-102">'\<methodname>' tem várias definições com assinaturas idênticas</span><span class="sxs-lookup"><span data-stu-id="88a40-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="88a40-103">Uma `Function` `Sub` declaração de procedimento or usa o nome de procedimento idêntico e a lista de argumentos como uma declaração anterior.</span><span class="sxs-lookup"><span data-stu-id="88a40-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="88a40-104">Uma causa possível é uma tentativa de sobrecarregar o procedimento original.</span><span class="sxs-lookup"><span data-stu-id="88a40-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="88a40-105">Os procedimentos sobrecarregados devem ter diferentes listas de argumentos.</span><span class="sxs-lookup"><span data-stu-id="88a40-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="88a40-106">**ID do erro:** BC30269</span><span class="sxs-lookup"><span data-stu-id="88a40-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="88a40-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="88a40-107">To correct this error</span></span>  
  
- <span data-ttu-id="88a40-108">Altere o nome do procedimento ou a lista de argumentos ou remova a declaração duplicada.</span><span class="sxs-lookup"><span data-stu-id="88a40-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a40-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="88a40-109">See also</span></span>

- [<span data-ttu-id="88a40-110">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="88a40-110">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="88a40-111">Considerações sobre procedimentos de sobrecarga</span><span class="sxs-lookup"><span data-stu-id="88a40-111">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
