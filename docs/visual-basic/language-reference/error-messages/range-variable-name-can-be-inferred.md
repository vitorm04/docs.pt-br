---
title: "O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords: BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c986fcf188482c526c53ddf3019cec5163d0b62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="f4e10-102">O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos</span><span class="sxs-lookup"><span data-stu-id="f4e10-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="f4e10-103">Um elemento de programação que usa um ou mais argumentos é incluído em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="f4e10-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="f4e10-104">O compilador é não é possível inferir uma variável de intervalo do elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="f4e10-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="f4e10-105">**ID do erro:** BC36599</span><span class="sxs-lookup"><span data-stu-id="f4e10-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4e10-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f4e10-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f4e10-107">Forneça um nome de variável explícito para o elemento de programação, como mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="f4e10-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4e10-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4e10-108">See Also</span></span>  
 [<span data-ttu-id="f4e10-109">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f4e10-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="f4e10-110">Cláusula Select</span><span class="sxs-lookup"><span data-stu-id="f4e10-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
