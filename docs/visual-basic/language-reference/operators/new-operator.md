---
title: Operador New (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.new
- vb.NewConstraint
dev_langs:
- VB
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword
- New constraint
- New keyword
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: 23
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
ms.openlocfilehash: 0e1e2bbda070ff91db630b13ab033dba1e991dc7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="7d39c-102">Operador New (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d39c-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="7d39c-103">Apresenta um `New` cláusula para criar uma nova instância de objeto, especifica uma restrição de construtor em um parâmetro de tipo, ou identifica um `Sub` procedimento como um construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="7d39c-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d39c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d39c-104">Remarks</span></span>  
 <span data-ttu-id="7d39c-105">Em uma declaração ou instrução de atribuição, um `New` cláusula deve especificar uma classe definida na qual a instância pode ser criada.</span><span class="sxs-lookup"><span data-stu-id="7d39c-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="7d39c-106">Isso significa que a classe deve expor um ou mais construtores que pode acessar o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7d39c-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="7d39c-107">Você pode usar um `New` cláusula em uma instrução de declaração ou uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="7d39c-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="7d39c-108">Quando a instrução é executada, ele chama o construtor apropriado da classe especificada, passando quaisquer argumentos que você forneceu.</span><span class="sxs-lookup"><span data-stu-id="7d39c-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="7d39c-109">O exemplo a seguir demonstra isso criando instâncias de um `Customer` classe que possui dois construtores, um que não recebe parâmetros e um que utiliza um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7d39c-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 <span data-ttu-id="7d39c-110">[!code-vb[VbVbalrKeywords n º&11;](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7d39c-110">[!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="7d39c-111">Como matrizes são classes, `New` pode criar uma nova instância de matriz, como mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d39c-111">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 <span data-ttu-id="7d39c-112">[!code-vb[VbVbalrKeywords&#12;](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7d39c-112">[!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="7d39c-113">O common language runtime (CLR) gera um <xref:System.OutOfMemoryException>erro se não houver memória suficiente para criar a nova instância.</xref:System.OutOfMemoryException></span><span class="sxs-lookup"><span data-stu-id="7d39c-113">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d39c-114">O `New` palavra-chave também é usado em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor acessível sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7d39c-114">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="7d39c-115">Para obter mais informações sobre parâmetros de tipo e restrições, consulte [tipo lista](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="7d39c-115">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="7d39c-116">Para criar um procedimento de construtor para uma classe, defina o nome de uma `Sub` procedimento para o `New` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="7d39c-116">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="7d39c-117">Para obter mais informações, consulte [tempo de vida do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="7d39c-117">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="7d39c-118">O `New` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="7d39c-118">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7d39c-119">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="7d39c-119">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="7d39c-120">De</span><span class="sxs-lookup"><span data-stu-id="7d39c-120">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="7d39c-121">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="7d39c-121">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d39c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d39c-122">See Also</span></span>  
 <span data-ttu-id="7d39c-123"><xref:System.OutOfMemoryException></xref:System.OutOfMemoryException></span><span class="sxs-lookup"><span data-stu-id="7d39c-123"><xref:System.OutOfMemoryException></span></span>   
<span data-ttu-id="7d39c-124"> [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7d39c-124"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="7d39c-125"> [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md) </span><span class="sxs-lookup"><span data-stu-id="7d39c-125"> [Type List](../../../visual-basic/language-reference/statements/type-list.md) </span></span>  
<span data-ttu-id="7d39c-126"> [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="7d39c-126"> [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="7d39c-127"> [Tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="7d39c-127"> [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>
