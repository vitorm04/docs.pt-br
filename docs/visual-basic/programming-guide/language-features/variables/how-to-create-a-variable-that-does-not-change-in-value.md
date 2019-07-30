---
title: 'Como: Criar uma variável que não é alterada no valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d201e95463dd0431825fee03ebfd340ac80cc552
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630891"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="9b38b-102">Como: Criar uma variável que não é alterada no valor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b38b-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="9b38b-103">A noção de uma variável que não altera seu valor pode parecer ser contraditória.</span><span class="sxs-lookup"><span data-stu-id="9b38b-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="9b38b-104">Mas há situações em que uma constante não é viável e é útil ter uma variável com um valor fixo.</span><span class="sxs-lookup"><span data-stu-id="9b38b-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="9b38b-105">Nesse caso, você pode definir uma variável de membro com a palavra-chave [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="9b38b-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="9b38b-106">Você não pode usar a [instrução const](../../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribuir um valor constante nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="9b38b-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="9b38b-107">A `Const` instrução não aceita o tipo de dados que você deseja usar</span><span class="sxs-lookup"><span data-stu-id="9b38b-107">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="9b38b-108">Você não conhece o valor no tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="9b38b-108">You do not know the value at compile time</span></span>

- <span data-ttu-id="9b38b-109">Não é possível calcular o valor constante no tempo de compilação</span><span class="sxs-lookup"><span data-stu-id="9b38b-109">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="9b38b-110">Para criar uma variável que não é alterada no valor</span><span class="sxs-lookup"><span data-stu-id="9b38b-110">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="9b38b-111">Em nível de módulo, declare uma variável de membro com a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)e inclua a palavra-chave [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="9b38b-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="9b38b-112">Você pode especificar `ReadOnly` somente em uma variável de membro.</span><span class="sxs-lookup"><span data-stu-id="9b38b-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="9b38b-113">Isso significa que você deve definir a variável no nível de módulo, fora de qualquer procedimento.</span><span class="sxs-lookup"><span data-stu-id="9b38b-113">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="9b38b-114">Se você puder calcular o valor em uma única instrução em tempo de compilação, use uma cláusula de inicialização `Dim` na instrução.</span><span class="sxs-lookup"><span data-stu-id="9b38b-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="9b38b-115">Siga a [cláusula as](../../../../visual-basic/language-reference/statements/as-clause.md) com um sinal de igual`=`(), seguido por uma expressão.</span><span class="sxs-lookup"><span data-stu-id="9b38b-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="9b38b-116">Verifique se o compilador pode avaliar essa expressão como um valor constante.</span><span class="sxs-lookup"><span data-stu-id="9b38b-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="9b38b-117">Você pode atribuir um valor a uma `ReadOnly` variável apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="9b38b-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="9b38b-118">Depois de fazer isso, nenhum código pode alterar seu valor.</span><span class="sxs-lookup"><span data-stu-id="9b38b-118">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="9b38b-119">Se você não souber o valor em tempo de compilação, ou não puder computar em tempo de compilação em uma única instrução, ainda poderá atribuí-lo em tempo de execução em um construtor.</span><span class="sxs-lookup"><span data-stu-id="9b38b-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="9b38b-120">Para fazer isso, você deve declarar a `ReadOnly` variável no nível de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="9b38b-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="9b38b-121">No construtor para essa classe ou estrutura, calcule o valor fixo da variável e atribua-o à variável antes de retornar do construtor.</span><span class="sxs-lookup"><span data-stu-id="9b38b-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b38b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b38b-122">See also</span></span>

- [<span data-ttu-id="9b38b-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="9b38b-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="9b38b-124">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="9b38b-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
