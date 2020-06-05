---
title: Declaração esperada
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 237622d0dc6c57f66d402f491a6191a5911574e2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409732"
---
# <a name="declaration-expected"></a><span data-ttu-id="52f21-102">Declaração esperada</span><span class="sxs-lookup"><span data-stu-id="52f21-102">Declaration expected</span></span>
<span data-ttu-id="52f21-103">Uma instrução não declarativa, como uma instrução de atribuição ou loop, ocorre fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="52f21-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="52f21-104">Somente declarações são permitidas para procedimentos externos.</span><span class="sxs-lookup"><span data-stu-id="52f21-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="52f21-105">Como alternativa, um elemento de programação é declarado sem uma palavra-chave de declaração, como `Dim` ou `Const` .</span><span class="sxs-lookup"><span data-stu-id="52f21-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="52f21-106">**ID do erro:** BC30188</span><span class="sxs-lookup"><span data-stu-id="52f21-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52f21-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="52f21-107">To correct this error</span></span>  
  
- <span data-ttu-id="52f21-108">Mova a instrução Declaration para o corpo de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="52f21-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
- <span data-ttu-id="52f21-109">Inicie a declaração com uma palavra-chave de declaração apropriada.</span><span class="sxs-lookup"><span data-stu-id="52f21-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
- <span data-ttu-id="52f21-110">Certifique-se de que uma palavra-chave de declaração não tenha sido digitada incorretamente.</span><span class="sxs-lookup"><span data-stu-id="52f21-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f21-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="52f21-111">See also</span></span>

- [<span data-ttu-id="52f21-112">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="52f21-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="52f21-113">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="52f21-113">Dim Statement</span></span>](../statements/dim-statement.md)
