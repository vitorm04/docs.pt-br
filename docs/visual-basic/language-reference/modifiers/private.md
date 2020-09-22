---
title: Particular
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 59f1c1666ce38923a2861244fb377007cd0fa992
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874977"
---
# <a name="private-visual-basic"></a><span data-ttu-id="7f0c0-102">Particular (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f0c0-102">Private (Visual Basic)</span></span>

<span data-ttu-id="7f0c0-103">Especifica que um ou mais elementos de programação declarados são acessíveis somente de dentro de seu contexto de declaração, incluindo de dentro de qualquer tipo contido.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f0c0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f0c0-104">Remarks</span></span>  

 <span data-ttu-id="7f0c0-105">Se um elemento de programação representar a funcionalidade proprietária ou contiver dados confidenciais, você geralmente desejará limitar o acesso a ele o mais estritamente possível.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="7f0c0-106">Você Obtém a limitação máxima permitindo apenas o módulo, a classe ou a estrutura que a define para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="7f0c0-107">Para limitar o acesso a um elemento dessa forma, você pode declará-lo com `Private` .</span><span class="sxs-lookup"><span data-stu-id="7f0c0-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="7f0c0-108">Você também pode usar o modificador de acesso [protegido privado](private-protected.md) , que torna um membro acessível de dentro dessa classe e de classes derivadas localizadas em seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="7f0c0-109">Regras</span><span class="sxs-lookup"><span data-stu-id="7f0c0-109">Rules</span></span>  

- <span data-ttu-id="7f0c0-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="7f0c0-110">**Declaration Context.**</span></span> <span data-ttu-id="7f0c0-111">Você pode usar `Private` somente no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="7f0c0-112">Isso significa que o contexto de declaração para um `Private` elemento deve ser um módulo, uma classe ou uma estrutura e não pode ser um arquivo de origem, namespace, interface ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7f0c0-113">Comportamento</span><span class="sxs-lookup"><span data-stu-id="7f0c0-113">Behavior</span></span>  
  
- <span data-ttu-id="7f0c0-114">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="7f0c0-114">**Access Level.**</span></span> <span data-ttu-id="7f0c0-115">Todo o código dentro de um contexto de declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="7f0c0-116">Isso inclui o código dentro de um tipo contido, como uma classe aninhada ou uma expressão de atribuição em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="7f0c0-117">Nenhum código fora do contexto da declaração pode acessar seus `Private` elementos.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="7f0c0-118">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="7f0c0-118">**Access Modifiers.**</span></span> <span data-ttu-id="7f0c0-119">As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="7f0c0-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="7f0c0-120">Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7f0c0-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="7f0c0-121">O `Private` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="7f0c0-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7f0c0-122">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="7f0c0-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="7f0c0-123">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="7f0c0-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="7f0c0-124">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="7f0c0-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="7f0c0-125">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="7f0c0-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="7f0c0-126">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="7f0c0-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="7f0c0-127">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="7f0c0-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="7f0c0-128">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="7f0c0-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="7f0c0-129">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="7f0c0-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="7f0c0-130">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="7f0c0-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="7f0c0-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="7f0c0-131">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="7f0c0-132">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="7f0c0-132">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="7f0c0-133">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="7f0c0-133">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7f0c0-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f0c0-134">See also</span></span>

- [<span data-ttu-id="7f0c0-135">Pública</span><span class="sxs-lookup"><span data-stu-id="7f0c0-135">Public</span></span>](public.md)
- [<span data-ttu-id="7f0c0-136">Protected</span><span class="sxs-lookup"><span data-stu-id="7f0c0-136">Protected</span></span>](protected.md)
- [<span data-ttu-id="7f0c0-137">Friend</span><span class="sxs-lookup"><span data-stu-id="7f0c0-137">Friend</span></span>](friend.md)
- [<span data-ttu-id="7f0c0-138">Particular protegido</span><span class="sxs-lookup"><span data-stu-id="7f0c0-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="7f0c0-139">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="7f0c0-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="7f0c0-140">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7f0c0-140">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="7f0c0-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="7f0c0-141">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="7f0c0-142">Estruturas</span><span class="sxs-lookup"><span data-stu-id="7f0c0-142">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7f0c0-143">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="7f0c0-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
