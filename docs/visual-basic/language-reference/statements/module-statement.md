---
title: "Instrução Module | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Module
- vb.Module
dev_langs:
- VB
helpviewer_keywords:
- modules, classes
- modules
- Module statement
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations, modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: 24
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
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: da0d1125b489a174132b6cef93d2854460d4da8d
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="module-statement"></a><span data-ttu-id="cb60f-102">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="cb60f-102">Module Statement</span></span>
<span data-ttu-id="cb60f-103">Declara o nome de um módulo e introduz a definição de variáveis, propriedades, eventos e procedimentos que compõem o módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-103">Declares the name of a module and introduces the definition of the variables, properties, events, and procedures that the module comprises.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb60f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb60f-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a><span data-ttu-id="cb60f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="cb60f-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="cb60f-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cb60f-106">Optional.</span></span> <span data-ttu-id="cb60f-107">Consulte [lista atributo](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="cb60f-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cb60f-108">Optional.</span></span> <span data-ttu-id="cb60f-109">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="cb60f-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="cb60f-110">Público</span><span class="sxs-lookup"><span data-stu-id="cb60f-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [<span data-ttu-id="cb60f-111">Friend</span><span class="sxs-lookup"><span data-stu-id="cb60f-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 <span data-ttu-id="cb60f-112">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-112">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `name`  
 <span data-ttu-id="cb60f-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="cb60f-113">Required.</span></span> <span data-ttu-id="cb60f-114">Nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-114">Name of this module.</span></span> <span data-ttu-id="cb60f-115">Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-115">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `statements`  
 <span data-ttu-id="cb60f-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="cb60f-116">Optional.</span></span> <span data-ttu-id="cb60f-117">Instruções que definem variáveis, propriedades, eventos, procedimentos e tipos aninhados deste módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-117">Statements which define the variables, properties, events, procedures, and nested types of this module.</span></span>  
  
 `End Module`  
 <span data-ttu-id="cb60f-118">Encerra o `Module` definição.</span><span class="sxs-lookup"><span data-stu-id="cb60f-118">Terminates the `Module` definition.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb60f-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb60f-119">Remarks</span></span>  
 <span data-ttu-id="cb60f-120">Um `Module` instrução define um tipo de referência disponível em todo o namespace.</span><span class="sxs-lookup"><span data-stu-id="cb60f-120">A `Module` statement defines a reference type available throughout its namespace.</span></span> <span data-ttu-id="cb60f-121">A *módulo* (às vezes chamado de um *módulo padrão*) é semelhante a uma classe, mas com algumas distinções importantes.</span><span class="sxs-lookup"><span data-stu-id="cb60f-121">A *module* (sometimes called a *standard module*)is similar to a class but with some important distinctions.</span></span> <span data-ttu-id="cb60f-122">Cada módulo tem exatamente uma instância e não precisa ser criado ou atribuído a uma variável.</span><span class="sxs-lookup"><span data-stu-id="cb60f-122">Every module has exactly one instance and does not need to be created or assigned to a variable.</span></span> <span data-ttu-id="cb60f-123">Módulos não oferecer suporte a herança ou implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="cb60f-123">Modules do not support inheritance or implement interfaces.</span></span> <span data-ttu-id="cb60f-124">Observe que um módulo não é um *tipo* no sentido de que uma classe ou estrutura é — você não pode declarar um elemento de programação para ter o tipo de dados de um módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-124">Notice that a module is not a *type* in the sense that a class or structure is — you cannot declare a programming element to have the data type of a module.</span></span>  
  
 <span data-ttu-id="cb60f-125">Você pode usar `Module` somente no nível de namespace.</span><span class="sxs-lookup"><span data-stu-id="cb60f-125">You can use `Module` only at namespace level.</span></span> <span data-ttu-id="cb60f-126">Isso significa que o *contexto declaração* para um módulo deve ser um arquivo fonte ou namespace e não pode ser uma classe, estrutura, módulo, interface, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="cb60f-126">This means the *declaration context* for a module must be a source file or namespace, and cannot be a class, structure, module, interface, procedure, or block.</span></span> <span data-ttu-id="cb60f-127">Não é possível aninhar um módulo dentro de outro módulo, ou em qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-127">You cannot nest a module within another module, or within any type.</span></span> <span data-ttu-id="cb60f-128">Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="cb60f-129">Um módulo tem a mesma duração do seu programa.</span><span class="sxs-lookup"><span data-stu-id="cb60f-129">A module has the same lifetime as your program.</span></span> <span data-ttu-id="cb60f-130">Como seus membros são todos os `Shared`, eles também têm vida útil igual a do programa.</span><span class="sxs-lookup"><span data-stu-id="cb60f-130">Because its members are all `Shared`, they also have lifetimes equal to that of the program.</span></span>  
  
 <span data-ttu-id="cb60f-131">Módulos padrão [amigo](../../../visual-basic/language-reference/modifiers/friend.md) acesso.</span><span class="sxs-lookup"><span data-stu-id="cb60f-131">Modules default to [Friend](../../../visual-basic/language-reference/modifiers/friend.md) access.</span></span> <span data-ttu-id="cb60f-132">Você pode ajustar os níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="cb60f-132">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="cb60f-133">Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-133">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="cb60f-134">Todos os membros de um módulo são implicitamente `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cb60f-134">All members of a module are implicitly `Shared`.</span></span>  
  
