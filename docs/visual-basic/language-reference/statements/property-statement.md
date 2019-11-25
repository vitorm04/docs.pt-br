---
title: Instrução Property
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 80bce2442d96ecb9c548a88c8e5ee44c6258473b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346751"
---
# <a name="property-statement"></a><span data-ttu-id="d7490-102">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="d7490-102">Property Statement</span></span>

<span data-ttu-id="d7490-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span><span class="sxs-lookup"><span data-stu-id="d7490-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7490-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7490-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="d7490-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d7490-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="d7490-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-106">Optional.</span></span> <span data-ttu-id="d7490-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="d7490-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="d7490-108">See [Attribute List](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="d7490-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-109">Optional.</span></span> <span data-ttu-id="d7490-110">Specifies that this property is the default property for the class or structure on which it is defined.</span><span class="sxs-lookup"><span data-stu-id="d7490-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="d7490-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span><span class="sxs-lookup"><span data-stu-id="d7490-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="d7490-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span><span class="sxs-lookup"><span data-stu-id="d7490-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="d7490-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span><span class="sxs-lookup"><span data-stu-id="d7490-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="d7490-114">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="d7490-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="d7490-115">Público</span><span class="sxs-lookup"><span data-stu-id="d7490-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="d7490-116">Protegido</span><span class="sxs-lookup"><span data-stu-id="d7490-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="d7490-117">Friend</span><span class="sxs-lookup"><span data-stu-id="d7490-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="d7490-118">Privado</span><span class="sxs-lookup"><span data-stu-id="d7490-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="d7490-119">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="d7490-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="d7490-120">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="d7490-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="d7490-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="d7490-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-122">Optional.</span></span> <span data-ttu-id="d7490-123">Can be one of the following:</span><span class="sxs-lookup"><span data-stu-id="d7490-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="d7490-124">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="d7490-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="d7490-125">Substituições</span><span class="sxs-lookup"><span data-stu-id="d7490-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="d7490-126">Substituível</span><span class="sxs-lookup"><span data-stu-id="d7490-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="d7490-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d7490-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="d7490-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="d7490-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="d7490-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-129">Optional.</span></span> <span data-ttu-id="d7490-130">See [Shared](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="d7490-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-131">Optional.</span></span> <span data-ttu-id="d7490-132">See [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="d7490-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-133">Optional.</span></span> <span data-ttu-id="d7490-134">See [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="d7490-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-135">Optional.</span></span> <span data-ttu-id="d7490-136">See [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="d7490-137">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-137">Optional.</span></span> <span data-ttu-id="d7490-138">See [Iterator](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="d7490-139">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d7490-139">Required.</span></span> <span data-ttu-id="d7490-140">Nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7490-140">Name of the property.</span></span> <span data-ttu-id="d7490-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="d7490-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-142">Optional.</span></span> <span data-ttu-id="d7490-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="d7490-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="d7490-144">See [Parameter List](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="d7490-145">Required if `Option Strict` is `On`.</span><span class="sxs-lookup"><span data-stu-id="d7490-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="d7490-146">Data type of the value returned by this property.</span><span class="sxs-lookup"><span data-stu-id="d7490-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="d7490-147">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-147">Optional.</span></span> <span data-ttu-id="d7490-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="d7490-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="d7490-149">See [Implements Statement](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="d7490-150">Required if `Implements` is supplied.</span><span class="sxs-lookup"><span data-stu-id="d7490-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="d7490-151">List of properties being implemented.</span><span class="sxs-lookup"><span data-stu-id="d7490-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="d7490-152">Each `implementedproperty` has the following syntax and parts:</span><span class="sxs-lookup"><span data-stu-id="d7490-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="d7490-153">Parte</span><span class="sxs-lookup"><span data-stu-id="d7490-153">Part</span></span>|<span data-ttu-id="d7490-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7490-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="d7490-155">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d7490-155">Required.</span></span> <span data-ttu-id="d7490-156">Name of an interface implemented by this property's containing class or structure.</span><span class="sxs-lookup"><span data-stu-id="d7490-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="d7490-157">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d7490-157">Required.</span></span> <span data-ttu-id="d7490-158">Name by which the property is defined in `interface`.</span><span class="sxs-lookup"><span data-stu-id="d7490-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="d7490-159">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-159">Optional.</span></span> <span data-ttu-id="d7490-160">Required if the property is marked `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="d7490-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="d7490-161">Starts a `Get` property procedure that is used to return the value of the property.</span><span class="sxs-lookup"><span data-stu-id="d7490-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="d7490-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="d7490-163">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-163">Optional.</span></span> <span data-ttu-id="d7490-164">Block of statements to run within the `Get` or `Set` procedure.</span><span class="sxs-lookup"><span data-stu-id="d7490-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="d7490-165">Terminates the `Get` property procedure.</span><span class="sxs-lookup"><span data-stu-id="d7490-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="d7490-166">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d7490-166">Optional.</span></span> <span data-ttu-id="d7490-167">Required if the property is marked `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="d7490-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="d7490-168">Starts a `Set` property procedure that is used to store the value of the property.</span><span class="sxs-lookup"><span data-stu-id="d7490-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="d7490-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="d7490-170">Terminates the `Set` property procedure.</span><span class="sxs-lookup"><span data-stu-id="d7490-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="d7490-171">Terminates the definition of this property.</span><span class="sxs-lookup"><span data-stu-id="d7490-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="d7490-172">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7490-172">Remarks</span></span>

<span data-ttu-id="d7490-173">The `Property` statement introduces the declaration of a property.</span><span class="sxs-lookup"><span data-stu-id="d7490-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="d7490-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span><span class="sxs-lookup"><span data-stu-id="d7490-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="d7490-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span><span class="sxs-lookup"><span data-stu-id="d7490-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="d7490-176">Para obter mais informações, consulte [Propriedades autoimplementadas](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="d7490-177">You can use `Property` only at class level.</span><span class="sxs-lookup"><span data-stu-id="d7490-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="d7490-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span><span class="sxs-lookup"><span data-stu-id="d7490-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="d7490-179">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d7490-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="d7490-180">By default, properties use public access.</span><span class="sxs-lookup"><span data-stu-id="d7490-180">By default, properties use public access.</span></span> <span data-ttu-id="d7490-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span><span class="sxs-lookup"><span data-stu-id="d7490-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="d7490-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span><span class="sxs-lookup"><span data-stu-id="d7490-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="d7490-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span><span class="sxs-lookup"><span data-stu-id="d7490-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="d7490-184">This parameter holds the value to be assigned to the property.</span><span class="sxs-lookup"><span data-stu-id="d7490-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="d7490-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span><span class="sxs-lookup"><span data-stu-id="d7490-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="d7490-186">Regras</span><span class="sxs-lookup"><span data-stu-id="d7490-186">Rules</span></span>

- <span data-ttu-id="d7490-187">**Mixed Access Levels.**</span><span class="sxs-lookup"><span data-stu-id="d7490-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="d7490-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span><span class="sxs-lookup"><span data-stu-id="d7490-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="d7490-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span><span class="sxs-lookup"><span data-stu-id="d7490-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="d7490-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span><span class="sxs-lookup"><span data-stu-id="d7490-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="d7490-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span><span class="sxs-lookup"><span data-stu-id="d7490-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="d7490-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span><span class="sxs-lookup"><span data-stu-id="d7490-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="d7490-193">**Return Type.**</span><span class="sxs-lookup"><span data-stu-id="d7490-193">**Return Type.**</span></span> <span data-ttu-id="d7490-194">The `Property` statement can declare the data type of the value it returns.</span><span class="sxs-lookup"><span data-stu-id="d7490-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="d7490-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span><span class="sxs-lookup"><span data-stu-id="d7490-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="d7490-196">If you do not specify `returntype`, the property returns `Object`.</span><span class="sxs-lookup"><span data-stu-id="d7490-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="d7490-197">**Implementation.**</span><span class="sxs-lookup"><span data-stu-id="d7490-197">**Implementation.**</span></span> <span data-ttu-id="d7490-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span><span class="sxs-lookup"><span data-stu-id="d7490-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="d7490-199">The `Implements` statement must include each interface specified in `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="d7490-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="d7490-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span><span class="sxs-lookup"><span data-stu-id="d7490-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="d7490-201">Comportamento</span><span class="sxs-lookup"><span data-stu-id="d7490-201">Behavior</span></span>

- <span data-ttu-id="d7490-202">**Returning from a Property Procedure.**</span><span class="sxs-lookup"><span data-stu-id="d7490-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="d7490-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span><span class="sxs-lookup"><span data-stu-id="d7490-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="d7490-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span><span class="sxs-lookup"><span data-stu-id="d7490-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="d7490-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span><span class="sxs-lookup"><span data-stu-id="d7490-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="d7490-206">**Return Value.**</span><span class="sxs-lookup"><span data-stu-id="d7490-206">**Return Value.**</span></span> <span data-ttu-id="d7490-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span><span class="sxs-lookup"><span data-stu-id="d7490-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="d7490-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span><span class="sxs-lookup"><span data-stu-id="d7490-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="d7490-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span><span class="sxs-lookup"><span data-stu-id="d7490-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="d7490-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span><span class="sxs-lookup"><span data-stu-id="d7490-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="d7490-211">The following example shows this.</span><span class="sxs-lookup"><span data-stu-id="d7490-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="d7490-212">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7490-212">Example</span></span>

<span data-ttu-id="d7490-213">The following example declares a property in a class.</span><span class="sxs-lookup"><span data-stu-id="d7490-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="d7490-214">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7490-214">See also</span></span>

- [<span data-ttu-id="d7490-215">Propriedades Autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="d7490-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="d7490-216">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="d7490-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="d7490-217">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="d7490-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="d7490-218">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="d7490-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="d7490-219">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7490-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="d7490-220">Padrão</span><span class="sxs-lookup"><span data-stu-id="d7490-220">Default</span></span>](../modifiers/default.md)
