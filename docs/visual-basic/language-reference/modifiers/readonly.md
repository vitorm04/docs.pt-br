---
title: ReadOnly
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 8c7e7e7c1571fd7c595ebfd54fb5767078ef41f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351274"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="12377-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12377-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="12377-103">Especifica que uma variável ou propriedade pode ser lida, mas não gravada.</span><span class="sxs-lookup"><span data-stu-id="12377-103">Specifies that a variable or property can be read but not written.</span></span>

## <a name="remarks"></a><span data-ttu-id="12377-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="12377-104">Remarks</span></span>

## <a name="rules"></a><span data-ttu-id="12377-105">Regras</span><span class="sxs-lookup"><span data-stu-id="12377-105">Rules</span></span>

- <span data-ttu-id="12377-106">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="12377-106">**Declaration Context.**</span></span> <span data-ttu-id="12377-107">Você pode usar `ReadOnly` somente no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="12377-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="12377-108">Isso significa que o contexto de declaração para um elemento de `ReadOnly` deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="12377-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="12377-109">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="12377-109">**Combined Modifiers.**</span></span> <span data-ttu-id="12377-110">Você não pode especificar `ReadOnly` junto com `Static` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="12377-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>

- <span data-ttu-id="12377-111">**Atribuindo um valor.**</span><span class="sxs-lookup"><span data-stu-id="12377-111">**Assigning a Value.**</span></span> <span data-ttu-id="12377-112">O código que consome uma propriedade `ReadOnly` não pode definir seu valor.</span><span class="sxs-lookup"><span data-stu-id="12377-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="12377-113">Mas o código que tem acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="12377-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>

     <span data-ttu-id="12377-114">Você pode atribuir um valor a uma variável `ReadOnly` somente em sua declaração ou no construtor de uma classe ou estrutura na qual ela está definida.</span><span class="sxs-lookup"><span data-stu-id="12377-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>

## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="12377-115">Quando usar uma variável ReadOnly</span><span class="sxs-lookup"><span data-stu-id="12377-115">When to Use a ReadOnly Variable</span></span>

<span data-ttu-id="12377-116">Há situações em que você não pode usar uma [instrução const](../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribuir um valor constante.</span><span class="sxs-lookup"><span data-stu-id="12377-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="12377-117">Por exemplo, a instrução `Const` pode não aceitar o tipo de dados que você deseja atribuir, ou talvez você não consiga calcular o valor em tempo de compilação com uma expressão constante.</span><span class="sxs-lookup"><span data-stu-id="12377-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="12377-118">Você pode nem mesmo saber o valor no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="12377-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="12377-119">Nesses casos, você pode usar uma variável `ReadOnly` para manter um valor constante.</span><span class="sxs-lookup"><span data-stu-id="12377-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12377-120">Se o tipo de dados da variável for um tipo de referência, como uma matriz ou instância de classe, seus membros poderão ser alterados mesmo se a variável em si for `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="12377-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="12377-121">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="12377-121">The following example illustrates this.</span></span>

```vb
ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}
Sub ChangeArrayElement()
    characterArray(1) = "M"c
End Sub
```

<span data-ttu-id="12377-122">Quando inicializado, a matriz apontada por `characterArray()` mantém "x", "y" e "z".</span><span class="sxs-lookup"><span data-stu-id="12377-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="12377-123">Como a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor depois que ela é inicializada; ou seja, você não pode atribuir uma nova matriz a ele.</span><span class="sxs-lookup"><span data-stu-id="12377-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="12377-124">No entanto, você pode alterar os valores de um ou mais dos membros da matriz.</span><span class="sxs-lookup"><span data-stu-id="12377-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="12377-125">Após uma chamada para o procedimento `ChangeArrayElement`, a matriz apontada por `characterArray()` mantém "x", "M" e "z".</span><span class="sxs-lookup"><span data-stu-id="12377-125">Following a call to the procedure `ChangeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>

<span data-ttu-id="12377-126">Observe que isso é semelhante à declaração de um parâmetro de procedimento como [ByVal](byval.md), o que impede que o procedimento altere o próprio argumento de chamada, mas permite alterar seus membros.</span><span class="sxs-lookup"><span data-stu-id="12377-126">Note that this is similar to declaring a procedure parameter to be [ByVal](byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>

## <a name="example"></a><span data-ttu-id="12377-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12377-127">Example</span></span>

<span data-ttu-id="12377-128">O exemplo a seguir define uma propriedade `ReadOnly` para a data em que um funcionário foi contratado.</span><span class="sxs-lookup"><span data-stu-id="12377-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="12377-129">A classe armazena o valor da propriedade internamente como uma variável `Private`, e somente o código dentro da classe pode alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="12377-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="12377-130">No entanto, a propriedade é `Public`e qualquer código que possa acessar a classe pode ler a propriedade.</span><span class="sxs-lookup"><span data-stu-id="12377-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>

[!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]

<span data-ttu-id="12377-131">O modificador de `ReadOnly` pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="12377-131">The `ReadOnly` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="12377-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="12377-132">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="12377-133">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="12377-133">Property Statement</span></span>](../statements/property-statement.md)

## <a name="see-also"></a><span data-ttu-id="12377-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12377-134">See also</span></span>

- [<span data-ttu-id="12377-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="12377-135">WriteOnly</span></span>](writeonly.md)
- [<span data-ttu-id="12377-136">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="12377-136">Keywords</span></span>](../keywords/index.md)
