---
title: Privado protegido (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="58519-102">Privado protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58519-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="58519-103">O `Private Protected` combinação de palavra-chave é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="58519-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="58519-104">Um `Private Protected` membro é acessado por todos os membros em sua classe, bem como por tipos derivados da classe que contém, mas somente se forem encontrados em seu assembly que contém.</span><span class="sxs-lookup"><span data-stu-id="58519-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="58519-105">Você pode especificar `Private Protected` somente em membros de classes; não é possível aplicar `Private Protected` para membros de uma estrutura como estruturas não podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="58519-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="58519-106">O `Private Protected` modificador de acesso é suportado pelo Visual Basic 15,5 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="58519-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="58519-107">Para usá-lo, você pode adicionar o elemento a seguir para o arquivo de projeto (\*. vbproj) do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="58519-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="58519-108">Como enquanto 15,5 do Visual Basic ou posterior está instalado em seu sistema, permite aproveitar todos os recursos de idioma com suporte pela versão mais recente do compilador do Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="58519-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="58519-109">No Visual Studio, selecionando Ajuda F1 em `private protected` fornece ajuda para o [privada](private.md) ou [protegido](protected.md).</span><span class="sxs-lookup"><span data-stu-id="58519-109">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="58519-110">O IDE adota o token único sob o cursor em vez da palavra composta.</span><span class="sxs-lookup"><span data-stu-id="58519-110">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="58519-111">Regras</span><span class="sxs-lookup"><span data-stu-id="58519-111">Rules</span></span>

- <span data-ttu-id="58519-112">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="58519-112">**Declaration Context.**</span></span> <span data-ttu-id="58519-113">Você pode usar `Private Protected` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="58519-113">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="58519-114">Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="58519-114">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="58519-115">Comportamento</span><span class="sxs-lookup"><span data-stu-id="58519-115">Behavior</span></span>

- <span data-ttu-id="58519-116">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="58519-116">**Access Level.**</span></span> <span data-ttu-id="58519-117">Todo o código em uma classe pode acessar seus elementos.</span><span class="sxs-lookup"><span data-stu-id="58519-117">All code in a class can access its elements.</span></span> <span data-ttu-id="58519-118">O código em qualquer classe que deriva de uma classe base e está contido no mesmo assembly pode acessar todos os `Private Protected` elementos da classe base.</span><span class="sxs-lookup"><span data-stu-id="58519-118">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="58519-119">No entanto, o código em qualquer classe que deriva de uma classe base e está contido em um assembly diferente não pode acessar a classe base `Private Protected` elementos.</span><span class="sxs-lookup"><span data-stu-id="58519-119">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="58519-120">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="58519-120">**Access Modifiers.**</span></span> <span data-ttu-id="58519-121">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="58519-121">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="58519-122">Para uma comparação entre os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="58519-122">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="58519-123">O `Private Protected` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="58519-123">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="58519-124">[Instrução class](../../../visual-basic/language-reference/statements/class-statement.md) de uma classe aninhada</span><span class="sxs-lookup"><span data-stu-id="58519-124">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="58519-125">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="58519-125">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="58519-126">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="58519-126">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="58519-127">[Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) de um delegado aninhado em uma classe</span><span class="sxs-lookup"><span data-stu-id="58519-127">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="58519-128">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="58519-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="58519-129">[Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md) de um eumeration aninhados em uma classe</span><span class="sxs-lookup"><span data-stu-id="58519-129">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="58519-130">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="58519-130">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="58519-131">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="58519-131">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="58519-132">[Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) de uma interface aninhada em uma classe</span><span class="sxs-lookup"><span data-stu-id="58519-132">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="58519-133">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="58519-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="58519-134">[Declaração de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md) de uma estrutura aninhada em uma classe</span><span class="sxs-lookup"><span data-stu-id="58519-134">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="58519-135">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="58519-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="58519-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58519-136">See Also</span></span>

[<span data-ttu-id="58519-137">Público</span><span class="sxs-lookup"><span data-stu-id="58519-137">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="58519-138">Protegido</span><span class="sxs-lookup"><span data-stu-id="58519-138">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="58519-139">[Friend](friend.md) </span><span class="sxs-lookup"><span data-stu-id="58519-139">[Friend](friend.md) </span></span>  
[<span data-ttu-id="58519-140">Privado</span><span class="sxs-lookup"><span data-stu-id="58519-140">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="58519-141">[Friend protegido](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="58519-141">[Protected Friend](./protected-friend.md) </span></span>  
[<span data-ttu-id="58519-142">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58519-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="58519-143">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="58519-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="58519-144">Estruturas</span><span class="sxs-lookup"><span data-stu-id="58519-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="58519-145">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="58519-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
