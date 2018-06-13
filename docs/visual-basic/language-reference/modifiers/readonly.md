---
title: ReadOnly (Visual Basic)
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
ms.openlocfilehash: e2957bf49292dfcafab8e78f4b997247c34ad279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599906"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="183dc-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="183dc-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="183dc-103">Especifica que uma variável ou propriedade pode ser lida mas não gravada.</span><span class="sxs-lookup"><span data-stu-id="183dc-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="183dc-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="183dc-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="183dc-105">Regras</span><span class="sxs-lookup"><span data-stu-id="183dc-105">Rules</span></span>  
  
-   <span data-ttu-id="183dc-106">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="183dc-106">**Declaration Context.**</span></span> <span data-ttu-id="183dc-107">Você pode usar `ReadOnly` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="183dc-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="183dc-108">Isso significa que o contexto da declaração para um `ReadOnly` elemento deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="183dc-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="183dc-109">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="183dc-109">**Combined Modifiers.**</span></span> <span data-ttu-id="183dc-110">Não é possível especificar `ReadOnly` junto com `Static` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="183dc-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="183dc-111">**Atribuindo um valor.**</span><span class="sxs-lookup"><span data-stu-id="183dc-111">**Assigning a Value.**</span></span> <span data-ttu-id="183dc-112">Código de consumo um `ReadOnly` propriedade não é possível definir seu valor.</span><span class="sxs-lookup"><span data-stu-id="183dc-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="183dc-113">Mas o código que tenha acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="183dc-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="183dc-114">Você pode atribuir um valor para um `ReadOnly` variável somente em sua declaração ou no construtor de uma classe ou estrutura na qual ela está definida.</span><span class="sxs-lookup"><span data-stu-id="183dc-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="183dc-115">Quando usar uma variável somente leitura</span><span class="sxs-lookup"><span data-stu-id="183dc-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="183dc-116">Há situações em que você não pode usar um [Declaração Const](../../../visual-basic/language-reference/statements/const-statement.md) declarar e atribuir um valor constante.</span><span class="sxs-lookup"><span data-stu-id="183dc-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="183dc-117">Por exemplo, o `Const` instrução não pode aceitar o tipo de dados que você deseja atribuir ou você não poderá calcular o valor em tempo de compilação com uma expressão constante.</span><span class="sxs-lookup"><span data-stu-id="183dc-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="183dc-118">Você pode não saber até mesmo o valor em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="183dc-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="183dc-119">Nesses casos, você pode usar um `ReadOnly` variável para conter um valor constante.</span><span class="sxs-lookup"><span data-stu-id="183dc-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="183dc-120">Se o tipo de dados da variável é um tipo de referência, como uma matriz ou uma instância da classe, seus membros podem ser alterados, mesmo se a variável em si é `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="183dc-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="183dc-121">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="183dc-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="183dc-122">Quando inicializado, a matriz apontada pelo `characterArray()` mantém "x", "y" e "z".</span><span class="sxs-lookup"><span data-stu-id="183dc-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="183dc-123">Porque a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor quando ele é inicializado; o que é, você não pode atribuir uma nova matriz para ele.</span><span class="sxs-lookup"><span data-stu-id="183dc-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="183dc-124">No entanto, você pode alterar os valores de um ou mais membros da matriz.</span><span class="sxs-lookup"><span data-stu-id="183dc-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="183dc-125">Uma chamada para o procedimento a seguir `changeArrayElement`, a matriz apontada pelo `characterArray()` mantém "x", "M" e "z".</span><span class="sxs-lookup"><span data-stu-id="183dc-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="183dc-126">Observe que isso é semelhante ao declarar um parâmetro de procedimento para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), que impede que o procedimento altere o argumento de chamada, mas permite que a mudança de seus membros.</span><span class="sxs-lookup"><span data-stu-id="183dc-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="183dc-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="183dc-127">Example</span></span>  
 <span data-ttu-id="183dc-128">O exemplo a seguir define um `ReadOnly` propriedade para a data em que um funcionário foi contratado.</span><span class="sxs-lookup"><span data-stu-id="183dc-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="183dc-129">Os repositórios de classe, o valor da propriedade internamente como um `Private` código variável e somente dentro da classe pode alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="183dc-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="183dc-130">No entanto, a propriedade é `Public`, e qualquer código que pode acessar a classe pode ler a propriedade.</span><span class="sxs-lookup"><span data-stu-id="183dc-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 <span data-ttu-id="183dc-131">O `ReadOnly` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="183dc-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="183dc-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="183dc-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="183dc-133">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="183dc-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="183dc-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="183dc-134">See Also</span></span>  
 [<span data-ttu-id="183dc-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="183dc-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="183dc-136">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="183dc-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
