---
title: Sobrecargas
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 44823b409cfa81dc889aabacf101fac90bf851e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351404"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="da48a-102">Sobrecargas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da48a-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="da48a-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span><span class="sxs-lookup"><span data-stu-id="da48a-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="da48a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="da48a-104">Remarks</span></span>

<span data-ttu-id="da48a-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span><span class="sxs-lookup"><span data-stu-id="da48a-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="da48a-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span><span class="sxs-lookup"><span data-stu-id="da48a-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="da48a-107">Regras</span><span class="sxs-lookup"><span data-stu-id="da48a-107">Rules</span></span>

- <span data-ttu-id="da48a-108">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="da48a-108">**Declaration Context.**</span></span> <span data-ttu-id="da48a-109">You can use `Overloads` only in a property or procedure declaration statement.</span><span class="sxs-lookup"><span data-stu-id="da48a-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="da48a-110">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="da48a-110">**Combined Modifiers.**</span></span> <span data-ttu-id="da48a-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span><span class="sxs-lookup"><span data-stu-id="da48a-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="da48a-112">**Required Differences.**</span><span class="sxs-lookup"><span data-stu-id="da48a-112">**Required Differences.**</span></span> <span data-ttu-id="da48a-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span><span class="sxs-lookup"><span data-stu-id="da48a-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="da48a-114">The signature comprises the property or procedure name together with the following:</span><span class="sxs-lookup"><span data-stu-id="da48a-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="da48a-115">the number of parameters</span><span class="sxs-lookup"><span data-stu-id="da48a-115">the number of parameters</span></span>

  - <span data-ttu-id="da48a-116">the order of the parameters</span><span class="sxs-lookup"><span data-stu-id="da48a-116">the order of the parameters</span></span>

  - <span data-ttu-id="da48a-117">the data types of the parameters</span><span class="sxs-lookup"><span data-stu-id="da48a-117">the data types of the parameters</span></span>

  - <span data-ttu-id="da48a-118">the number of type parameters (for a generic procedure)</span><span class="sxs-lookup"><span data-stu-id="da48a-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="da48a-119">the return type (only for a conversion operator procedure)</span><span class="sxs-lookup"><span data-stu-id="da48a-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="da48a-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span><span class="sxs-lookup"><span data-stu-id="da48a-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="da48a-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span><span class="sxs-lookup"><span data-stu-id="da48a-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="da48a-122">**Disallowed Differences.**</span><span class="sxs-lookup"><span data-stu-id="da48a-122">**Disallowed Differences.**</span></span> <span data-ttu-id="da48a-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span><span class="sxs-lookup"><span data-stu-id="da48a-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="da48a-124">whether or not it returns a value (for a procedure)</span><span class="sxs-lookup"><span data-stu-id="da48a-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="da48a-125">the data type of the return value (except for a conversion operator)</span><span class="sxs-lookup"><span data-stu-id="da48a-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="da48a-126">the names of the parameters or type parameters</span><span class="sxs-lookup"><span data-stu-id="da48a-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="da48a-127">the constraints on the type parameters (for a generic procedure)</span><span class="sxs-lookup"><span data-stu-id="da48a-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="da48a-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span><span class="sxs-lookup"><span data-stu-id="da48a-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="da48a-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span><span class="sxs-lookup"><span data-stu-id="da48a-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="da48a-130">**Optional Modifier.**</span><span class="sxs-lookup"><span data-stu-id="da48a-130">**Optional Modifier.**</span></span> <span data-ttu-id="da48a-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span><span class="sxs-lookup"><span data-stu-id="da48a-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="da48a-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span><span class="sxs-lookup"><span data-stu-id="da48a-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="da48a-133">**Shadowing and Overloading.**</span><span class="sxs-lookup"><span data-stu-id="da48a-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="da48a-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span><span class="sxs-lookup"><span data-stu-id="da48a-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="da48a-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span><span class="sxs-lookup"><span data-stu-id="da48a-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="da48a-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span><span class="sxs-lookup"><span data-stu-id="da48a-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="da48a-137">The `Overloads` modifier can be used in these contexts:</span><span class="sxs-lookup"><span data-stu-id="da48a-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="da48a-138">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="da48a-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="da48a-139">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="da48a-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)

- [<span data-ttu-id="da48a-140">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="da48a-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="da48a-141">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="da48a-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="da48a-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da48a-142">See also</span></span>

- [<span data-ttu-id="da48a-143">Sombras</span><span class="sxs-lookup"><span data-stu-id="da48a-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="da48a-144">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="da48a-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="da48a-145">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da48a-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="da48a-146">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="da48a-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="da48a-147">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="da48a-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
