---
title: Estático (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 1205d620fb5b6ec6af14cdeb7c6d78439f9e6b97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627623"
---
# <a name="static-visual-basic"></a><span data-ttu-id="90b46-102">Estático (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90b46-102">Static (Visual Basic)</span></span>
<span data-ttu-id="90b46-103">Especifica que um ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o encerramento do procedimento no qual eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="90b46-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90b46-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="90b46-104">Remarks</span></span>  
 <span data-ttu-id="90b46-105">Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento será interrompida.</span><span class="sxs-lookup"><span data-stu-id="90b46-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="90b46-106">Uma variável estática continua a existir e mantém seu valor mais recente.</span><span class="sxs-lookup"><span data-stu-id="90b46-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="90b46-107">Na próxima vez em que seu código chama o procedimento, a variável não for reiniciada, e ela ainda mantém o valor mais recente que você atribuiu a ele.</span><span class="sxs-lookup"><span data-stu-id="90b46-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="90b46-108">Uma variável estática continua existindo durante a vida útil da classe ou módulo que é definido em.</span><span class="sxs-lookup"><span data-stu-id="90b46-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="90b46-109">Regras</span><span class="sxs-lookup"><span data-stu-id="90b46-109">Rules</span></span>  
  
-   <span data-ttu-id="90b46-110">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="90b46-110">**Declaration Context.**</span></span> <span data-ttu-id="90b46-111">Você pode usar `Static` somente nas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="90b46-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="90b46-112">Isso significa que o contexto da declaração para um `Static` variável deve ser um procedimento ou um bloco em um procedimento, e ele não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="90b46-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="90b46-113">Não é possível usar `Static` dentro de um procedimento de estrutura.</span><span class="sxs-lookup"><span data-stu-id="90b46-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="90b46-114">Os tipos de dados de `Static` variáveis locais não podem ser inferidas.</span><span class="sxs-lookup"><span data-stu-id="90b46-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="90b46-115">Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="90b46-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="90b46-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="90b46-116">**Combined Modifiers.**</span></span> <span data-ttu-id="90b46-117">Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="90b46-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="90b46-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="90b46-118">Behavior</span></span>  
 <span data-ttu-id="90b46-119">Quando você declara uma variável estática em uma `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="90b46-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="90b46-120">Você chama um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="90b46-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="90b46-121">Quando você declara uma variável estática em um procedimento que não seja `Shared`, somente uma cópia da variável está disponível para cada instância da classe.</span><span class="sxs-lookup"><span data-stu-id="90b46-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="90b46-122">Você pode chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.</span><span class="sxs-lookup"><span data-stu-id="90b46-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90b46-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90b46-123">Example</span></span>  
 <span data-ttu-id="90b46-124">O exemplo a seguir demonstra o uso de `Static`.</span><span class="sxs-lookup"><span data-stu-id="90b46-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="90b46-125">O `Static` variável `totalSales` será inicializada como 0, apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="90b46-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="90b46-126">Cada vez que você insere `updateSales`, `totalSales` ainda tem o valor mais recente que calculou para ela.</span><span class="sxs-lookup"><span data-stu-id="90b46-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="90b46-127">O `Static` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="90b46-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="90b46-128">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="90b46-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="90b46-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90b46-129">See also</span></span>
- [<span data-ttu-id="90b46-130">Sombras</span><span class="sxs-lookup"><span data-stu-id="90b46-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="90b46-131">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="90b46-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="90b46-132">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90b46-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="90b46-133">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="90b46-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="90b46-134">Estruturas</span><span class="sxs-lookup"><span data-stu-id="90b46-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="90b46-135">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="90b46-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="90b46-136">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="90b46-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
