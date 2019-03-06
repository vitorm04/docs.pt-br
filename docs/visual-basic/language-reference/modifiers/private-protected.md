---
title: Private protegida (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: fea43558ac0fe8181f2786b69f2621346d446b2e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376384"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="2bf0d-102">Private protegida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bf0d-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="2bf0d-103">A combinação de palavras-chave `Private Protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="2bf0d-104">Um `Private Protected` membro é acessível por todos os membros em sua classe recipiente, bem como por tipos derivados da classe recipiente, mas somente se forem encontrados em seu assembly recipiente.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="2bf0d-105">Você pode especificar `Private Protected` somente em membros de classes; não é possível aplicar `Private Protected` aos membros de uma estrutura porque as estruturas não podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="2bf0d-106">O `Private Protected` modificador de acesso é suportado pelo Visual Basic 15.5 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="2bf0d-107">Para usá-lo, você pode adicionar o seguinte elemento ao seu projeto do Visual Basic (\*. vbproj) arquivos.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="2bf0d-108">Como desde que o Visual Basic 15.5 ou posterior estiver instalado no seu sistema, ele permite que você aproveite todos os recursos de idioma com suporte pela versão mais recente do compilador do Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="2bf0d-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="2bf0d-109">Para obter mais informações, consulte [definindo a versão da linguagem Visual Basic](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="2bf0d-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2bf0d-110">No Visual Studio, selecionando a Ajuda de F1 na `private protected` fornece ajuda para o [privada](private.md) ou [protegido](protected.md).</span><span class="sxs-lookup"><span data-stu-id="2bf0d-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="2bf0d-111">O IDE escolherá o token único sob o cursor em vez da palavra composta.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="2bf0d-112">Regras</span><span class="sxs-lookup"><span data-stu-id="2bf0d-112">Rules</span></span>

- <span data-ttu-id="2bf0d-113">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="2bf0d-113">**Declaration Context.**</span></span> <span data-ttu-id="2bf0d-114">Você pode usar `Private Protected` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="2bf0d-115">Isso significa que o contexto da declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, estrutura, módulo ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="2bf0d-116">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2bf0d-116">Behavior</span></span>

- <span data-ttu-id="2bf0d-117">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="2bf0d-117">**Access Level.**</span></span> <span data-ttu-id="2bf0d-118">Todo o código em uma classe pode acessar seus elementos.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-118">All code in a class can access its elements.</span></span> <span data-ttu-id="2bf0d-119">Código em qualquer classe que deriva de uma classe base e está contido no mesmo assembly pode acessar todos os `Private Protected` elementos da classe base.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="2bf0d-120">No entanto, o código em qualquer classe que deriva de uma classe base e está contido em um assembly diferente não é possível acessar a classe base `Private Protected` elementos.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="2bf0d-121">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="2bf0d-121">**Access Modifiers.**</span></span> <span data-ttu-id="2bf0d-122">As palavras-chave que especificam o nível de acesso são chamadas *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="2bf0d-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2bf0d-123">Para obter uma comparação os modificadores de acesso, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2bf0d-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="2bf0d-124">O `Private Protected` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="2bf0d-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="2bf0d-125">[Instrução class](../../../visual-basic/language-reference/statements/class-statement.md) de uma classe aninhada</span><span class="sxs-lookup"><span data-stu-id="2bf0d-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="2bf0d-126">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="2bf0d-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="2bf0d-127">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="2bf0d-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- <span data-ttu-id="2bf0d-128">[Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) de um delegado aninhado em uma classe</span><span class="sxs-lookup"><span data-stu-id="2bf0d-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="2bf0d-129">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="2bf0d-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- <span data-ttu-id="2bf0d-130">[Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md) de uma enumeração aninhado em uma classe</span><span class="sxs-lookup"><span data-stu-id="2bf0d-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="2bf0d-131">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="2bf0d-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="2bf0d-132">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="2bf0d-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- <span data-ttu-id="2bf0d-133">[Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) de uma interface aninhada em uma classe</span><span class="sxs-lookup"><span data-stu-id="2bf0d-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="2bf0d-134">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="2bf0d-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- <span data-ttu-id="2bf0d-135">[Estrutura da instrução](../../../visual-basic/language-reference/statements/structure-statement.md) de uma estrutura aninhada em uma classe</span><span class="sxs-lookup"><span data-stu-id="2bf0d-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="2bf0d-136">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="2bf0d-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="2bf0d-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bf0d-137">See also</span></span>

- [<span data-ttu-id="2bf0d-138">Público</span><span class="sxs-lookup"><span data-stu-id="2bf0d-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="2bf0d-139">Protegido</span><span class="sxs-lookup"><span data-stu-id="2bf0d-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="2bf0d-140">Friend</span><span class="sxs-lookup"><span data-stu-id="2bf0d-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="2bf0d-141">Privado</span><span class="sxs-lookup"><span data-stu-id="2bf0d-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="2bf0d-142">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="2bf0d-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="2bf0d-143">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bf0d-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="2bf0d-144">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="2bf0d-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="2bf0d-145">Estruturas</span><span class="sxs-lookup"><span data-stu-id="2bf0d-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2bf0d-146">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="2bf0d-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
