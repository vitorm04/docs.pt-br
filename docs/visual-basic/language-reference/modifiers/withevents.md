---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 50d5a768393e90d28d150b451405e35e6f4c7953
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583035"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="3e626-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e626-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="3e626-103">Especifica que uma ou mais variáveis de membro declaradas se referem a uma instância de uma classe que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="3e626-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e626-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e626-104">Remarks</span></span>

<span data-ttu-id="3e626-105">Quando uma variável é definida usando `WithEvents`, você pode especificar declarativamente que um método manipule os eventos da variável usando a palavra-chave `Handles`.</span><span class="sxs-lookup"><span data-stu-id="3e626-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="3e626-106">Você pode usar `WithEvents` somente no nível de classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="3e626-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="3e626-107">Isso significa que o contexto de declaração para uma variável de `WithEvents` deve ser uma classe ou um módulo e não pode ser um arquivo de origem, namespace, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="3e626-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="3e626-108">Você não pode usar `WithEvents` em um membro de estrutura.</span><span class="sxs-lookup"><span data-stu-id="3e626-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="3e626-109">Você pode declarar apenas variáveis individuais, e não matrizes, com `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="3e626-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="3e626-110">Regras</span><span class="sxs-lookup"><span data-stu-id="3e626-110">Rules</span></span>

<span data-ttu-id="3e626-111">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="3e626-111">**Element Types.**</span></span> <span data-ttu-id="3e626-112">Você deve declarar `WithEvents` variáveis para serem variáveis de objeto para que elas possam aceitar instâncias de classe.</span><span class="sxs-lookup"><span data-stu-id="3e626-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="3e626-113">No entanto, você não pode declará-las como `Object`.</span><span class="sxs-lookup"><span data-stu-id="3e626-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="3e626-114">Você deve declará-los como a classe específica que pode gerar os eventos.</span><span class="sxs-lookup"><span data-stu-id="3e626-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="3e626-115">O modificador de `WithEvents` pode ser usado neste contexto: [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="3e626-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="3e626-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e626-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="3e626-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e626-117">See also</span></span>

- [<span data-ttu-id="3e626-118">Handles</span><span class="sxs-lookup"><span data-stu-id="3e626-118">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="3e626-119">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3e626-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="3e626-120">Eventos</span><span class="sxs-lookup"><span data-stu-id="3e626-120">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
