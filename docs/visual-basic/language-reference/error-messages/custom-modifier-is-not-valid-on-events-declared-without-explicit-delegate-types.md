---
title: O modificador 'Custom' não é válido em eventos declarados sem tipos delegados explícitos
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: a2277e3778c2c252fd4b1eaeb033d549f041c15c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160627"
---
# <a name="bc31122-custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="c558a-102">BC31122: o modificador ' Custom ' não é válido em eventos declarados sem tipos delegados explícitos</span><span class="sxs-lookup"><span data-stu-id="c558a-102">BC31122: 'Custom' modifier is not valid on events declared without explicit delegate types</span></span>

<span data-ttu-id="c558a-103">Ao contrário de um evento não personalizado, uma `Custom Event` declaração requer uma `As` cláusula após o nome do evento que especifica explicitamente o tipo delegado para o evento.</span><span class="sxs-lookup"><span data-stu-id="c558a-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>

 <span data-ttu-id="c558a-104">Eventos não personalizados podem ser definidos com uma `As` cláusula e um tipo de delegado explícito, ou com uma lista de parâmetros imediatamente após o nome do evento.</span><span class="sxs-lookup"><span data-stu-id="c558a-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>

 <span data-ttu-id="c558a-105">**ID do erro:** BC31122</span><span class="sxs-lookup"><span data-stu-id="c558a-105">**Error ID:** BC31122</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c558a-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c558a-106">To correct this error</span></span>

1. <span data-ttu-id="c558a-107">Defina um delegado com a mesma lista de parâmetros que o evento personalizado.</span><span class="sxs-lookup"><span data-stu-id="c558a-107">Define a delegate with the same parameter list as the custom event.</span></span>

     <span data-ttu-id="c558a-108">Por exemplo, se o `Custom Event` foi definido por `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` , o delegado correspondente seria o seguinte.</span><span class="sxs-lookup"><span data-stu-id="c558a-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>

     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]

2. <span data-ttu-id="c558a-109">Substitua a lista de parâmetros do evento personalizado por uma `As` cláusula especificando o tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="c558a-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>

     <span data-ttu-id="c558a-110">Continuando com o exemplo, a `Custom Event` declaração seria reescrita da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="c558a-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>

     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]

## <a name="example"></a><span data-ttu-id="c558a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c558a-111">Example</span></span>

 <span data-ttu-id="c558a-112">Este exemplo declara um `Custom Event` e especifica a cláusula necessária `As` com um tipo delegate.</span><span class="sxs-lookup"><span data-stu-id="c558a-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>

 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]

## <a name="see-also"></a><span data-ttu-id="c558a-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="c558a-113">See also</span></span>

- [<span data-ttu-id="c558a-114">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="c558a-114">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="c558a-115">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="c558a-115">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="c558a-116">Eventos</span><span class="sxs-lookup"><span data-stu-id="c558a-116">Events</span></span>](../../programming-guide/language-features/events/index.md)
