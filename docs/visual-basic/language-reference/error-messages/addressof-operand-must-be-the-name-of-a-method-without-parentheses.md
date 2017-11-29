---
title: "&#39; AddressOf &#39; operando deve ser o nome de um método (sem parênteses)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords: BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="9478f-102">&#39; AddressOf &#39; operando deve ser o nome de um método (sem parênteses)</span><span class="sxs-lookup"><span data-stu-id="9478f-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="9478f-103">O `AddressOf` operador cria uma instância de delegado de procedimento que faz referência a um procedimento específico.</span><span class="sxs-lookup"><span data-stu-id="9478f-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="9478f-104">A sintaxe é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="9478f-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="9478f-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="9478f-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="9478f-106">Você inseriu o seguinte argumento entre parênteses `AddressOf`, onde nenhuma é necessária.</span><span class="sxs-lookup"><span data-stu-id="9478f-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="9478f-107">**ID do erro:** BC30577</span><span class="sxs-lookup"><span data-stu-id="9478f-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9478f-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9478f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="9478f-109">Remova os parênteses que delimitam o seguinte argumento `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="9478f-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="9478f-110">Verifique se que o argumento é um nome de método.</span><span class="sxs-lookup"><span data-stu-id="9478f-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9478f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9478f-111">See Also</span></span>  
 [<span data-ttu-id="9478f-112">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="9478f-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="9478f-113">Delegados</span><span class="sxs-lookup"><span data-stu-id="9478f-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
