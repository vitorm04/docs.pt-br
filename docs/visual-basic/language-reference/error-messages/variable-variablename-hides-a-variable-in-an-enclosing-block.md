---
title: A variável '<variablename>' oculta uma variável em bloco delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 408acaafd5e266266b5191313611b94b72a5c270
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161342"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="8c961-102">BC30616: a variável ' \<variablename> ' oculta uma variável em um bloco delimitador</span><span class="sxs-lookup"><span data-stu-id="8c961-102">BC30616: Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="8c961-103">Uma variável colocada em um bloco tem o mesmo nome que outra variável local.</span><span class="sxs-lookup"><span data-stu-id="8c961-103">A variable enclosed in a block has the same name as another local variable.</span></span>

 <span data-ttu-id="8c961-104">**ID do erro:** BC30616</span><span class="sxs-lookup"><span data-stu-id="8c961-104">**Error ID:** BC30616</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8c961-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8c961-105">To correct this error</span></span>

- <span data-ttu-id="8c961-106">Renomeie a variável no bloco incluído para que ela não seja a mesma que qualquer outra variável local.</span><span class="sxs-lookup"><span data-stu-id="8c961-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="8c961-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8c961-107">For example:</span></span>

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- <span data-ttu-id="8c961-108">Uma causa comum para esse erro é o uso de `Catch e As Exception` dentro de um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="8c961-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="8c961-109">Se esse for o caso, nomeie a `Catch` variável de bloco `ex` em vez de `e` .</span><span class="sxs-lookup"><span data-stu-id="8c961-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>

- <span data-ttu-id="8c961-110">Outra fonte comum desse erro é uma tentativa de acessar uma variável local declarada dentro de um `Try` bloco em um `Catch` bloco separado.</span><span class="sxs-lookup"><span data-stu-id="8c961-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="8c961-111">Para corrigir isso, declare a variável fora da `Try...Catch...Finally` estrutura.</span><span class="sxs-lookup"><span data-stu-id="8c961-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c961-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="8c961-112">See also</span></span>

- [<span data-ttu-id="8c961-113">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="8c961-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="8c961-114">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="8c961-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
