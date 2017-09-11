---
title: Private (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Private
dev_langs:
- VB
helpviewer_keywords:
- Private keyword
- Private keyword, syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
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
ms.openlocfilehash: f1634d8361da88ba6b7d37c45982947ceb46979d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="private-visual-basic"></a><span data-ttu-id="aa17c-102">Particular (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa17c-102">Private (Visual Basic)</span></span>
<span data-ttu-id="aa17c-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seus contextos de declaração, inclusive em todos os tipos contidos.</span><span class="sxs-lookup"><span data-stu-id="aa17c-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa17c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa17c-104">Remarks</span></span>  
 <span data-ttu-id="aa17c-105">Se um elemento de programação representa funcionalidade proprietária, ou contém dados confidenciais, você geralmente deseja limitar o acesso a ele estritamente possível.</span><span class="sxs-lookup"><span data-stu-id="aa17c-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="aa17c-106">Obtém o limite máximo, permitindo que somente o módulo, classe ou estrutura que o define para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="aa17c-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="aa17c-107">Para limitar o acesso a um elemento dessa maneira, você pode declará-lo com `Private`.</span><span class="sxs-lookup"><span data-stu-id="aa17c-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="aa17c-108">Regras</span><span class="sxs-lookup"><span data-stu-id="aa17c-108">Rules</span></span>  
  
-   <span data-ttu-id="aa17c-109">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="aa17c-109">**Declaration Context.**</span></span> <span data-ttu-id="aa17c-110">Você pode usar `Private` somente no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="aa17c-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="aa17c-111">Isso significa que o contexto da declaração para um `Private` elemento deve ser um módulo, classe ou estrutura e não pode ser um arquivo fonte, namespace, interface ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="aa17c-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="aa17c-112">Comportamento</span><span class="sxs-lookup"><span data-stu-id="aa17c-112">Behavior</span></span>  
  
-   <span data-ttu-id="aa17c-113">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="aa17c-113">**Access Level.**</span></span> <span data-ttu-id="aa17c-114">Todo código em um contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="aa17c-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="aa17c-115">Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="aa17c-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="aa17c-116">Nenhum código fora do contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="aa17c-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="aa17c-117">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="aa17c-117">**Access Modifiers.**</span></span> <span data-ttu-id="aa17c-118">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="aa17c-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="aa17c-119">Para uma comparação entre os modificadores de acesso, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="aa17c-119">For a comparison of the access modifiers, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="aa17c-120">O `Private` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="aa17c-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="aa17c-121">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="aa17c-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="aa17c-122">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="aa17c-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="aa17c-123">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="aa17c-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="aa17c-124">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="aa17c-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="aa17c-125">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="aa17c-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="aa17c-126">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="aa17c-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="aa17c-127">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="aa17c-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="aa17c-128">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="aa17c-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="aa17c-129">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="aa17c-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="aa17c-130">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="aa17c-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="aa17c-131">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="aa17c-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="aa17c-132">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="aa17c-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="aa17c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa17c-133">See Also</span></span>  
 <span data-ttu-id="aa17c-134">[Público](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="aa17c-134">[Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="aa17c-135"> [Protegido](../../../visual-basic/language-reference/modifiers/protected.md) </span><span class="sxs-lookup"><span data-stu-id="aa17c-135"> [Protected](../../../visual-basic/language-reference/modifiers/protected.md) </span></span>  
<span data-ttu-id="aa17c-136"> [Friend](../../../visual-basic/language-reference/modifiers/friend.md) </span><span class="sxs-lookup"><span data-stu-id="aa17c-136"> [Friend](../../../visual-basic/language-reference/modifiers/friend.md) </span></span>  
<span data-ttu-id="aa17c-137"> [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="aa17c-137"> [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md) </span></span>  
<span data-ttu-id="aa17c-138"> [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="aa17c-138"> [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="aa17c-139"> [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="aa17c-139"> [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="aa17c-140"> [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="aa17c-140"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
