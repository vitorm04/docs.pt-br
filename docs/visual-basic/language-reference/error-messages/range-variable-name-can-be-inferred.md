---
title: O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6d082511d501b961b537317f0cb17bcd1c9370b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594615"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="659b5-102">O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos</span><span class="sxs-lookup"><span data-stu-id="659b5-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="659b5-103">Um elemento de programação que usa um ou mais argumentos é incluído em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="659b5-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="659b5-104">O compilador é não é possível inferir uma variável de intervalo do elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="659b5-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="659b5-105">**ID do erro:** BC36599</span><span class="sxs-lookup"><span data-stu-id="659b5-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="659b5-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="659b5-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="659b5-107">Forneça um nome de variável explícito para o elemento de programação, como mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="659b5-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="659b5-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="659b5-108">See Also</span></span>  
 [<span data-ttu-id="659b5-109">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="659b5-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="659b5-110">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="659b5-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
