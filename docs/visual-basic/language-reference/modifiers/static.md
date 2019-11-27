---
title: Estático
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: f020756466888f51298abb423997906ddc7caff7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350755"
---
# <a name="static-visual-basic"></a><span data-ttu-id="de4ba-102">Estático (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de4ba-102">Static (Visual Basic)</span></span>
<span data-ttu-id="de4ba-103">Especifica que uma ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="de4ba-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de4ba-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="de4ba-104">Remarks</span></span>  
 <span data-ttu-id="de4ba-105">Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento para.</span><span class="sxs-lookup"><span data-stu-id="de4ba-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="de4ba-106">Uma variável estática continua existindo e retém seu valor mais recente.</span><span class="sxs-lookup"><span data-stu-id="de4ba-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="de4ba-107">Na próxima vez em que o código chamar o procedimento, a variável não será reinicializada e ainda manterá o valor mais recente que você atribuiu a ela.</span><span class="sxs-lookup"><span data-stu-id="de4ba-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="de4ba-108">Uma variável estática continua existindo durante o tempo de vida da classe ou do módulo em que ela está definida.</span><span class="sxs-lookup"><span data-stu-id="de4ba-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="de4ba-109">Regras</span><span class="sxs-lookup"><span data-stu-id="de4ba-109">Rules</span></span>  
  
- <span data-ttu-id="de4ba-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="de4ba-110">**Declaration Context.**</span></span> <span data-ttu-id="de4ba-111">Você pode usar `Static` apenas em variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="de4ba-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="de4ba-112">Isso significa que o contexto de declaração para uma variável `Static` deve ser um procedimento ou um bloco em um procedimento, e não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="de4ba-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="de4ba-113">Você não pode usar `Static` dentro de um procedimento de estrutura.</span><span class="sxs-lookup"><span data-stu-id="de4ba-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="de4ba-114">Os tipos de dados de `Static` variáveis locais não podem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="de4ba-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="de4ba-115">Para obter mais informações, consulte [inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="de4ba-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="de4ba-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="de4ba-116">**Combined Modifiers.**</span></span> <span data-ttu-id="de4ba-117">Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="de4ba-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="de4ba-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="de4ba-118">Behavior</span></span>  
 <span data-ttu-id="de4ba-119">Quando você declara uma variável estática em um procedimento `Shared`, apenas uma cópia da variável estática está disponível para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="de4ba-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="de4ba-120">Você chama um procedimento de `Shared` usando o nome da classe, não uma variável que aponta para uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="de4ba-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="de4ba-121">Quando você declara uma variável estática em um procedimento que não é `Shared`, apenas uma cópia da variável está disponível para cada instância da classe.</span><span class="sxs-lookup"><span data-stu-id="de4ba-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="de4ba-122">Você chama um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.</span><span class="sxs-lookup"><span data-stu-id="de4ba-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de4ba-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de4ba-123">Example</span></span>  
 <span data-ttu-id="de4ba-124">O exemplo a seguir demonstra o uso de `Static`.</span><span class="sxs-lookup"><span data-stu-id="de4ba-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="de4ba-125">A variável de `Static` `totalSales` é inicializada como 0 somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="de4ba-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="de4ba-126">Cada vez que você inserir `updateSales`, `totalSales` ainda terá o valor mais recente que você calculou para ele.</span><span class="sxs-lookup"><span data-stu-id="de4ba-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="de4ba-127">O modificador de `Static` pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="de4ba-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="de4ba-128">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="de4ba-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="de4ba-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de4ba-129">See also</span></span>

- [<span data-ttu-id="de4ba-130">Sombras</span><span class="sxs-lookup"><span data-stu-id="de4ba-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="de4ba-131">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="de4ba-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="de4ba-132">Tempo de vida em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de4ba-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="de4ba-133">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="de4ba-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="de4ba-134">Estruturas</span><span class="sxs-lookup"><span data-stu-id="de4ba-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="de4ba-135">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="de4ba-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="de4ba-136">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="de4ba-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
