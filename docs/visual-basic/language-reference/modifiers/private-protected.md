---
title: Protegido de forma particular
ms.date: 05/10/2018
f1_keywords:
- vb.PrivateProtected
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 8ad1509da71bc80b33700d363ddd4569a0965dff
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303459"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="89cfb-102">Privado protegido (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89cfb-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="89cfb-103">A combinação de palavras-chave `Private Protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="89cfb-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="89cfb-104">Um `Private Protected` membro é acessível por todos os membros em sua classe que o contém, bem como por tipos derivados da classe que a contém, mas somente se eles forem encontrados em seu assembly de contenção.</span><span class="sxs-lookup"><span data-stu-id="89cfb-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="89cfb-105">Você pode especificar `Private Protected` somente membros de classes; não é possível aplicar `Private Protected` a membros de uma estrutura porque as estruturas não podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="89cfb-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="89cfb-106">O `Private Protected` modificador de acesso é suportado pelo Visual Basic 15,5 e posterior.</span><span class="sxs-lookup"><span data-stu-id="89cfb-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="89cfb-107">Para usá-lo, você pode adicionar o seguinte elemento ao seu arquivo de Visual Basic projeto ( \* . vbproj).</span><span class="sxs-lookup"><span data-stu-id="89cfb-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="89cfb-108">Desde que Visual Basic 15,5 ou posterior esteja instalado no seu sistema, ele permite que você aproveite todos os recursos de linguagem suportados pela versão mais recente do compilador de Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="89cfb-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="89cfb-109">Para obter mais informações, consulte [definindo a versão do idioma do Visual Basic](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="89cfb-109">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="89cfb-110">No Visual Studio, a seleção de ajuda F1 no `private protected` fornece ajuda para [privado](private.md) ou [protegido](protected.md).</span><span class="sxs-lookup"><span data-stu-id="89cfb-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="89cfb-111">O IDE escolhe o único token sob o cursor em vez da palavra composta.</span><span class="sxs-lookup"><span data-stu-id="89cfb-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="89cfb-112">Regras</span><span class="sxs-lookup"><span data-stu-id="89cfb-112">Rules</span></span>

- <span data-ttu-id="89cfb-113">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="89cfb-113">**Declaration Context.**</span></span> <span data-ttu-id="89cfb-114">Você pode usar `Private Protected` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="89cfb-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="89cfb-115">Isso significa que o contexto de declaração para um `Protected` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="89cfb-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="89cfb-116">Comportamento</span><span class="sxs-lookup"><span data-stu-id="89cfb-116">Behavior</span></span>

- <span data-ttu-id="89cfb-117">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="89cfb-117">**Access Level.**</span></span> <span data-ttu-id="89cfb-118">Todo o código em uma classe pode acessar seus elementos.</span><span class="sxs-lookup"><span data-stu-id="89cfb-118">All code in a class can access its elements.</span></span> <span data-ttu-id="89cfb-119">O código em qualquer classe que deriva de uma classe base e está contido no mesmo assembly pode acessar todos os `Private Protected` elementos da classe base.</span><span class="sxs-lookup"><span data-stu-id="89cfb-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="89cfb-120">No entanto, o código em qualquer classe derivada de uma classe base e está contido em um assembly diferente não pode acessar os elementos da classe base `Private Protected` .</span><span class="sxs-lookup"><span data-stu-id="89cfb-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="89cfb-121">**Modificadores de acesso.**</span><span class="sxs-lookup"><span data-stu-id="89cfb-121">**Access Modifiers.**</span></span> <span data-ttu-id="89cfb-122">As palavras-chave que especificam o nível de acesso são chamadas de *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="89cfb-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="89cfb-123">Para obter uma comparação dos modificadores de acesso, consulte [níveis de acesso em Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="89cfb-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="89cfb-124">O `Private Protected` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="89cfb-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="89cfb-125">[Declaração de classe](../statements/class-statement.md) de uma classe aninhada</span><span class="sxs-lookup"><span data-stu-id="89cfb-125">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="89cfb-126">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="89cfb-126">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="89cfb-127">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="89cfb-127">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="89cfb-128">[Instrução delegate](../statements/delegate-statement.md) de um delegado aninhado em uma classe</span><span class="sxs-lookup"><span data-stu-id="89cfb-128">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="89cfb-129">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="89cfb-129">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="89cfb-130">[Instrução enum](../statements/enum-statement.md) de uma enumeração aninhada em uma classe</span><span class="sxs-lookup"><span data-stu-id="89cfb-130">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="89cfb-131">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="89cfb-131">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="89cfb-132">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="89cfb-132">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="89cfb-133">[Declaração de interface](../statements/interface-statement.md) de uma interface aninhada em uma classe</span><span class="sxs-lookup"><span data-stu-id="89cfb-133">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="89cfb-134">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="89cfb-134">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="89cfb-135">[Instrução de estrutura](../statements/structure-statement.md) de uma estrutura aninhada em uma classe</span><span class="sxs-lookup"><span data-stu-id="89cfb-135">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="89cfb-136">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="89cfb-136">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="89cfb-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="89cfb-137">See also</span></span>

- [<span data-ttu-id="89cfb-138">Pública</span><span class="sxs-lookup"><span data-stu-id="89cfb-138">Public</span></span>](public.md)
- [<span data-ttu-id="89cfb-139">Protected</span><span class="sxs-lookup"><span data-stu-id="89cfb-139">Protected</span></span>](protected.md)
- [<span data-ttu-id="89cfb-140">Público</span><span class="sxs-lookup"><span data-stu-id="89cfb-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="89cfb-141">Privada</span><span class="sxs-lookup"><span data-stu-id="89cfb-141">Private</span></span>](private.md)
- [<span data-ttu-id="89cfb-142">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="89cfb-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="89cfb-143">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89cfb-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="89cfb-144">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="89cfb-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="89cfb-145">Estruturas</span><span class="sxs-lookup"><span data-stu-id="89cfb-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="89cfb-146">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="89cfb-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
