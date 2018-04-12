---
title: '&#39; &lt;methodname&gt;&#39; tem várias definições com assinaturas idênticas'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1a71d51690d6318a559a94ac81de625289d7587d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39ltmethodnamegt39-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="e49b0-102">&#39; &lt;methodname&gt;&#39; tem várias definições com assinaturas idênticas</span><span class="sxs-lookup"><span data-stu-id="e49b0-102">&#39;&lt;methodname&gt;&#39; has multiple definitions with identical signatures</span></span>
<span data-ttu-id="e49b0-103">Um `Function` ou `Sub` declaração de procedimento usa a lista de nome e o argumento de procedimento idêntica de uma declaração anterior.</span><span class="sxs-lookup"><span data-stu-id="e49b0-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="e49b0-104">Uma possível causa é uma tentativa para sobrecarregar o procedimento original.</span><span class="sxs-lookup"><span data-stu-id="e49b0-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="e49b0-105">Procedimentos sobrecarregados devem ter listas diferentes de argumentos.</span><span class="sxs-lookup"><span data-stu-id="e49b0-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="e49b0-106">**ID do erro:** BC30269</span><span class="sxs-lookup"><span data-stu-id="e49b0-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e49b0-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e49b0-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e49b0-108">Alterar o nome do procedimento ou a lista de argumentos, ou remova a declaração duplicada.</span><span class="sxs-lookup"><span data-stu-id="e49b0-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49b0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e49b0-109">See Also</span></span>  
 [<span data-ttu-id="e49b0-110">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="e49b0-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="e49b0-111">Considerações sobre Procedimentos de Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="e49b0-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
