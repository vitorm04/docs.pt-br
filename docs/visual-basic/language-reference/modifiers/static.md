---
title: Estático
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2b7113424969b0b18c981b0c8932aeef3795ca4a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867674"
---
# <a name="static-visual-basic"></a><span data-ttu-id="eed69-102">Estático (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eed69-102">Static (Visual Basic)</span></span>

<span data-ttu-id="eed69-103">Especifica que uma ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="eed69-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eed69-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="eed69-104">Remarks</span></span>  

 <span data-ttu-id="eed69-105">Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento para.</span><span class="sxs-lookup"><span data-stu-id="eed69-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="eed69-106">Uma variável estática continua existindo e retém seu valor mais recente.</span><span class="sxs-lookup"><span data-stu-id="eed69-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="eed69-107">Na próxima vez em que o código chamar o procedimento, a variável não será reinicializada e ainda manterá o valor mais recente que você atribuiu a ela.</span><span class="sxs-lookup"><span data-stu-id="eed69-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="eed69-108">Uma variável estática continua existindo durante o tempo de vida da classe ou do módulo em que ela está definida.</span><span class="sxs-lookup"><span data-stu-id="eed69-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="eed69-109">Regras</span><span class="sxs-lookup"><span data-stu-id="eed69-109">Rules</span></span>  
  
- <span data-ttu-id="eed69-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="eed69-110">**Declaration Context.**</span></span> <span data-ttu-id="eed69-111">Você pode usar `Static` somente em variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="eed69-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="eed69-112">Isso significa que o contexto de declaração para uma `Static` variável deve ser um procedimento ou um bloco em um procedimento, e não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="eed69-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="eed69-113">Você não pode usar `Static` dentro de um procedimento de estrutura.</span><span class="sxs-lookup"><span data-stu-id="eed69-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
- <span data-ttu-id="eed69-114">Os tipos de dados de `Static` variáveis locais não podem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="eed69-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="eed69-115">Para obter mais informações, consulte [inferência de tipo local](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="eed69-115">For more information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
- <span data-ttu-id="eed69-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="eed69-116">**Combined Modifiers.**</span></span> <span data-ttu-id="eed69-117">Você não pode especificar `Static` juntos com `ReadOnly` , `Shadows` ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="eed69-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="eed69-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="eed69-118">Behavior</span></span>  

 <span data-ttu-id="eed69-119">Quando você declara uma variável estática em um `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="eed69-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="eed69-120">Você chama um `Shared` procedimento usando o nome da classe, não uma variável que aponta para uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="eed69-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="eed69-121">Quando você declara uma variável estática em um procedimento que não é `Shared` , apenas uma cópia da variável está disponível para cada instância da classe.</span><span class="sxs-lookup"><span data-stu-id="eed69-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="eed69-122">Você chama um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.</span><span class="sxs-lookup"><span data-stu-id="eed69-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed69-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eed69-123">Example</span></span>  

 <span data-ttu-id="eed69-124">O exemplo a seguir demonstra o uso de `Static`.</span><span class="sxs-lookup"><span data-stu-id="eed69-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 <span data-ttu-id="eed69-125">A `Static` variável `totalSales` é inicializada como 0 somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="eed69-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="eed69-126">Cada vez que você inserir `updateSales` , `totalSales` ainda terá o valor mais recente que você calculou para ele.</span><span class="sxs-lookup"><span data-stu-id="eed69-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="eed69-127">O `Static` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="eed69-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="eed69-128">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="eed69-128">Dim Statement</span></span>](../statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="eed69-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="eed69-129">See also</span></span>

- [<span data-ttu-id="eed69-130">Sombras</span><span class="sxs-lookup"><span data-stu-id="eed69-130">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="eed69-131">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="eed69-131">Shared</span></span>](shared.md)
- [<span data-ttu-id="eed69-132">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eed69-132">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="eed69-133">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="eed69-133">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="eed69-134">Estruturas</span><span class="sxs-lookup"><span data-stu-id="eed69-134">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="eed69-135">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="eed69-135">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="eed69-136">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="eed69-136">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
