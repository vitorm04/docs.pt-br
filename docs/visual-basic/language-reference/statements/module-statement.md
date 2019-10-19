---
title: Instrução Module (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 9b1aae08d0009a9fd23d6441207f1601ffec2568
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583104"
---
# <a name="module-statement"></a><span data-ttu-id="939ff-102">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="939ff-102">Module Statement</span></span>

<span data-ttu-id="939ff-103">Declara o nome de um módulo e apresenta a definição das variáveis, propriedades, eventos e procedimentos que o módulo compreende.</span><span class="sxs-lookup"><span data-stu-id="939ff-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>

## <a name="syntax"></a><span data-ttu-id="939ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="939ff-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a><span data-ttu-id="939ff-105">Partes</span><span class="sxs-lookup"><span data-stu-id="939ff-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="939ff-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="939ff-106">Optional.</span></span> <span data-ttu-id="939ff-107">Consulte a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`accessmodifier`  
<span data-ttu-id="939ff-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="939ff-108">Optional.</span></span> <span data-ttu-id="939ff-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="939ff-109">Can be one of the following:</span></span>

- [<span data-ttu-id="939ff-110">Público</span><span class="sxs-lookup"><span data-stu-id="939ff-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

- [<span data-ttu-id="939ff-111">Friend</span><span class="sxs-lookup"><span data-stu-id="939ff-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

<span data-ttu-id="939ff-112">Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-112">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

`name`  
<span data-ttu-id="939ff-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="939ff-113">Required.</span></span> <span data-ttu-id="939ff-114">Nome deste módulo.</span><span class="sxs-lookup"><span data-stu-id="939ff-114">Name of this module.</span></span> <span data-ttu-id="939ff-115">Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

`statements`  
<span data-ttu-id="939ff-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="939ff-116">Optional.</span></span> <span data-ttu-id="939ff-117">Instruções que definem as variáveis, propriedades, eventos, procedimentos e tipos aninhados deste módulo.</span><span class="sxs-lookup"><span data-stu-id="939ff-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>

`End Module`  
<span data-ttu-id="939ff-118">Encerra a definição de `Module`.</span><span class="sxs-lookup"><span data-stu-id="939ff-118">Terminates the `Module` definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="939ff-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="939ff-119">Remarks</span></span>

<span data-ttu-id="939ff-120">Uma instrução `Module` define um tipo de referência disponível em todo o namespace.</span><span class="sxs-lookup"><span data-stu-id="939ff-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="939ff-121">Um *módulo* (às vezes chamado de *módulo padrão*) é semelhante a uma classe, mas com algumas distinções importantes.</span><span class="sxs-lookup"><span data-stu-id="939ff-121">A *module* (sometimes called a *standard module*) is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="939ff-122">Cada módulo tem exatamente uma instância e não precisa ser criado ou atribuído a uma variável.</span><span class="sxs-lookup"><span data-stu-id="939ff-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="939ff-123">Os módulos não dão suporte à herança ou à implementação de interfaces.</span><span class="sxs-lookup"><span data-stu-id="939ff-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="939ff-124">Observe que um módulo não é um *tipo* no sentido de que uma classe ou estrutura é — você não pode declarar um elemento de programação para ter o tipo de dados de um módulo.</span><span class="sxs-lookup"><span data-stu-id="939ff-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>

<span data-ttu-id="939ff-125">Você pode usar `Module` somente no nível de namespace.</span><span class="sxs-lookup"><span data-stu-id="939ff-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="939ff-126">Isso significa que o *contexto de declaração* para um módulo deve ser um arquivo ou namespace de origem e não pode ser uma classe, estrutura, módulo, interface, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="939ff-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="939ff-127">Não é possível aninhar um módulo dentro de outro módulo ou dentro de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="939ff-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="939ff-128">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="939ff-129">Um módulo tem o mesmo tempo de vida do seu programa.</span><span class="sxs-lookup"><span data-stu-id="939ff-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="939ff-130">Como seus membros são todos `Shared`, eles também têm tempos de vida iguais aos do programa.</span><span class="sxs-lookup"><span data-stu-id="939ff-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>

<span data-ttu-id="939ff-131">Os módulos são padrão para acesso [Friend](../../../visual-basic/language-reference/modifiers/friend.md) .</span><span class="sxs-lookup"><span data-stu-id="939ff-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="939ff-132">Você pode ajustar seus níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="939ff-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="939ff-133">Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-133">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="939ff-134">Todos os membros de um módulo são implicitamente `Shared`.</span><span class="sxs-lookup"><span data-stu-id="939ff-134">All members of a module are implicitly `Shared`.</span></span>

## <a name="classes-and-modules"></a><span data-ttu-id="939ff-135">Classes e módulos</span><span class="sxs-lookup"><span data-stu-id="939ff-135">Classes and Modules</span></span>

<span data-ttu-id="939ff-136">Esses elementos têm muitas semelhanças, mas também há algumas diferenças importantes.</span><span class="sxs-lookup"><span data-stu-id="939ff-136">These elements have many similarities, but there are some important differences as well.</span></span>

- <span data-ttu-id="939ff-137">**Terminologia.**</span><span class="sxs-lookup"><span data-stu-id="939ff-137">**Terminology.**</span></span> <span data-ttu-id="939ff-138">As versões anteriores do Visual Basic reconhecem dois tipos de módulos: *módulos de classe* (arquivos. CLS) e *módulos padrão* (arquivos. bas).</span><span class="sxs-lookup"><span data-stu-id="939ff-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="939ff-139">A versão atual chama essas *classes* e *módulos*, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="939ff-139">The current version calls these *classes* and *modules*, respectively.</span></span>

- <span data-ttu-id="939ff-140">**Membros compartilhados.**</span><span class="sxs-lookup"><span data-stu-id="939ff-140">**Shared Members.**</span></span> <span data-ttu-id="939ff-141">Você pode controlar se um membro de uma classe é um membro compartilhado ou de instância.</span><span class="sxs-lookup"><span data-stu-id="939ff-141">You can control whether a member of a class is a shared or instance member.</span></span>

- <span data-ttu-id="939ff-142">**Orientação do objeto.**</span><span class="sxs-lookup"><span data-stu-id="939ff-142">**Object Orientation.**</span></span> <span data-ttu-id="939ff-143">As classes são orientadas a objeto, mas os módulos não são.</span><span class="sxs-lookup"><span data-stu-id="939ff-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="939ff-144">Portanto, somente classes podem ser instanciadas como objetos.</span><span class="sxs-lookup"><span data-stu-id="939ff-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="939ff-145">Para obter mais informações, consulte [objetos e classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="939ff-146">Regras</span><span class="sxs-lookup"><span data-stu-id="939ff-146">Rules</span></span>

- <span data-ttu-id="939ff-147">**Modificadores.**</span><span class="sxs-lookup"><span data-stu-id="939ff-147">**Modifiers.**</span></span> <span data-ttu-id="939ff-148">Todos os membros do módulo são [compartilhados](../../../visual-basic/language-reference/modifiers/shared.md)implicitamente.</span><span class="sxs-lookup"><span data-stu-id="939ff-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="939ff-149">Você não pode usar a palavra-chave `Shared` ao declarar um membro e não pode alterar o status compartilhado de nenhum membro.</span><span class="sxs-lookup"><span data-stu-id="939ff-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>

- <span data-ttu-id="939ff-150">**Herança.**</span><span class="sxs-lookup"><span data-stu-id="939ff-150">**Inheritance.**</span></span> <span data-ttu-id="939ff-151">Um módulo não pode herdar de nenhum tipo que não seja <xref:System.Object>, do qual todos os módulos herdam.</span><span class="sxs-lookup"><span data-stu-id="939ff-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="939ff-152">Em particular, um módulo não pode herdar de outro.</span><span class="sxs-lookup"><span data-stu-id="939ff-152">In particular, one module cannot inherit from another.</span></span>

  <span data-ttu-id="939ff-153">Você não pode usar a [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de módulo, mesmo para especificar <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="939ff-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>

- <span data-ttu-id="939ff-154">**Propriedade padrão.**</span><span class="sxs-lookup"><span data-stu-id="939ff-154">**Default Property.**</span></span> <span data-ttu-id="939ff-155">Você não pode definir nenhuma propriedade padrão em um módulo.</span><span class="sxs-lookup"><span data-stu-id="939ff-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="939ff-156">Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>

## <a name="behavior"></a><span data-ttu-id="939ff-157">Comportamento</span><span class="sxs-lookup"><span data-stu-id="939ff-157">Behavior</span></span>

- <span data-ttu-id="939ff-158">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="939ff-158">**Access Level.**</span></span> <span data-ttu-id="939ff-159">Dentro de um módulo, você pode declarar cada membro com seu próprio nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="939ff-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="939ff-160">Os membros do módulo assumem como padrão acesso [público](../../../visual-basic/language-reference/modifiers/public.md) , Exceto variáveis e constantes, que assumem como padrão o acesso [privado](../../../visual-basic/language-reference/modifiers/private.md) .</span><span class="sxs-lookup"><span data-stu-id="939ff-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="939ff-161">Quando um módulo tem acesso mais restrito do que um de seus membros, o nível de acesso do módulo especificado tem precedência.</span><span class="sxs-lookup"><span data-stu-id="939ff-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>

- <span data-ttu-id="939ff-162">**Com.**</span><span class="sxs-lookup"><span data-stu-id="939ff-162">**Scope.**</span></span> <span data-ttu-id="939ff-163">Um módulo está no escopo em todo o namespace.</span><span class="sxs-lookup"><span data-stu-id="939ff-163">A module is in scope throughout its namespace.</span></span>

  <span data-ttu-id="939ff-164">O escopo de cada membro de módulo é o módulo inteiro.</span><span class="sxs-lookup"><span data-stu-id="939ff-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="939ff-165">Observe que todos os membros sofrem a *promoção de tipos*, o que faz com que seu escopo seja promovido para o namespace que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="939ff-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="939ff-166">Para obter mais informações, consulte [promoção de tipos](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>

- <span data-ttu-id="939ff-167">**Aprovação.**</span><span class="sxs-lookup"><span data-stu-id="939ff-167">**Qualification.**</span></span> <span data-ttu-id="939ff-168">Você pode ter vários módulos em um projeto e pode declarar membros com o mesmo nome em dois ou mais módulos.</span><span class="sxs-lookup"><span data-stu-id="939ff-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="939ff-169">No entanto, você deve qualificar qualquer referência a tal membro com o nome do módulo apropriado se a referência for de fora desse módulo.</span><span class="sxs-lookup"><span data-stu-id="939ff-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="939ff-170">Para obter mais informações, consulte [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="939ff-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

## <a name="example"></a><span data-ttu-id="939ff-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="939ff-171">Example</span></span>

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a><span data-ttu-id="939ff-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="939ff-172">See also</span></span>

- [<span data-ttu-id="939ff-173">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="939ff-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="939ff-174">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="939ff-174">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="939ff-175">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="939ff-175">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="939ff-176">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="939ff-176">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="939ff-177">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="939ff-177">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="939ff-178">Tipo de promoção</span><span class="sxs-lookup"><span data-stu-id="939ff-178">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
