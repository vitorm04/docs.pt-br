---
title: Fim de instrução esperado
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 36883989fe5aa0b5c70aa9ab1f7c991fab99e778
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163123"
---
# <a name="bc30205-end-of-statement-expected"></a><span data-ttu-id="3663f-102">BC30205: fim da instrução esperada</span><span class="sxs-lookup"><span data-stu-id="3663f-102">BC30205: End of statement expected</span></span>

<span data-ttu-id="3663f-103">A instrução está sintaticamente concluída, mas um elemento de programação adicional segue o elemento que conclui a instrução.</span><span class="sxs-lookup"><span data-stu-id="3663f-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="3663f-104">Um terminador de linha é necessário no final de cada instrução.</span><span class="sxs-lookup"><span data-stu-id="3663f-104">A line terminator is required at the end of every statement.</span></span>

 <span data-ttu-id="3663f-105">Um terminador de linha divide os caracteres de um Visual Basic arquivo de origem em linhas.</span><span class="sxs-lookup"><span data-stu-id="3663f-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="3663f-106">Exemplos de terminadores de linha são o caractere de retorno de carro Unicode (&HD), o caractere de alimentação Unicode (&HA) e o caractere de retorno de carro Unicode seguido pelo caractere de alimentação de linha Unicode.</span><span class="sxs-lookup"><span data-stu-id="3663f-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="3663f-107">Para obter mais informações sobre terminadores de linha, consulte a [especificação da linguagem Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="3663f-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>

 <span data-ttu-id="3663f-108">**ID do erro:** BC30205</span><span class="sxs-lookup"><span data-stu-id="3663f-108">**Error ID:** BC30205</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3663f-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3663f-109">To correct this error</span></span>

1. <span data-ttu-id="3663f-110">Verifique se duas instruções diferentes foram acidentalmente colocadas na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="3663f-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>

2. <span data-ttu-id="3663f-111">Insira um terminador de linha após o elemento que conclui a instrução.</span><span class="sxs-lookup"><span data-stu-id="3663f-111">Insert a line terminator after the element that completes the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="3663f-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="3663f-112">See also</span></span>

- [<span data-ttu-id="3663f-113">Como: Quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="3663f-113">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="3663f-114">Instruções</span><span class="sxs-lookup"><span data-stu-id="3663f-114">Statements</span></span>](../../programming-guide/language-features/statements.md)
