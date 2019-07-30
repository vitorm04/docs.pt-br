---
title: Opcional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 3758f17634395236abf2cd7059418bf6f8b6c062
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630926"
---
# <a name="optional-visual-basic"></a><span data-ttu-id="3935d-102">Opcional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3935d-102">Optional (Visual Basic)</span></span>

<span data-ttu-id="3935d-103">Especifica que um argumento de procedimento pode ser omitido quando o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="3935d-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>

## <a name="remarks"></a><span data-ttu-id="3935d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="3935d-104">Remarks</span></span>

<span data-ttu-id="3935d-105">Para cada parâmetro opcional, você deve especificar uma expressão constante como o valor padrão desse parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3935d-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="3935d-106">Se a expressão for avaliada como [Nothing](../../../visual-basic/language-reference/nothing.md), o valor padrão do tipo de dados Value será usado como o valor padrão do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3935d-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>

<span data-ttu-id="3935d-107">Se a lista de parâmetros contiver um parâmetro opcional, todos os parâmetros que o segue também deverão ser opcionais.</span><span class="sxs-lookup"><span data-stu-id="3935d-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>

<span data-ttu-id="3935d-108">O `Optional` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="3935d-108">The `Optional` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="3935d-109">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="3935d-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="3935d-110">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="3935d-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="3935d-111">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="3935d-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="3935d-112">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="3935d-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

> [!NOTE]
> <span data-ttu-id="3935d-113">Ao chamar um procedimento com ou sem parâmetros opcionais, você pode passar argumentos por posição ou por nome.</span><span class="sxs-lookup"><span data-stu-id="3935d-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="3935d-114">Para obter mais informações, consulte [passando argumentos por posição e por nome](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="3935d-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3935d-115">Você também pode definir um procedimento com parâmetros opcionais usando sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="3935d-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="3935d-116">Se você tiver um parâmetro opcional, poderá definir duas versões sobrecarregadas do procedimento, uma que aceite o parâmetro e outra que não.</span><span class="sxs-lookup"><span data-stu-id="3935d-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="3935d-117">Para obter mais informações, consulte [sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="3935d-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>

## <a name="example"></a><span data-ttu-id="3935d-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3935d-118">Example</span></span>

<span data-ttu-id="3935d-119">O exemplo a seguir define um procedimento que tem um parâmetro opcional.</span><span class="sxs-lookup"><span data-stu-id="3935d-119">The following example defines a procedure that has an optional parameter.</span></span>

```vb
Public Function FindMatches(ByRef values As List(Of String),
                            ByVal searchString As String,
                            Optional ByVal matchCase As Boolean = False) As List(Of String)

    Dim results As IEnumerable(Of String)

    If matchCase Then
        results = From v In values
                  Where v.Contains(searchString)
    Else
        results = From v In values
                  Where UCase(v).Contains(UCase(searchString))
    End If

    Return results.ToList()
End Function
```

## <a name="example"></a><span data-ttu-id="3935d-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3935d-120">Example</span></span>

<span data-ttu-id="3935d-121">O exemplo a seguir demonstra como chamar um procedimento com argumentos passados por position e com argumentos passados pelo nome.</span><span class="sxs-lookup"><span data-stu-id="3935d-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="3935d-122">O procedimento tem dois parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="3935d-122">The procedure has two optional parameters.</span></span>

[!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]

## <a name="see-also"></a><span data-ttu-id="3935d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3935d-123">See also</span></span>

- [<span data-ttu-id="3935d-124">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3935d-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="3935d-125">Parâmetros Opcionais</span><span class="sxs-lookup"><span data-stu-id="3935d-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="3935d-126">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="3935d-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
