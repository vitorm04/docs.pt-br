---
title: Instrução Property (Visual Basic)
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
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332744"
---
# <a name="property-statement"></a><span data-ttu-id="cf279-102">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="cf279-102">Property Statement</span></span>

<span data-ttu-id="cf279-103">Declara o nome de uma propriedade e os procedimentos de propriedade usados para armazenar e recuperar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf279-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf279-104">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="cf279-105">Partes</span><span class="sxs-lookup"><span data-stu-id="cf279-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="cf279-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-106">Optional.</span></span> <span data-ttu-id="cf279-107">Lista de atributos que se aplicam a esta propriedade ou ao procedimento `Get` ou `Set`.</span><span class="sxs-lookup"><span data-stu-id="cf279-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="cf279-108">Consulte a [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="cf279-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-109">Optional.</span></span> <span data-ttu-id="cf279-110">Especifica que essa propriedade é a propriedade padrão para a classe ou estrutura na qual ela está definida.</span><span class="sxs-lookup"><span data-stu-id="cf279-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="cf279-111">As propriedades padrão devem aceitar parâmetros e podem ser definidas e recuperadas sem especificar o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="cf279-112">Se você declarar a propriedade como `Default`, não poderá usar `Private` na propriedade ou em qualquer um dos seus procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="cf279-113">Opcional na instrução `Property` e em no máximo uma das instruções `Get` e `Set`.</span><span class="sxs-lookup"><span data-stu-id="cf279-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="cf279-114">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="cf279-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="cf279-115">Público</span><span class="sxs-lookup"><span data-stu-id="cf279-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="cf279-116">Protegido</span><span class="sxs-lookup"><span data-stu-id="cf279-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="cf279-117">Friend</span><span class="sxs-lookup"><span data-stu-id="cf279-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="cf279-118">Privado</span><span class="sxs-lookup"><span data-stu-id="cf279-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="cf279-119">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="cf279-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="cf279-120">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="cf279-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="cf279-121">Consulte [níveis de acesso em Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="cf279-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-122">Optional.</span></span> <span data-ttu-id="cf279-123">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="cf279-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="cf279-124">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="cf279-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="cf279-125">Substituições</span><span class="sxs-lookup"><span data-stu-id="cf279-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="cf279-126">Substituível</span><span class="sxs-lookup"><span data-stu-id="cf279-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="cf279-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="cf279-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="cf279-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="cf279-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="cf279-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-129">Optional.</span></span> <span data-ttu-id="cf279-130">Consulte [compartilhado](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="cf279-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-131">Optional.</span></span> <span data-ttu-id="cf279-132">Consulte [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="cf279-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-133">Optional.</span></span> <span data-ttu-id="cf279-134">Consulte [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="cf279-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-135">Optional.</span></span> <span data-ttu-id="cf279-136">Consulte [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="cf279-137">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-137">Optional.</span></span> <span data-ttu-id="cf279-138">Consulte [iterador](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="cf279-139">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cf279-139">Required.</span></span> <span data-ttu-id="cf279-140">Nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-140">Name of the property.</span></span> <span data-ttu-id="cf279-141">Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="cf279-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-142">Optional.</span></span> <span data-ttu-id="cf279-143">Lista de nomes de variáveis locais que representam os parâmetros dessa propriedade e possíveis parâmetros adicionais do procedimento `Set`.</span><span class="sxs-lookup"><span data-stu-id="cf279-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="cf279-144">Consulte a [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="cf279-145">Necessário se `Option Strict` for `On`.</span><span class="sxs-lookup"><span data-stu-id="cf279-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="cf279-146">Tipo de dados do valor retornado por essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="cf279-147">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-147">Optional.</span></span> <span data-ttu-id="cf279-148">Indica que essa propriedade implementa uma ou mais propriedades, cada uma definida em uma interface implementada por essa propriedade que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="cf279-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="cf279-149">Consulte a [instrução Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="cf279-150">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="cf279-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="cf279-151">Lista de propriedades que estão sendo implementadas.</span><span class="sxs-lookup"><span data-stu-id="cf279-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="cf279-152">Cada `implementedproperty` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="cf279-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="cf279-153">Parte</span><span class="sxs-lookup"><span data-stu-id="cf279-153">Part</span></span>|<span data-ttu-id="cf279-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf279-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="cf279-155">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cf279-155">Required.</span></span> <span data-ttu-id="cf279-156">Nome de uma interface implementada por essa propriedade que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="cf279-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="cf279-157">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cf279-157">Required.</span></span> <span data-ttu-id="cf279-158">Nome pelo qual a propriedade é definida em `interface`.</span><span class="sxs-lookup"><span data-stu-id="cf279-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="cf279-159">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-159">Optional.</span></span> <span data-ttu-id="cf279-160">Obrigatório se a propriedade estiver marcada `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="cf279-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="cf279-161">Inicia um procedimento de propriedade `Get` que é usado para retornar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="cf279-162">A instrução `Get` não é usada com [Propriedades implementadas automaticamente](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="cf279-163">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-163">Optional.</span></span> <span data-ttu-id="cf279-164">Bloco de instruções a serem executadas dentro do procedimento `Get` ou `Set`.</span><span class="sxs-lookup"><span data-stu-id="cf279-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="cf279-165">Encerra o procedimento de propriedade `Get`.</span><span class="sxs-lookup"><span data-stu-id="cf279-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="cf279-166">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cf279-166">Optional.</span></span> <span data-ttu-id="cf279-167">Obrigatório se a propriedade estiver marcada `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="cf279-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="cf279-168">Inicia um procedimento de propriedade `Set` que é usado para armazenar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="cf279-169">A instrução `Set` não é usada com [Propriedades implementadas automaticamente](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="cf279-170">Encerra o procedimento de propriedade `Set`.</span><span class="sxs-lookup"><span data-stu-id="cf279-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="cf279-171">Encerra a definição desta propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf279-172">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf279-172">Remarks</span></span>

<span data-ttu-id="cf279-173">A instrução `Property` apresenta a declaração de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="cf279-174">Uma propriedade pode ter um procedimento `Get` (somente leitura), um procedimento `Set` (somente gravação) ou ambos (leitura-gravação).</span><span class="sxs-lookup"><span data-stu-id="cf279-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="cf279-175">Você pode omitir o `Get` e o procedimento `Set` ao usar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="cf279-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="cf279-176">Para obter mais informações, consulte [Propriedades autoimplementadas](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="cf279-177">Você pode usar `Property` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="cf279-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="cf279-178">Isso significa que o *contexto de declaração* para uma propriedade deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo de origem, namespace, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="cf279-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="cf279-179">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cf279-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="cf279-180">Por padrão, as propriedades usam acesso público.</span><span class="sxs-lookup"><span data-stu-id="cf279-180">By default, properties use public access.</span></span> <span data-ttu-id="cf279-181">Você pode ajustar o nível de acesso de uma propriedade com um modificador de acesso na instrução `Property` e, opcionalmente, pode ajustar um de seus procedimentos de propriedade para um nível de acesso mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="cf279-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="cf279-182">Visual Basic passa um parâmetro para o procedimento `Set` durante as atribuições de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="cf279-183">Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usará um parâmetro implícito denominado `value`.</span><span class="sxs-lookup"><span data-stu-id="cf279-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="cf279-184">Esse parâmetro contém o valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="cf279-185">Normalmente, você armazena esse valor em uma variável local privada e retorna-o sempre que o procedimento `Get` for chamado.</span><span class="sxs-lookup"><span data-stu-id="cf279-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="cf279-186">Regras</span><span class="sxs-lookup"><span data-stu-id="cf279-186">Rules</span></span>

- <span data-ttu-id="cf279-187">**Níveis de acesso misto.**</span><span class="sxs-lookup"><span data-stu-id="cf279-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="cf279-188">Se você estiver definindo uma propriedade de leitura/gravação, você pode opcionalmente especificar um nível de acesso diferente para o procedimento `Get` ou `Set`, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="cf279-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="cf279-189">Se você fizer isso, o nível de acesso do procedimento deverá ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="cf279-190">Por exemplo, se a propriedade for declarada `Friend`, você poderá declarar o procedimento `Set` `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="cf279-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="cf279-191">Se você estiver definindo uma propriedade `ReadOnly` ou `WriteOnly`, o procedimento de propriedade única (`Get` ou `Set`, respectivamente) representará toda a propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="cf279-192">Você não pode declarar um nível de acesso diferente para tal procedimento, pois isso definiria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="cf279-193">**Tipo de retorno.**</span><span class="sxs-lookup"><span data-stu-id="cf279-193">**Return Type.**</span></span> <span data-ttu-id="cf279-194">A instrução `Property` pode declarar o tipo de dados do valor que ele retorna.</span><span class="sxs-lookup"><span data-stu-id="cf279-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="cf279-195">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="cf279-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="cf279-196">Se você não especificar `returntype`, a propriedade retornará `Object`.</span><span class="sxs-lookup"><span data-stu-id="cf279-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="cf279-197">**Implementação.**</span><span class="sxs-lookup"><span data-stu-id="cf279-197">**Implementation.**</span></span> <span data-ttu-id="cf279-198">Se essa propriedade usar a palavra-chave `Implements`, a classe contendo ou a estrutura deverá ter uma instrução `Implements` imediatamente após sua instrução `Class` ou `Structure`.</span><span class="sxs-lookup"><span data-stu-id="cf279-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="cf279-199">A instrução `Implements` deve incluir cada interface especificada em `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="cf279-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="cf279-200">No entanto, o nome pelo qual uma interface define o `Property` (em `definedname`) não precisa ser o mesmo que o nome dessa propriedade (em `name`).</span><span class="sxs-lookup"><span data-stu-id="cf279-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="cf279-201">Comportamento</span><span class="sxs-lookup"><span data-stu-id="cf279-201">Behavior</span></span>

- <span data-ttu-id="cf279-202">**Retornando de um procedimento de propriedade.**</span><span class="sxs-lookup"><span data-stu-id="cf279-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="cf279-203">Quando o procedimento `Get` ou `Set` retorna ao código de chamada, a execução continua com a instrução após a instrução que o invocou.</span><span class="sxs-lookup"><span data-stu-id="cf279-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="cf279-204">As instruções `Exit Property` e `Return` causam uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="cf279-205">Qualquer número de instruções `Exit Property` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar instruções `Exit Property` e `Return`.</span><span class="sxs-lookup"><span data-stu-id="cf279-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="cf279-206">**Valor de retorno.**</span><span class="sxs-lookup"><span data-stu-id="cf279-206">**Return Value.**</span></span> <span data-ttu-id="cf279-207">Para retornar um valor de um procedimento `Get`, você pode atribuir o valor ao nome da propriedade ou incluí-lo em uma instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="cf279-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="cf279-208">O exemplo a seguir atribui o valor de retorno ao nome da propriedade `quoteForTheDay` e, em seguida, usa a instrução `Exit Property` para retornar.</span><span class="sxs-lookup"><span data-stu-id="cf279-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="cf279-209">Se você usar `Exit Property` sem atribuir um valor a `name`, o procedimento `Get` retornará o valor padrão para o tipo de dados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="cf279-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="cf279-210">A instrução `Return` ao mesmo tempo atribui o valor de retorno do procedimento `Get` e sai do procedimento.</span><span class="sxs-lookup"><span data-stu-id="cf279-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="cf279-211">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="cf279-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="cf279-212">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf279-212">Example</span></span>

<span data-ttu-id="cf279-213">O exemplo a seguir declara uma propriedade em uma classe.</span><span class="sxs-lookup"><span data-stu-id="cf279-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="cf279-214">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf279-214">See also</span></span>

- [<span data-ttu-id="cf279-215">Propriedades Autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="cf279-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="cf279-216">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="cf279-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="cf279-217">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="cf279-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="cf279-218">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="cf279-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="cf279-219">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf279-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="cf279-220">Padrão</span><span class="sxs-lookup"><span data-stu-id="cf279-220">Default</span></span>](../modifiers/default.md)
