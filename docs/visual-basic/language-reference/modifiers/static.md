---
title: Estático (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2cbd99a026a5ebf0e215ee5732d62ccf639d3836
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602048"
---
# <a name="static-visual-basic"></a><span data-ttu-id="cc148-102">Estático (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc148-102">Static (Visual Basic)</span></span>
<span data-ttu-id="cc148-103">Especifica que um ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="cc148-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc148-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc148-104">Remarks</span></span>  
 <span data-ttu-id="cc148-105">Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento será interrompida.</span><span class="sxs-lookup"><span data-stu-id="cc148-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="cc148-106">Uma variável estática continua existindo e retém seu valor mais recente.</span><span class="sxs-lookup"><span data-stu-id="cc148-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="cc148-107">Na próxima vez que seu código chama o procedimento, a variável não for reiniciada, e ela ainda mantém o valor mais recente que você atribuiu a ele.</span><span class="sxs-lookup"><span data-stu-id="cc148-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="cc148-108">Uma variável estática continua a existir para o tempo de vida da classe ou módulo que está definido no.</span><span class="sxs-lookup"><span data-stu-id="cc148-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cc148-109">Regras</span><span class="sxs-lookup"><span data-stu-id="cc148-109">Rules</span></span>  
  
-   <span data-ttu-id="cc148-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="cc148-110">**Declaration Context.**</span></span> <span data-ttu-id="cc148-111">Você pode usar `Static` somente nas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="cc148-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="cc148-112">Isso significa que o contexto da declaração para um `Static` variável deve ser um procedimento ou um bloco em um procedimento, e ele não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="cc148-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="cc148-113">Não é possível usar `Static` dentro de um procedimento de estrutura.</span><span class="sxs-lookup"><span data-stu-id="cc148-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="cc148-114">Os tipos de dados de `Static` variáveis locais não podem ser inferidas.</span><span class="sxs-lookup"><span data-stu-id="cc148-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="cc148-115">Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="cc148-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="cc148-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="cc148-116">**Combined Modifiers.**</span></span> <span data-ttu-id="cc148-117">Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="cc148-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cc148-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="cc148-118">Behavior</span></span>  
 <span data-ttu-id="cc148-119">Quando você declara uma variável estática em uma `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="cc148-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="cc148-120">Você chama um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="cc148-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="cc148-121">Quando você declara uma variável estática em um procedimento que não seja `Shared`, somente uma cópia da variável está disponível para cada instância da classe.</span><span class="sxs-lookup"><span data-stu-id="cc148-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="cc148-122">Você pode chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.</span><span class="sxs-lookup"><span data-stu-id="cc148-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc148-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cc148-123">Example</span></span>  
 <span data-ttu-id="cc148-124">O exemplo a seguir demonstra o uso de `Static`.</span><span class="sxs-lookup"><span data-stu-id="cc148-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="cc148-125">O `Static` variável `totalSales` foi inicializada para 0 somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="cc148-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="cc148-126">Cada vez que você inserir `updateSales`, `totalSales` ainda tem o valor mais recente que você calculou para ela.</span><span class="sxs-lookup"><span data-stu-id="cc148-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="cc148-127">O `Static` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="cc148-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="cc148-128">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="cc148-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cc148-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc148-129">See Also</span></span>  
 [<span data-ttu-id="cc148-130">Sombras</span><span class="sxs-lookup"><span data-stu-id="cc148-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="cc148-131">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="cc148-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="cc148-132">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc148-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="cc148-133">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="cc148-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="cc148-134">Estruturas</span><span class="sxs-lookup"><span data-stu-id="cc148-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="cc148-135">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="cc148-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="cc148-136">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="cc148-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
