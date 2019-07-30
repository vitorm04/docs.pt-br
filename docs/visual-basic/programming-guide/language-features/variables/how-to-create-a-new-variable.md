---
title: 'Como: Criar uma nova variável (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630903"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="9e764-102">Como: Criar uma nova variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e764-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="9e764-103">Você cria uma variável com uma [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9e764-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="9e764-104">Para criar uma nova variável</span><span class="sxs-lookup"><span data-stu-id="9e764-104">To create a new variable</span></span>

1. <span data-ttu-id="9e764-105">Declare a variável em uma `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="9e764-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="9e764-106">Inclua especificações para as características da variável, como [privado](../../../../visual-basic/language-reference/modifiers/private.md), [estático](../../../../visual-basic/language-reference/modifiers/static.md), [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md)ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="9e764-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="9e764-107">Para obter mais informações, consulte [características de elemento](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)declaradas.</span><span class="sxs-lookup"><span data-stu-id="9e764-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="9e764-108">Você não precisará da `Dim` palavra-chave se usar outras palavras-chaves na declaração.</span><span class="sxs-lookup"><span data-stu-id="9e764-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="9e764-109">Siga as especificações com o nome da variável, que deve seguir Visual Basic regras e convenções.</span><span class="sxs-lookup"><span data-stu-id="9e764-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="9e764-110">Para obter mais informações, consulte [nomes de elementos](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)declarados.</span><span class="sxs-lookup"><span data-stu-id="9e764-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="9e764-111">Siga o nome com a [cláusula as](../../../../visual-basic/language-reference/statements/as-clause.md) para especificar o tipo de dados da variável.</span><span class="sxs-lookup"><span data-stu-id="9e764-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="9e764-112">Se você não especificar o tipo de dados, ele usará o padrão `Object`:.</span><span class="sxs-lookup"><span data-stu-id="9e764-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="9e764-113">Siga a `As` cláusula com um sinal de igual`=`() e siga o sinal de igual com o valor inicial da variável.</span><span class="sxs-lookup"><span data-stu-id="9e764-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="9e764-114">Visual Basic atribui o valor especificado à variável toda vez que ele executa a `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="9e764-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="9e764-115">Se você não especificar um valor inicial, Visual Basic atribuirá o valor inicial padrão para o tipo de dados da variável quando ele entrar pela primeira vez no código que contém `Dim` a instrução.</span><span class="sxs-lookup"><span data-stu-id="9e764-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="9e764-116">Se a variável for um tipo de referência, você poderá criar uma instância de sua classe, incluindo a palavra-chave [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) na `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="9e764-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="9e764-117">Se você não usar `New`, o valor inicial da variável será [Nothing](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="9e764-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="9e764-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e764-118">See also</span></span>

- [<span data-ttu-id="9e764-119">Variáveis</span><span class="sxs-lookup"><span data-stu-id="9e764-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="9e764-120">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="9e764-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="9e764-121">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="9e764-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="9e764-122">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="9e764-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="9e764-123">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="9e764-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="9e764-124">Instruções</span><span class="sxs-lookup"><span data-stu-id="9e764-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="9e764-125">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="9e764-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="9e764-126">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="9e764-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
