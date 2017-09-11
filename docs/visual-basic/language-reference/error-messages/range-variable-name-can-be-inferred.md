---
title: "Nome de variável de intervalo pode ser inferido somente de um nome simple ou qualificado sem argumentos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
dev_langs:
- VB
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 556a43676b81a540c1b4f6fd329ca170ad4bc5f6
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="8a35f-102">O nome da variável de intervalo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos</span><span class="sxs-lookup"><span data-stu-id="8a35f-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="8a35f-103">Um elemento de programação que usa um ou mais argumentos está incluído em uma consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="8a35f-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="8a35f-104">O compilador é capaz de inferir a uma variável de intervalo do elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="8a35f-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="8a35f-105">**ID do erro:** BC36599</span><span class="sxs-lookup"><span data-stu-id="8a35f-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a35f-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8a35f-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="8a35f-107">Forneça um nome de variável explícito para o elemento de programação, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8a35f-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a35f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a35f-108">See Also</span></span>  
 <span data-ttu-id="8a35f-109">[Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="8a35f-109">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="8a35f-110"> [Cláusula Select](../../../visual-basic/language-reference/queries/select-clause.md)</span><span class="sxs-lookup"><span data-stu-id="8a35f-110"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)</span></span>
