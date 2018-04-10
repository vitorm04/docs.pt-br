---
title: Protegido (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a><span data-ttu-id="d58da-102">Protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d58da-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="d58da-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de sua própria classe ou de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="d58da-103">Specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d58da-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d58da-104">Remarks</span></span>  
 <span data-ttu-id="d58da-105">Às vezes, um elemento de programação declarado em uma classe contém dados confidenciais ou código restrito, e você deseja limitar o acesso ao elemento.</span><span class="sxs-lookup"><span data-stu-id="d58da-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="d58da-106">No entanto, se a classe é herdável e você espera uma hierarquia de classes derivadas, pode ser necessário para essas classes derivadas acessar os dados ou código.</span><span class="sxs-lookup"><span data-stu-id="d58da-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="d58da-107">Nesse caso, você deseja que o elemento para ser acessível da classe base e de todas as classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="d58da-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="d58da-108">Para limitar o acesso a um elemento dessa maneira, você pode declará-la com `Protected`.</span><span class="sxs-lookup"><span data-stu-id="d58da-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d58da-109">Regras</span><span class="sxs-lookup"><span data-stu-id="d58da-109">Rules</span></span>  
  
-   <span data-ttu-id="d58da-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="d58da-110">**Declaration Context.**</span></span> <span data-ttu-id="d58da-111">Você pode usar `Protected` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="d58da-111">You can use `Protected` only at class level.</span></span> <span data-ttu-id="d58da-112">Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="d58da-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
-   <span data-ttu-id="d58da-113">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="d58da-113">**Combined Modifiers.**</span></span> <span data-ttu-id="d58da-114">Você pode usar o `Protected` modificador junto com o [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modificador na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="d58da-114">You can use the `Protected` modifier together with the [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifier in the same declaration.</span></span> <span data-ttu-id="d58da-115">Essa combinação torna os elementos declarados acessíveis de qualquer lugar no mesmo assembly, de sua própria classe e de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="d58da-115">This combination makes the declared elements accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="d58da-116">Você pode especificar `Protected Friend` somente em membros de classes.</span><span class="sxs-lookup"><span data-stu-id="d58da-116">You can specify `Protected Friend` only on members of classes.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d58da-117">Comportamento</span><span class="sxs-lookup"><span data-stu-id="d58da-117">Behavior</span></span>  
  
-   <span data-ttu-id="d58da-118">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="d58da-118">**Access Level.**</span></span> <span data-ttu-id="d58da-119">Todo o código em uma classe pode acessar seus elementos.</span><span class="sxs-lookup"><span data-stu-id="d58da-119">All code in a class can access its elements.</span></span> <span data-ttu-id="d58da-120">O código em qualquer classe que deriva de uma classe base pode acessar todos os `Protected` elementos da classe base.</span><span class="sxs-lookup"><span data-stu-id="d58da-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="d58da-121">Isso é verdadeiro para todas as gerações de derivação.</span><span class="sxs-lookup"><span data-stu-id="d58da-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="d58da-122">Isso significa que uma classe pode acessar `Protected` elementos da classe base da classe base e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="d58da-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="d58da-123">Acesso protegido não é um superconjunto ou subconjunto de acesso friend.</span><span class="sxs-lookup"><span data-stu-id="d58da-123">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="d58da-124">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="d58da-124">**Access Modifiers.**</span></span> <span data-ttu-id="d58da-125">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="d58da-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="d58da-126">Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d58da-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="d58da-127">O `Protected` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="d58da-127">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d58da-128">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="d58da-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="d58da-129">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="d58da-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="d58da-130">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="d58da-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="d58da-131">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="d58da-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="d58da-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="d58da-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="d58da-133">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="d58da-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="d58da-134">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="d58da-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="d58da-135">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="d58da-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="d58da-136">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="d58da-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="d58da-137">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="d58da-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="d58da-138">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="d58da-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="d58da-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="d58da-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d58da-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d58da-140">See Also</span></span>  
 [<span data-ttu-id="d58da-141">Público</span><span class="sxs-lookup"><span data-stu-id="d58da-141">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="d58da-142">Friend</span><span class="sxs-lookup"><span data-stu-id="d58da-142">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="d58da-143">Privado</span><span class="sxs-lookup"><span data-stu-id="d58da-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="d58da-144">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d58da-144">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="d58da-145">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="d58da-145">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="d58da-146">Estruturas</span><span class="sxs-lookup"><span data-stu-id="d58da-146">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="d58da-147">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="d58da-147">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
