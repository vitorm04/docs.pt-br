---
title: Variável de &#39; &lt;variablename&gt; &#39; oculta uma variável em um bloco delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 23ec659535b71ee9af189f5c4fec0dec2bb1cd8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719424"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="9fd51-102">Variável de &#39; &lt;variablename&gt; &#39; oculta uma variável em um bloco delimitador</span><span class="sxs-lookup"><span data-stu-id="9fd51-102">Variable &#39;&lt;variablename&gt;&#39; hides a variable in an enclosing block</span></span>
<span data-ttu-id="9fd51-103">Uma variável incluída em um bloco tem o mesmo nome que outra variável local.</span><span class="sxs-lookup"><span data-stu-id="9fd51-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="9fd51-104">**ID do erro:** BC30616</span><span class="sxs-lookup"><span data-stu-id="9fd51-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9fd51-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9fd51-105">To correct this error</span></span>  
  
-   <span data-ttu-id="9fd51-106">Renomear a variável no bloco incluído para que não seja o mesmo que qualquer outra variável local.</span><span class="sxs-lookup"><span data-stu-id="9fd51-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="9fd51-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9fd51-107">For example:</span></span>  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   <span data-ttu-id="9fd51-108">Uma causa comum desse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="9fd51-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="9fd51-109">Se esse for o caso, o nome do `Catch` variável de bloco `ex` em vez de `e`.</span><span class="sxs-lookup"><span data-stu-id="9fd51-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
-   <span data-ttu-id="9fd51-110">Outra origem comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloco em um separado `Catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="9fd51-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="9fd51-111">Para corrigir isso, declare a variável de fora a `Try...Catch...Finally` estrutura.</span><span class="sxs-lookup"><span data-stu-id="9fd51-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd51-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fd51-112">See also</span></span>
- [<span data-ttu-id="9fd51-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="9fd51-113">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="9fd51-114">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="9fd51-114">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