## <a name="classes-and-modules"></a><span data-ttu-id="cb60f-135">Classes e módulos</span><span class="sxs-lookup"><span data-stu-id="cb60f-135">Classes and Modules</span></span>  
 <span data-ttu-id="cb60f-136">Esses elementos têm várias semelhanças, mas há algumas diferenças importantes também.</span><span class="sxs-lookup"><span data-stu-id="cb60f-136">These elements have many similarities, but there are some important differences as well.</span></span>  
  
-   <span data-ttu-id="cb60f-137">**Terminologia.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-137">**Terminology.**</span></span> <span data-ttu-id="cb60f-138">Versões anteriores do Visual Basic reconhecem dois tipos de módulos: *módulos de classe* (CLS arquivos) e *módulos padrão* (arquivos. bas).</span><span class="sxs-lookup"><span data-stu-id="cb60f-138">Previous versions of Visual Basic recognize two types of modules: *class modules* (.cls files) and *standard modules* (.bas files).</span></span> <span data-ttu-id="cb60f-139">A versão atual chama esses *classes* e *módulos*, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="cb60f-139">The current version calls these *classes* and *modules*, respectively.</span></span>  
  
-   <span data-ttu-id="cb60f-140">**Membros compartilhados.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-140">**Shared Members.**</span></span> <span data-ttu-id="cb60f-141">Você pode controlar se um membro de uma classe é uma chave secreta ou membro de instância.</span><span class="sxs-lookup"><span data-stu-id="cb60f-141">You can control whether a member of a class is a shared or instance member.</span></span>  
  
