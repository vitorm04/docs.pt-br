---
title: "Estático (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Static
dev_langs:
- VB
helpviewer_keywords:
- static modifier
- Static keyword
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d18c2f7ff98e626de45dfe03e0b5ca207a292d17
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="static-visual-basic"></a><span data-ttu-id="56ff3-102">Estático (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56ff3-102">Static (Visual Basic)</span></span>
<span data-ttu-id="56ff3-103">Especifica que um ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual elas são declaradas.</span><span class="sxs-lookup"><span data-stu-id="56ff3-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56ff3-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="56ff3-104">Remarks</span></span>  
 <span data-ttu-id="56ff3-105">Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento para.</span><span class="sxs-lookup"><span data-stu-id="56ff3-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="56ff3-106">Uma variável estática continua a existir e mantém seu valor mais recente.</span><span class="sxs-lookup"><span data-stu-id="56ff3-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="56ff3-107">Na próxima vez em que seu código chama o procedimento, a variável não será reinicializada, e ela ainda mantém o valor mais recente que você atribuiu a ele.</span><span class="sxs-lookup"><span data-stu-id="56ff3-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="56ff3-108">Uma variável estática continua a existir durante o tempo de vida da classe ou módulo que é definido em.</span><span class="sxs-lookup"><span data-stu-id="56ff3-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="56ff3-109">Regras</span><span class="sxs-lookup"><span data-stu-id="56ff3-109">Rules</span></span>  
  
-   <span data-ttu-id="56ff3-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="56ff3-110">**Declaration Context.**</span></span> <span data-ttu-id="56ff3-111">Você pode usar `Static` somente nas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="56ff3-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="56ff3-112">Isso significa que o contexto da declaração para um `Static` variável deve ser um procedimento ou um bloco em um procedimento e não pode ser um arquivo fonte, namespace, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="56ff3-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="56ff3-113">Não é possível usar `Static` dentro de um procedimento de estrutura.</span><span class="sxs-lookup"><span data-stu-id="56ff3-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="56ff3-114">Os tipos de dados de `Static` variáveis locais não podem ser inferidas.</span><span class="sxs-lookup"><span data-stu-id="56ff3-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="56ff3-115">Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="56ff3-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="56ff3-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="56ff3-116">**Combined Modifiers.**</span></span> <span data-ttu-id="56ff3-117">Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="56ff3-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="56ff3-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="56ff3-118">Behavior</span></span>  
 <span data-ttu-id="56ff3-119">Quando você declara uma variável estática em uma `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="56ff3-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="56ff3-120">Você chamar um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="56ff3-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="56ff3-121">Quando você declara uma variável estática em um procedimento que não seja `Shared`, somente uma cópia da variável está disponível para cada instância da classe.</span><span class="sxs-lookup"><span data-stu-id="56ff3-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="56ff3-122">Você pode chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.</span><span class="sxs-lookup"><span data-stu-id="56ff3-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ff3-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56ff3-123">Example</span></span>  
 <span data-ttu-id="56ff3-124">O exemplo a seguir demonstra o uso de `Static`.</span><span class="sxs-lookup"><span data-stu-id="56ff3-124">The following example demonstrates the use of `Static`.</span></span>  
  
 <span data-ttu-id="56ff3-125">[!code-vb[VbVbalrKeywords n º&5;](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="56ff3-125">[!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]</span></span>  
  
 <span data-ttu-id="56ff3-126">O `Static` variável `totalSales` foi inicializada para 0 somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="56ff3-126">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="56ff3-127">Cada vez que você inserir `updateSales`, `totalSales` ainda tem o valor mais recente que você calculou para ela.</span><span class="sxs-lookup"><span data-stu-id="56ff3-127">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="56ff3-128">O `Static` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="56ff3-128">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="56ff3-129">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="56ff3-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="56ff3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56ff3-130">See Also</span></span>  
 <span data-ttu-id="56ff3-131">[Sombras](../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="56ff3-131">[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="56ff3-132"> [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) </span><span class="sxs-lookup"><span data-stu-id="56ff3-132"> [Shared](../../../visual-basic/language-reference/modifiers/shared.md) </span></span>  
<span data-ttu-id="56ff3-133"> [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span><span class="sxs-lookup"><span data-stu-id="56ff3-133"> [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span></span>  
<span data-ttu-id="56ff3-134"> [Declaração de variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="56ff3-134"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="56ff3-135"> [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="56ff3-135"> [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="56ff3-136"> [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="56ff3-136"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="56ff3-137"> [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="56ff3-137"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
