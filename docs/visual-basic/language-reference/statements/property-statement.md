---
title: "Instrução Property | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
dev_langs:
- VB
helpviewer_keywords:
- Property statement
- default modifier
- property procedures, Property statements
- Property keyword
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: dbd779b4b6a1dd167e8581066b0fbe034cd2d8f2
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="property-statement"></a><span data-ttu-id="4f1fa-102">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="4f1fa-102">Property Statement</span></span>
<span data-ttu-id="4f1fa-103">Declara o nome de uma propriedade e os procedimentos de propriedade usados para armazenar e recuperar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f1fa-104">Syntax</span></span>  
  
```  
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
  
## <a name="parts"></a><span data-ttu-id="4f1fa-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4f1fa-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="4f1fa-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-106">Optional.</span></span> <span data-ttu-id="4f1fa-107">Lista de atributos que se aplicam a essa propriedade ou `Get` ou `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="4f1fa-108">Consulte [lista atributo](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="4f1fa-109">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-109">Optional.</span></span> <span data-ttu-id="4f1fa-110">Especifica que esta propriedade é a propriedade padrão para a classe ou estrutura na qual ele está definido.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="4f1fa-111">Propriedades padrão devem aceitar parâmetros e podem ser definidas e recuperadas sem especificar o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="4f1fa-112">Se você declarar a propriedade como `Default`, você não pode usar `Private` na propriedade ou um dos seus procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="4f1fa-113">Opcional no `Property` instrução e no máximo uma o `Get` e `Set` instruções.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="4f1fa-114">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="4f1fa-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4f1fa-115">Público</span><span class="sxs-lookup"><span data-stu-id="4f1fa-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="4f1fa-116">Protegido</span><span class="sxs-lookup"><span data-stu-id="4f1fa-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="4f1fa-117">Friend</span><span class="sxs-lookup"><span data-stu-id="4f1fa-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="4f1fa-118">Privado</span><span class="sxs-lookup"><span data-stu-id="4f1fa-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="4f1fa-119">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-119">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="4f1fa-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-120">Optional.</span></span> <span data-ttu-id="4f1fa-121">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="4f1fa-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4f1fa-122">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="4f1fa-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="4f1fa-123">Substituições</span><span class="sxs-lookup"><span data-stu-id="4f1fa-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="4f1fa-124">Substituível</span><span class="sxs-lookup"><span data-stu-id="4f1fa-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="4f1fa-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4f1fa-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="4f1fa-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4f1fa-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="4f1fa-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-127">Optional.</span></span> <span data-ttu-id="4f1fa-128">Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="4f1fa-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-129">Optional.</span></span> <span data-ttu-id="4f1fa-130">Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="4f1fa-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-131">Optional.</span></span> <span data-ttu-id="4f1fa-132">Consulte [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="4f1fa-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-133">Optional.</span></span> <span data-ttu-id="4f1fa-134">Consulte [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="4f1fa-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-135">Optional.</span></span> <span data-ttu-id="4f1fa-136">Consulte [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="4f1fa-137">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-137">Required.</span></span> <span data-ttu-id="4f1fa-138">Nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-138">Name of the property.</span></span> <span data-ttu-id="4f1fa-139">Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="4f1fa-140">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-140">Optional.</span></span> <span data-ttu-id="4f1fa-141">Lista de nomes de variáveis locais que representam os parâmetros da propriedade e possíveis parâmetros adicionais do `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="4f1fa-142">Consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="4f1fa-143">Necessário se `Option``Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="4f1fa-144">Tipo de dados do valor retornado por essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="4f1fa-145">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-145">Optional.</span></span> <span data-ttu-id="4f1fa-146">Indica que essa propriedade implementa uma ou mais propriedades, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="4f1fa-147">Consulte [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="4f1fa-148">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="4f1fa-149">Lista de propriedades que estão sendo implementadas.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="4f1fa-150">Cada `implementedproperty` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="4f1fa-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="4f1fa-151">Parte</span><span class="sxs-lookup"><span data-stu-id="4f1fa-151">Part</span></span>|<span data-ttu-id="4f1fa-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f1fa-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="4f1fa-153">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-153">Required.</span></span> <span data-ttu-id="4f1fa-154">Nome de uma interface implementada por esta propriedade contendo classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="4f1fa-155">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-155">Required.</span></span> <span data-ttu-id="4f1fa-156">Nome pelo qual a propriedade é definida em `interface`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="4f1fa-157">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-157">Optional.</span></span> <span data-ttu-id="4f1fa-158">Necessário se a propriedade é marcada como `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="4f1fa-159">Inicia uma `Get` procedimento de propriedade que é usado para retornar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="4f1fa-160">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-160">Optional.</span></span> <span data-ttu-id="4f1fa-161">Bloco de instruções para executar dentro de `Get` ou `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="4f1fa-162">Encerra o `Get` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="4f1fa-163">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-163">Optional.</span></span> <span data-ttu-id="4f1fa-164">Necessário se a propriedade é marcada como `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="4f1fa-165">Inicia uma `Set` procedimento de propriedade que é usado para armazenar o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="4f1fa-166">Encerra o `Set` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="4f1fa-167">Finaliza a definição dessa propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f1fa-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f1fa-168">Remarks</span></span>  
 <span data-ttu-id="4f1fa-169">O `Property` instrução apresenta a declaração de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="4f1fa-170">Uma propriedade pode ter um `Get` procedimento (somente leitura), um `Set` procedimento (somente gravação), ou ambos (leitura-gravação).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="4f1fa-171">Você pode omitir o `Get` e `Set` procedimento ao usar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="4f1fa-172">Para obter mais informações, consulte [Auto-Implemented propriedades](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="4f1fa-173">Você pode usar `Property` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="4f1fa-174">Isso significa que o *contexto declaração* para uma propriedade deve ser uma classe, estrutura, módulo ou interface e não pode ser um arquivo fonte, namespace, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="4f1fa-175">Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="4f1fa-176">Por padrão, as propriedades usam acesso público.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-176">By default, properties use public access.</span></span> <span data-ttu-id="4f1fa-177">Você pode ajustar o nível de acesso de uma propriedade com um modificador de acesso a `Property` instrução e, opcionalmente, pode ajustar um dos seus procedimentos de propriedade para um nível de acesso mais restritivo.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="4f1fa-178">Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="4f1fa-179">Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito chamada `value`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="4f1fa-180">Esse parâmetro contém o valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="4f1fa-181">Você geralmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4f1fa-182">Regras</span><span class="sxs-lookup"><span data-stu-id="4f1fa-182">Rules</span></span>  
  
-   <span data-ttu-id="4f1fa-183">**Níveis de acesso mistos.**</span><span class="sxs-lookup"><span data-stu-id="4f1fa-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="4f1fa-184">Se você estiver definindo uma propriedade de leitura / gravação, você pode opcionalmente especificar um nível de acesso diferente para o `Get` ou `Set` procedimento, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="4f1fa-185">Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="4f1fa-186">Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="4f1fa-187">Se você estiver definindo um `ReadOnly` ou `WriteOnly` propriedade, o único procedimento de propriedade (`Get` ou `Set`, respectivamente) representa tudo da propriedades.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="4f1fa-188">Você não pode declarar um nível de acesso diferente para tal procedimento, porque que iria definir dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="4f1fa-189">**Tipo de retorno.**</span><span class="sxs-lookup"><span data-stu-id="4f1fa-189">**Return Type.**</span></span> <span data-ttu-id="4f1fa-190">O `Property` instrução pode declarar o tipo de dados do valor que ele retorna.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="4f1fa-191">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="4f1fa-192">Se você não especificar `returntype`, a propriedade retornará `Object`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="4f1fa-193">**Implementação.**</span><span class="sxs-lookup"><span data-stu-id="4f1fa-193">**Implementation.**</span></span> <span data-ttu-id="4f1fa-194">Se essa propriedade utiliza o `Implements` palavra-chave, a classe ou estrutura continente deve ter uma `Implements` instrução imediatamente após sua `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="4f1fa-195">O `Implements` instrução deve incluir cada interface especificada em `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="4f1fa-196">No entanto, o nome pelo qual uma interface define o `Property` (em `definedname`) não precisa ser o mesmo que o nome da propriedade (em `name`).</span><span class="sxs-lookup"><span data-stu-id="4f1fa-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4f1fa-197">Comportamento</span><span class="sxs-lookup"><span data-stu-id="4f1fa-197">Behavior</span></span>  
  
-   <span data-ttu-id="4f1fa-198">**Retornando a partir de um procedimento de propriedade.**</span><span class="sxs-lookup"><span data-stu-id="4f1fa-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="4f1fa-199">Quando o `Get` ou `Set` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que o chamou.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="4f1fa-200">O `Exit Property` e `Return` instruções causam uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="4f1fa-201">Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="4f1fa-202">**Valor de retorno.**</span><span class="sxs-lookup"><span data-stu-id="4f1fa-202">**Return Value.**</span></span> <span data-ttu-id="4f1fa-203">Para retornar um valor de uma `Get` procedimento, você pode atribuir o valor ao nome da propriedade ou incluí-lo em um `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="4f1fa-204">O exemplo a seguir atribui o valor de retorno ao nome da propriedade `quoteForTheDay` e, em seguida, usa o `Exit Property` instrução para retornar.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     <span data-ttu-id="4f1fa-205">[!code-vb[VbVbalrStatements&#27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4f1fa-205">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="4f1fa-206">[!code-vb[VbVbalrStatements&#28;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4f1fa-206">[!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span></span>  
  
     <span data-ttu-id="4f1fa-207">Se você usar `Exit Property` sem atribuir um valor para `name`, o `Get` procedimento retorna o valor padrão para o tipo de dados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="4f1fa-208">O `Return` instrução ao mesmo tempo atribui o `Get` valor e finaliza o procedimento de retorno de procedimento.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="4f1fa-209">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-209">The following example shows this.</span></span>  
  
     <span data-ttu-id="4f1fa-210">[!code-vb[VbVbalrStatements&#27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4f1fa-210">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="4f1fa-211">[!code-vb[29 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="4f1fa-211">[!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f1fa-212">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4f1fa-212">Example</span></span>  
 <span data-ttu-id="4f1fa-213">O exemplo a seguir declara uma propriedade em uma classe.</span><span class="sxs-lookup"><span data-stu-id="4f1fa-213">The following example declares a property in a class.</span></span>  
  
 <span data-ttu-id="4f1fa-214">[!code-vb[VbVbalrStatements&#51;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="4f1fa-214">[!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1fa-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f1fa-215">See Also</span></span>  
 <span data-ttu-id="4f1fa-216">[Propriedades autoimplementadas](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4f1fa-216">[Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span></span>  
<span data-ttu-id="4f1fa-217"> [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="4f1fa-217"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="4f1fa-218"> [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4f1fa-218"> [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="4f1fa-219"> [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4f1fa-219"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) </span></span>  
<span data-ttu-id="4f1fa-220"> [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="4f1fa-220"> [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) </span></span>  
<span data-ttu-id="4f1fa-221"> [Padrão](../../../visual-basic/language-reference/modifiers/default.md)</span><span class="sxs-lookup"><span data-stu-id="4f1fa-221"> [Default](../../../visual-basic/language-reference/modifiers/default.md)</span></span>