-   <span data-ttu-id="cb60f-142">**Orientação a objeto.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-142">**Object Orientation.**</span></span> <span data-ttu-id="cb60f-143">Classes são orientadas a objeto, mas módulos não são.</span><span class="sxs-lookup"><span data-stu-id="cb60f-143">Classes are object-oriented, but modules are not.</span></span> <span data-ttu-id="cb60f-144">Portanto, apenas classes podem ser instanciadas como objetos.</span><span class="sxs-lookup"><span data-stu-id="cb60f-144">So only classes can be instantiated as objects.</span></span> <span data-ttu-id="cb60f-145">Para obter mais informações, consulte [objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-145">For more information, see [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cb60f-146">Regras</span><span class="sxs-lookup"><span data-stu-id="cb60f-146">Rules</span></span>  
  
-   <span data-ttu-id="cb60f-147">**Modificadores.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-147">**Modifiers.**</span></span> <span data-ttu-id="cb60f-148">Todos os membros do módulo são implicitamente [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-148">All module members are implicitly [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="cb60f-149">Não é possível usar o `Shared` palavra-chave ao declarar um membro e você não pode alterar o status compartilhado de nenhum membro.</span><span class="sxs-lookup"><span data-stu-id="cb60f-149">You cannot use the `Shared` keyword when declaring a member, and you cannot alter the shared status of any member.</span></span>  
  
-   <span data-ttu-id="cb60f-150">**Herança.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-150">**Inheritance.**</span></span> <span data-ttu-id="cb60f-151">Um módulo não pode herdar de qualquer tipo diferente de <xref:System.Object>, do qual todas os módulos herdam.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="cb60f-151">A module cannot inherit from any type other than <xref:System.Object>, from which all modules inherit.</span></span> <span data-ttu-id="cb60f-152">Em particular, um módulo não pode herdar de outra.</span><span class="sxs-lookup"><span data-stu-id="cb60f-152">In particular, one module cannot inherit from another.</span></span>  
  
     <span data-ttu-id="cb60f-153">Não é possível usar o [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) em uma definição de módulo, mesmo para especificar <xref:System.Object>.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="cb60f-153">You cannot use the [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) in a module definition, even to specify <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="cb60f-154">**Propriedade padrão.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-154">**Default Property.**</span></span> <span data-ttu-id="cb60f-155">Você não pode definir as propriedades padrão em um módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-155">You cannot define any default properties in a module.</span></span> <span data-ttu-id="cb60f-156">Para obter mais informações, consulte [padrão](../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-156">For more information, see [Default](../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cb60f-157">Comportamento</span><span class="sxs-lookup"><span data-stu-id="cb60f-157">Behavior</span></span>  
  
-   <span data-ttu-id="cb60f-158">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-158">**Access Level.**</span></span> <span data-ttu-id="cb60f-159">Dentro de um módulo, você pode declarar cada membro com seu próprio nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="cb60f-159">Within a module, you can declare each member with its own access level.</span></span> <span data-ttu-id="cb60f-160">Membros de módulo padrão [pública](../../../visual-basic/language-reference/modifiers/public.md) acessar, exceto as variáveis e constantes, padrão para [particular](../../../visual-basic/language-reference/modifiers/private.md) acesso.</span><span class="sxs-lookup"><span data-stu-id="cb60f-160">Module members default to [Public](../../../visual-basic/language-reference/modifiers/public.md) access, except variables and constants, which default to [Private](../../../visual-basic/language-reference/modifiers/private.md) access.</span></span> <span data-ttu-id="cb60f-161">Quando um módulo tem mais acesso restrito que um de seus membros, o nível de acesso especificado do módulo tem precedência.</span><span class="sxs-lookup"><span data-stu-id="cb60f-161">When a module has more restricted access than one of its members, the specified module access level takes precedence.</span></span>  
  
-   <span data-ttu-id="cb60f-162">**Escopo.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-162">**Scope.**</span></span> <span data-ttu-id="cb60f-163">Um módulo está no escopo em todo o namespace.</span><span class="sxs-lookup"><span data-stu-id="cb60f-163">A module is in scope throughout its namespace.</span></span>  
  
     <span data-ttu-id="cb60f-164">O escopo de cada membro de módulo é todo o módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-164">The scope of every module member is the entire module.</span></span> <span data-ttu-id="cb60f-165">Observe que todos os membros sofrem *promoção de tipo*, que faz com que o escopo seja promovido para o namespace que contém o módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-165">Notice that all members undergo *type promotion*, which causes their scope to be promoted to the namespace containing the module.</span></span> <span data-ttu-id="cb60f-166">Para obter mais informações, consulte [promoção de tipo](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-166">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
-   <span data-ttu-id="cb60f-167">**Qualificação.**</span><span class="sxs-lookup"><span data-stu-id="cb60f-167">**Qualification.**</span></span> <span data-ttu-id="cb60f-168">Você pode ter vários módulos em um projeto, e você pode declarar membros com o mesmo nome em dois ou mais módulos.</span><span class="sxs-lookup"><span data-stu-id="cb60f-168">You can have multiple modules in a project, and you can declare members with the same name in two or more modules.</span></span> <span data-ttu-id="cb60f-169">No entanto, você deverá qualificar qualquer referência a esse membro com o nome do módulo apropriado se a referência estiver fora desse módulo.</span><span class="sxs-lookup"><span data-stu-id="cb60f-169">However, you must qualify any reference to such a member with the appropriate module name if the reference is from outside that module.</span></span> <span data-ttu-id="cb60f-170">Para obter mais informações, consulte [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="cb60f-170">For more information, see [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb60f-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb60f-171">Example</span></span>  
 <span data-ttu-id="cb60f-172">[!code-vb[VbVbalrStatements&#69;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cb60f-172">[!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb60f-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb60f-173">See Also</span></span>  
 <span data-ttu-id="cb60f-174">[Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb60f-174">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="cb60f-175"> [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb60f-175"> [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="cb60f-176"> [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb60f-176"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="cb60f-177"> [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb60f-177"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="cb60f-178"> [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb60f-178"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="cb60f-179"> [Tipo de promoção](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)</span><span class="sxs-lookup"><span data-stu-id="cb60f-179"> [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)</span></span>

