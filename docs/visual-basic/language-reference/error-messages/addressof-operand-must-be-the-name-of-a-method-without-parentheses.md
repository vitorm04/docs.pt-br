---
title: "O operando &quot;AddressOf&quot; deve ser o nome de um método (sem parênteses) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
dev_langs:
- VB
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
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
ms.openlocfilehash: c4ee57896b70d8af1a7bc245bdb45521c2442fea
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="b31a0-102">O operando 'AddressOf' deve ser o nome de um método (sem parênteses)</span><span class="sxs-lookup"><span data-stu-id="b31a0-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="b31a0-103">O `AddressOf` operador cria uma instância delegada de procedimento que faz referência a um procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="b31a0-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="b31a0-104">A sintaxe é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="b31a0-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="b31a0-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="b31a0-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="b31a0-106">Você inseriu o seguinte argumento entre parênteses `AddressOf`, onde nenhuma é necessária.</span><span class="sxs-lookup"><span data-stu-id="b31a0-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="b31a0-107">**ID do erro:** BC30577</span><span class="sxs-lookup"><span data-stu-id="b31a0-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b31a0-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b31a0-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="b31a0-109">Remova os parênteses que delimitam o seguinte argumento `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="b31a0-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="b31a0-110">Verifique se que o argumento é um nome de método.</span><span class="sxs-lookup"><span data-stu-id="b31a0-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b31a0-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b31a0-111">See Also</span></span>  
 <span data-ttu-id="b31a0-112">[Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b31a0-112">[AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="b31a0-113"> [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="b31a0-113"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span></span>
