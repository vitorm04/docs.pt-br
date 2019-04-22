---
title: Declaração de propriedade (Visual Basic)
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
ms.openlocfilehash: 7b2d388cbcd1995178adf4102520ecaa1c9b1889
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814171"
---
# <a name="property-statement"></a><span data-ttu-id="3f36f-102">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="3f36f-102">Property Statement</span></span>
<span data-ttu-id="3f36f-103">Declara o nome de uma propriedade e os procedimentos de propriedade usados para armazenar e recuperar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f36f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f36f-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="3f36f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="3f36f-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="3f36f-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-106">Optional.</span></span> <span data-ttu-id="3f36f-107">Lista de atributos que se aplicam a essa propriedade ou `Get` ou `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3f36f-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="3f36f-108">Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="3f36f-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-109">Optional.</span></span> <span data-ttu-id="3f36f-110">Especifica que essa propriedade é a propriedade padrão para a classe ou estrutura na qual ele está definido.</span><span class="sxs-lookup"><span data-stu-id="3f36f-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="3f36f-111">As propriedades padrão devem aceitar parâmetros e podem ser definidas e recuperadas sem especificar o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="3f36f-112">Se você declarar a propriedade como `Default`, você não pode usar `Private` na propriedade ou um de seus procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="3f36f-113">Opcional sobre o `Property` instrução e no máximo um da `Get` e `Set` instruções.</span><span class="sxs-lookup"><span data-stu-id="3f36f-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="3f36f-114">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="3f36f-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3f36f-115">Público</span><span class="sxs-lookup"><span data-stu-id="3f36f-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="3f36f-116">Protegido</span><span class="sxs-lookup"><span data-stu-id="3f36f-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="3f36f-117">Friend</span><span class="sxs-lookup"><span data-stu-id="3f36f-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="3f36f-118">Privado</span><span class="sxs-lookup"><span data-stu-id="3f36f-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="3f36f-119">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="3f36f-119">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md) 

    - [<span data-ttu-id="3f36f-120">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="3f36f-120">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="3f36f-121">Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-121">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="3f36f-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-122">Optional.</span></span> <span data-ttu-id="3f36f-123">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="3f36f-123">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3f36f-124">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="3f36f-124">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="3f36f-125">Substituições</span><span class="sxs-lookup"><span data-stu-id="3f36f-125">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="3f36f-126">Substituível</span><span class="sxs-lookup"><span data-stu-id="3f36f-126">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="3f36f-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3f36f-127">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="3f36f-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="3f36f-128">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="3f36f-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-129">Optional.</span></span> <span data-ttu-id="3f36f-130">Ver [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-130">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="3f36f-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-131">Optional.</span></span> <span data-ttu-id="3f36f-132">Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-132">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="3f36f-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-133">Optional.</span></span> <span data-ttu-id="3f36f-134">Ver [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-134">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="3f36f-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-135">Optional.</span></span> <span data-ttu-id="3f36f-136">Ver [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-136">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="3f36f-137">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-137">Optional.</span></span> <span data-ttu-id="3f36f-138">Ver [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-138">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="3f36f-139">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3f36f-139">Required.</span></span> <span data-ttu-id="3f36f-140">Nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-140">Name of the property.</span></span> <span data-ttu-id="3f36f-141">Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-141">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="3f36f-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-142">Optional.</span></span> <span data-ttu-id="3f36f-143">Lista de nomes de variável local que representa os parâmetros da propriedade e possíveis parâmetros adicionais do `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3f36f-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="3f36f-144">Ver [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-144">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="3f36f-145">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="3f36f-146">Tipo de dados do valor retornado por essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-146">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="3f36f-147">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-147">Optional.</span></span> <span data-ttu-id="3f36f-148">Indica que essa propriedade implementa uma ou mais propriedades, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="3f36f-149">Ver [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-149">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="3f36f-150">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="3f36f-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="3f36f-151">Lista de propriedades que está sendo implementado.</span><span class="sxs-lookup"><span data-stu-id="3f36f-151">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="3f36f-152">Cada `implementedproperty` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="3f36f-152">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="3f36f-153">Parte</span><span class="sxs-lookup"><span data-stu-id="3f36f-153">Part</span></span>|<span data-ttu-id="3f36f-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f36f-154">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="3f36f-155">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3f36f-155">Required.</span></span> <span data-ttu-id="3f36f-156">Que contém o nome de uma interface implementada por esta propriedade de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="3f36f-156">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="3f36f-157">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3f36f-157">Required.</span></span> <span data-ttu-id="3f36f-158">Nome pelo qual a propriedade é definida no `interface`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-158">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="3f36f-159">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-159">Optional.</span></span> <span data-ttu-id="3f36f-160">Necessário se a propriedade é marcada como `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-160">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="3f36f-161">Inicia uma `Get` procedimento de propriedade que é usado para retornar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="3f36f-162">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-162">Optional.</span></span> <span data-ttu-id="3f36f-163">Bloco de instruções para executar dentro de `Get` ou `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="3f36f-163">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="3f36f-164">Encerra o `Get` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-164">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="3f36f-165">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3f36f-165">Optional.</span></span> <span data-ttu-id="3f36f-166">Necessário se a propriedade é marcada como `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-166">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="3f36f-167">Inicia uma `Set` procedimento de propriedade que é usado para armazenar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-167">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="3f36f-168">Encerra o `Set` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-168">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="3f36f-169">Finaliza a definição dessa propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-169">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f36f-170">Comentários</span><span class="sxs-lookup"><span data-stu-id="3f36f-170">Remarks</span></span>  
 <span data-ttu-id="3f36f-171">O `Property` instrução introduz a declaração de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-171">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="3f36f-172">Uma propriedade pode ter um `Get` procedimento (somente leitura), um `Set` procedimento (somente gravação), ou ambos (leitura-gravação).</span><span class="sxs-lookup"><span data-stu-id="3f36f-172">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="3f36f-173">Você pode omitir as `Get` e `Set` procedimento ao usar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="3f36f-173">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="3f36f-174">Para obter mais informações, consulte [Propriedades autoimplementadas](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-174">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="3f36f-175">Você pode usar `Property` apenas no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="3f36f-175">You can use `Property` only at class level.</span></span> <span data-ttu-id="3f36f-176">Isso significa que o *contexto de declaração* para uma propriedade deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo de origem, namespace, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="3f36f-176">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="3f36f-177">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3f36f-177">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3f36f-178">Por padrão, as propriedades usam acesso público.</span><span class="sxs-lookup"><span data-stu-id="3f36f-178">By default, properties use public access.</span></span> <span data-ttu-id="3f36f-179">Você pode ajustar o nível de acesso da propriedade com um modificador de acesso a `Property` instrução e, opcionalmente, pode ajustar um dos seus procedimentos de propriedade para um nível de acesso mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="3f36f-179">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="3f36f-180">Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-180">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="3f36f-181">Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito chamada `value`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-181">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="3f36f-182">Este parâmetro contém o valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-182">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="3f36f-183">Você normalmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="3f36f-183">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3f36f-184">Regras</span><span class="sxs-lookup"><span data-stu-id="3f36f-184">Rules</span></span>  
  
-   <span data-ttu-id="3f36f-185">**Níveis de acesso mistos.**</span><span class="sxs-lookup"><span data-stu-id="3f36f-185">**Mixed Access Levels.**</span></span> <span data-ttu-id="3f36f-186">Se você estiver definindo uma propriedade de leitura / gravação, você pode, opcionalmente, especificar um nível de acesso diferentes para qualquer um de `Get` ou o `Set` procedimento, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="3f36f-186">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="3f36f-187">Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-187">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="3f36f-188">Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-188">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="3f36f-189">Se você estiver definindo uma `ReadOnly` ou `WriteOnly` propriedade, o procedimento de propriedade única (`Get` ou `Set`, respectivamente) representa todos os da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-189">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="3f36f-190">Você não pode declarar um nível de acesso diferentes para procedimento, pois isso configuraria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-190">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="3f36f-191">**Tipo de retorno.**</span><span class="sxs-lookup"><span data-stu-id="3f36f-191">**Return Type.**</span></span> <span data-ttu-id="3f36f-192">O `Property` instrução pode declarar o tipo de dados do valor que ele retorna.</span><span class="sxs-lookup"><span data-stu-id="3f36f-192">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="3f36f-193">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="3f36f-193">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="3f36f-194">Se você não especificar `returntype`, a propriedade retorna `Object`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-194">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="3f36f-195">**Implementação.**</span><span class="sxs-lookup"><span data-stu-id="3f36f-195">**Implementation.**</span></span> <span data-ttu-id="3f36f-196">Se esta propriedade usa a `Implements` deve ter a palavra-chave, a classe ou estrutura contendo um `Implements` instrução imediatamente após sua `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="3f36f-196">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="3f36f-197">O `Implements` instrução deve incluir cada interface especificada em `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="3f36f-197">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="3f36f-198">No entanto, o nome pelo qual uma interface define os `Property` (no `definedname`) não precisa ser o mesmo que o nome da propriedade (em `name`).</span><span class="sxs-lookup"><span data-stu-id="3f36f-198">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3f36f-199">Comportamento</span><span class="sxs-lookup"><span data-stu-id="3f36f-199">Behavior</span></span>  
  
-   <span data-ttu-id="3f36f-200">**Retornando de um procedimento de propriedade.**</span><span class="sxs-lookup"><span data-stu-id="3f36f-200">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="3f36f-201">Quando o `Get` ou `Set` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que a invocou.</span><span class="sxs-lookup"><span data-stu-id="3f36f-201">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="3f36f-202">O `Exit Property` e `Return` instruções fazem com que uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-202">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="3f36f-203">Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="3f36f-203">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="3f36f-204">**Valor de retorno.**</span><span class="sxs-lookup"><span data-stu-id="3f36f-204">**Return Value.**</span></span> <span data-ttu-id="3f36f-205">Para retornar um valor de uma `Get` procedimento, você pode atribuir o valor para o nome da propriedade ou incluí-lo em um `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="3f36f-205">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="3f36f-206">O exemplo a seguir atribui o valor de retorno para o nome da propriedade `quoteForTheDay` e, em seguida, usa o `Exit Property` instrução para retornar.</span><span class="sxs-lookup"><span data-stu-id="3f36f-206">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     <span data-ttu-id="3f36f-207">Se você usar `Exit Property` sem atribuir um valor para `name`, o `Get` procedimento retorna o valor padrão para o tipo de dados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3f36f-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="3f36f-208">O `Return` instrução ao mesmo tempo atribui o `Get` de valor e finaliza o procedimento de retorno de procedimento.</span><span class="sxs-lookup"><span data-stu-id="3f36f-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="3f36f-209">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="3f36f-209">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="3f36f-210">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f36f-210">Example</span></span>  
 <span data-ttu-id="3f36f-211">O exemplo a seguir declara uma propriedade em uma classe.</span><span class="sxs-lookup"><span data-stu-id="3f36f-211">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="3f36f-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f36f-212">See also</span></span>

- [<span data-ttu-id="3f36f-213">Propriedades Autoimplementadas</span><span class="sxs-lookup"><span data-stu-id="3f36f-213">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="3f36f-214">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="3f36f-214">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="3f36f-215">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="3f36f-215">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="3f36f-216">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="3f36f-216">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="3f36f-217">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f36f-217">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="3f36f-218">Padrão</span><span class="sxs-lookup"><span data-stu-id="3f36f-218">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
