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
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051852"
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="aff64-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff64-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="aff64-103">Especifica que uma variável ou propriedade pode ser lido mas não gravada.</span><span class="sxs-lookup"><span data-stu-id="aff64-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aff64-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="aff64-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="aff64-105">Regras</span><span class="sxs-lookup"><span data-stu-id="aff64-105">Rules</span></span>  
  
- <span data-ttu-id="aff64-106">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="aff64-106">**Declaration Context.**</span></span> <span data-ttu-id="aff64-107">Você pode usar `ReadOnly` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="aff64-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="aff64-108">Isso significa que o contexto da declaração para um `ReadOnly` elemento deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="aff64-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
- <span data-ttu-id="aff64-109">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="aff64-109">**Combined Modifiers.**</span></span> <span data-ttu-id="aff64-110">Não é possível especificar `ReadOnly` junto com `Static` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="aff64-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
- <span data-ttu-id="aff64-111">**Atribuir um valor.**</span><span class="sxs-lookup"><span data-stu-id="aff64-111">**Assigning a Value.**</span></span> <span data-ttu-id="aff64-112">Código consumindo um `ReadOnly` propriedade não é possível definir seu valor.</span><span class="sxs-lookup"><span data-stu-id="aff64-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="aff64-113">Mas o código que tem acesso ao armazenamento subjacente pode atribuir ou alterar o valor a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="aff64-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="aff64-114">Você pode atribuir um valor para um `ReadOnly` variável apenas em sua declaração ou no construtor de uma classe ou estrutura na qual ele está definido.</span><span class="sxs-lookup"><span data-stu-id="aff64-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="aff64-115">Quando usar uma variável somente leitura</span><span class="sxs-lookup"><span data-stu-id="aff64-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="aff64-116">Há situações em que você não pode usar um [instrução Const](../../../visual-basic/language-reference/statements/const-statement.md) declarar e atribuir um valor constante.</span><span class="sxs-lookup"><span data-stu-id="aff64-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="aff64-117">Por exemplo, o `Const` instrução pode não aceitar o tipo de dados que você deseja atribuir, ou você não poderá calcular o valor de tempo de compilação com uma expressão constante.</span><span class="sxs-lookup"><span data-stu-id="aff64-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="aff64-118">Você pode não saber até mesmo o valor no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="aff64-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="aff64-119">Nesses casos, você pode usar um `ReadOnly` variável para conter um valor constante.</span><span class="sxs-lookup"><span data-stu-id="aff64-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aff64-120">Se o tipo de dados da variável é um tipo de referência, como uma matriz ou uma instância da classe, seus membros podem ser alterados, mesmo se a variável em si é `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="aff64-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="aff64-121">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="aff64-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="aff64-122">Quando inicializado, a matriz apontada por `characterArray()` mantém "x", "y" e "z".</span><span class="sxs-lookup"><span data-stu-id="aff64-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="aff64-123">Porque a variável `characterArray` é `ReadOnly`, você não pode alterar seu valor depois que ele é inicializado; o que é, você não pode atribuir uma nova matriz a ela.</span><span class="sxs-lookup"><span data-stu-id="aff64-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="aff64-124">No entanto, você pode alterar os valores de um ou mais dos membros da matriz.</span><span class="sxs-lookup"><span data-stu-id="aff64-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="aff64-125">Uma chamada para o procedimento a seguir `changeArrayElement`, a matriz apontada por `characterArray()` mantém "x", "M" e "z".</span><span class="sxs-lookup"><span data-stu-id="aff64-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="aff64-126">Observe que isso é semelhante a declarar um parâmetro de procedimento para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), que impede que o procedimento altere o argumento de chamada em si, mas permite que a mudança de seus membros.</span><span class="sxs-lookup"><span data-stu-id="aff64-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aff64-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aff64-127">Example</span></span>  
 <span data-ttu-id="aff64-128">O exemplo a seguir define uma `ReadOnly` propriedade para a data em que um funcionário foi contratado.</span><span class="sxs-lookup"><span data-stu-id="aff64-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="aff64-129">A classe armazena o valor da propriedade internamente como um `Private` variável e apenas código dentro da classe pode alterar esse valor.</span><span class="sxs-lookup"><span data-stu-id="aff64-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="aff64-130">No entanto, a propriedade é `Public`, e qualquer código que pode acessar a classe pode ler a propriedade.</span><span class="sxs-lookup"><span data-stu-id="aff64-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 <span data-ttu-id="aff64-131">O `ReadOnly` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="aff64-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="aff64-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="aff64-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="aff64-133">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="aff64-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="aff64-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aff64-134">See also</span></span>

- [<span data-ttu-id="aff64-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="aff64-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="aff64-136">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="aff64-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
