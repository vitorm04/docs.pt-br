---
title: A instrução não pode finalizar um bloco fora de uma instrução 'If' de linha
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 4fd7577accd0b312ee1e3d2d990d256514d5f5f6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161329"
---
# <a name="bc32005-statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="3c984-102">BC32005: a instrução não pode encerrar um bloco fora de uma instrução ' If ' de linha</span><span class="sxs-lookup"><span data-stu-id="3c984-102">BC32005: Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="3c984-103">Uma `If` instrução de linha única contém várias instruções separadas por dois-pontos (:), uma das quais é uma `End` instrução para um bloco de controle fora da linha única `If` .</span><span class="sxs-lookup"><span data-stu-id="3c984-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="3c984-104">`If`Instruções de linha única não usam a `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="3c984-104">Single-line `If` statements do not use the `End If` statement.</span></span>

 <span data-ttu-id="3c984-105">**ID do erro:** BC32005</span><span class="sxs-lookup"><span data-stu-id="3c984-105">**Error ID:** BC32005</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3c984-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3c984-106">To correct this error</span></span>

- <span data-ttu-id="3c984-107">Mova a instrução de linha única para `If` fora do bloco de controle que contém a `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="3c984-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c984-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="3c984-108">See also</span></span>

- [<span data-ttu-id="3c984-109">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="3c984-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
