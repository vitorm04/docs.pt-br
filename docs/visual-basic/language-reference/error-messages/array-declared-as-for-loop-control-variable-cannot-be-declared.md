---
title: "Matriz declarada como variável de controle de loop não pode ser declarada com um tamanho inicial | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
dev_langs:
- VB
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 13
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
ms.openlocfilehash: d3b1b7e5ba158e6bdc9838cc8b50db482ca97454
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="9a944-102">A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial</span><span class="sxs-lookup"><span data-stu-id="9a944-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="9a944-103">A `For Each` usa uma matriz como seu *elemento* variável de iteração mas inicializa essa matriz.</span><span class="sxs-lookup"><span data-stu-id="9a944-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="9a944-104">As instruções a seguir mostram como esse erro pode ser gerado.</span><span class="sxs-lookup"><span data-stu-id="9a944-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="9a944-105">A primeira `For Each` instrução é a maneira correta de acessar elementos de `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="9a944-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="9a944-106">O segundo `For Each` instrução gera esse erro.</span><span class="sxs-lookup"><span data-stu-id="9a944-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="9a944-107">**ID do erro:** BC32039</span><span class="sxs-lookup"><span data-stu-id="9a944-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a944-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9a944-108">To correct this error</span></span>  
  
-   <span data-ttu-id="9a944-109">Remova a inicialização da declaração do *elemento* variável de iteração.</span><span class="sxs-lookup"><span data-stu-id="9a944-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a944-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a944-110">See Also</span></span>  
 <span data-ttu-id="9a944-111">[Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9a944-111">[For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="9a944-112"> [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a944-112"> [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="9a944-113"> [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)</span><span class="sxs-lookup"><span data-stu-id="9a944-113"> [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)</span></span>
