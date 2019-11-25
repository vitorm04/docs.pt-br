---
title: Sombras
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351269"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="39f36-102">Sombras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39f36-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="39f36-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span><span class="sxs-lookup"><span data-stu-id="39f36-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="39f36-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="39f36-104">Remarks</span></span>

<span data-ttu-id="39f36-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span><span class="sxs-lookup"><span data-stu-id="39f36-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="39f36-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span><span class="sxs-lookup"><span data-stu-id="39f36-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="39f36-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span><span class="sxs-lookup"><span data-stu-id="39f36-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="39f36-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span><span class="sxs-lookup"><span data-stu-id="39f36-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="39f36-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="39f36-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="39f36-110">Regras</span><span class="sxs-lookup"><span data-stu-id="39f36-110">Rules</span></span>

- <span data-ttu-id="39f36-111">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="39f36-111">**Declaration Context.**</span></span> <span data-ttu-id="39f36-112">You can use `Shadows` only at class level.</span><span class="sxs-lookup"><span data-stu-id="39f36-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="39f36-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span><span class="sxs-lookup"><span data-stu-id="39f36-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="39f36-114">You can declare only one shadowing element in a single declaration statement.</span><span class="sxs-lookup"><span data-stu-id="39f36-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="39f36-115">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="39f36-115">**Combined Modifiers.**</span></span> <span data-ttu-id="39f36-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="39f36-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="39f36-117">**Element Types.**</span><span class="sxs-lookup"><span data-stu-id="39f36-117">**Element Types.**</span></span> <span data-ttu-id="39f36-118">You can shadow any kind of declared element with any other kind.</span><span class="sxs-lookup"><span data-stu-id="39f36-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="39f36-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span><span class="sxs-lookup"><span data-stu-id="39f36-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="39f36-120">**Accessing.**</span><span class="sxs-lookup"><span data-stu-id="39f36-120">**Accessing.**</span></span> <span data-ttu-id="39f36-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span><span class="sxs-lookup"><span data-stu-id="39f36-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="39f36-122">However, the following considerations apply.</span><span class="sxs-lookup"><span data-stu-id="39f36-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="39f36-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span><span class="sxs-lookup"><span data-stu-id="39f36-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="39f36-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span><span class="sxs-lookup"><span data-stu-id="39f36-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="39f36-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span><span class="sxs-lookup"><span data-stu-id="39f36-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="39f36-126">You can also access it through `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="39f36-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="39f36-127">The `Shadows` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="39f36-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="39f36-128">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="39f36-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="39f36-129">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="39f36-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="39f36-130">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="39f36-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="39f36-131">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="39f36-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="39f36-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="39f36-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="39f36-133">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="39f36-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="39f36-134">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="39f36-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="39f36-135">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="39f36-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="39f36-136">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="39f36-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="39f36-137">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="39f36-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="39f36-138">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="39f36-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="39f36-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="39f36-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="39f36-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39f36-140">See also</span></span>

- [<span data-ttu-id="39f36-141">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="39f36-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="39f36-142">Estático</span><span class="sxs-lookup"><span data-stu-id="39f36-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)
- [<span data-ttu-id="39f36-143">Privado</span><span class="sxs-lookup"><span data-stu-id="39f36-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="39f36-144">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="39f36-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="39f36-145">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="39f36-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="39f36-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="39f36-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="39f36-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="39f36-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="39f36-148">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="39f36-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="39f36-149">Substituível</span><span class="sxs-lookup"><span data-stu-id="39f36-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="39f36-150">Substituições</span><span class="sxs-lookup"><span data-stu-id="39f36-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="39f36-151">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39f36-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
