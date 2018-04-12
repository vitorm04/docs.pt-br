---
title: Variável &#39; &lt;variablename&gt;&#39; oculta uma variável em um bloco delimitador
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="e7ecd-102">Variável &#39; &lt;variablename&gt;&#39; oculta uma variável em um bloco delimitador</span><span class="sxs-lookup"><span data-stu-id="e7ecd-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="e7ecd-103">Uma variável incluída em um bloco tem o mesmo nome que outra variável local.</span><span class="sxs-lookup"><span data-stu-id="e7ecd-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="e7ecd-104">**ID do erro:** BC30616</span><span class="sxs-lookup"><span data-stu-id="e7ecd-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7ecd-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e7ecd-105">To correct this error</span></span>  
  
-   <span data-ttu-id="e7ecd-106">Renomear a variável no bloco do anexo para que não seja o mesmo que todas as outras variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="e7ecd-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="e7ecd-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e7ecd-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="e7ecd-108">Uma causa comum para esse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e7ecd-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="e7ecd-109">Se esse for o caso, o nome de `Catch` variável de bloco `ex` em vez de `e`.</span><span class="sxs-lookup"><span data-stu-id="e7ecd-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="e7ecd-110">Outra origem comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloco em um separado `Catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="e7ecd-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="e7ecd-111">Para corrigir isso, declare a variável de fora de `Try...Catch...Finally` estrutura.</span><span class="sxs-lookup"><span data-stu-id="e7ecd-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ecd-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7ecd-112">See Also</span></span>  
 [<span data-ttu-id="e7ecd-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="e7ecd-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="e7ecd-114">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="e7ecd-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
