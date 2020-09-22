---
title: A variável '<variablename>' oculta uma variável em bloco delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 04538be3431fb06518051db4378e986ea5711219
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875062"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="b3220-102">A variável '\<variablename>' oculta uma variável em bloco delimitador</span><span class="sxs-lookup"><span data-stu-id="b3220-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="b3220-103">Uma variável colocada em um bloco tem o mesmo nome que outra variável local.</span><span class="sxs-lookup"><span data-stu-id="b3220-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="b3220-104">**ID do erro:** BC30616</span><span class="sxs-lookup"><span data-stu-id="b3220-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3220-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b3220-105">To correct this error</span></span>  
  
- <span data-ttu-id="b3220-106">Renomeie a variável no bloco incluído para que ela não seja a mesma que qualquer outra variável local.</span><span class="sxs-lookup"><span data-stu-id="b3220-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="b3220-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b3220-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="b3220-108">Uma causa comum para esse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b3220-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="b3220-109">Se esse for o caso, nomeie a `Catch` variável de bloco `ex` em vez de `e` .</span><span class="sxs-lookup"><span data-stu-id="b3220-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="b3220-110">Outra fonte comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloco em um `Catch` bloco separado.</span><span class="sxs-lookup"><span data-stu-id="b3220-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="b3220-111">Para corrigir isso, declare a variável fora da `Try...Catch...Finally` estrutura.</span><span class="sxs-lookup"><span data-stu-id="b3220-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3220-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3220-112">See also</span></span>

- [<span data-ttu-id="b3220-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="b3220-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b3220-114">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="b3220-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
