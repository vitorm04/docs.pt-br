---
title: Parcial (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5129ef7737b1b07317d47f8d18e9aceb668bf05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="partial-visual-basic"></a><span data-ttu-id="6269d-102">Parcial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6269d-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="6269d-103">Indica que uma declaração de tipo é uma definição parcial do tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="6269d-104">Você pode dividir a definição de um tipo entre várias declarações usando o `Partial` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="6269d-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="6269d-105">Você pode usar quantas declarações parciais conforme desejado, em quantos arquivos de origem diferente conforme desejado.</span><span class="sxs-lookup"><span data-stu-id="6269d-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="6269d-106">No entanto, todas as declarações devem estar no mesmo assembly e no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="6269d-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6269d-107">Visual Basic oferece suporte *métodos parciais*, que são normalmente implementado em classes parciais.</span><span class="sxs-lookup"><span data-stu-id="6269d-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="6269d-108">Para obter mais informações, consulte [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) e [instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6269d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6269d-109">Syntax</span></span>  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="6269d-110">Partes</span><span class="sxs-lookup"><span data-stu-id="6269d-110">Parts</span></span>  
  
|<span data-ttu-id="6269d-111">Termo</span><span class="sxs-lookup"><span data-stu-id="6269d-111">Term</span></span>|<span data-ttu-id="6269d-112">Definição</span><span class="sxs-lookup"><span data-stu-id="6269d-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="6269d-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-113">Optional.</span></span> <span data-ttu-id="6269d-114">Lista de atributos que se aplicam a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="6269d-115">Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares (`< >`).</span><span class="sxs-lookup"><span data-stu-id="6269d-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="6269d-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-116">Optional.</span></span> <span data-ttu-id="6269d-117">Especifica o código pode acessar esse tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-117">Specifies what code can access this type.</span></span> <span data-ttu-id="6269d-118">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="6269d-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-119">Optional.</span></span> <span data-ttu-id="6269d-120">Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="6269d-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-121">Optional.</span></span> <span data-ttu-id="6269d-122">Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="6269d-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-123">Optional.</span></span> <span data-ttu-id="6269d-124">Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="6269d-125">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6269d-125">Required.</span></span> <span data-ttu-id="6269d-126">Nome deste tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-126">Name of this type.</span></span> <span data-ttu-id="6269d-127">Deve corresponder ao nome definido em todas as outras declarações parciais do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="6269d-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-128">Optional.</span></span> <span data-ttu-id="6269d-129">Especifica que se trata de um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="6269d-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="6269d-130">Consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="6269d-131">Necessário se você usar [de](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="6269d-132">Consulte [digite lista](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="6269d-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-133">Optional.</span></span> <span data-ttu-id="6269d-134">Consulte [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="6269d-135">Necessário se você usar `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="6269d-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="6269d-136">O nome da classe ou interface da qual essa classe deriva.</span><span class="sxs-lookup"><span data-stu-id="6269d-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="6269d-137">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-137">Optional.</span></span> <span data-ttu-id="6269d-138">Consulte [implementa a instrução](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="6269d-139">Necessário se você usar `Implements`.</span><span class="sxs-lookup"><span data-stu-id="6269d-139">Required if you use `Implements`.</span></span> <span data-ttu-id="6269d-140">Os nomes das interfaces que implementa esse tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="6269d-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-141">Optional.</span></span> <span data-ttu-id="6269d-142">Instruções que declaram variáveis adicionais e eventos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="6269d-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6269d-143">Optional.</span></span> <span data-ttu-id="6269d-144">Instruções que declaram e definem procedimentos adicionais para o tipo.</span><span class="sxs-lookup"><span data-stu-id="6269d-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="6269d-145">`End Class` ou `End Structure`</span><span class="sxs-lookup"><span data-stu-id="6269d-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="6269d-146">Encerra esta parcial `Class` ou `Structure` definição.</span><span class="sxs-lookup"><span data-stu-id="6269d-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6269d-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="6269d-147">Remarks</span></span>  
 <span data-ttu-id="6269d-148">Visual Basic usa definições de classe parcial para separar o código gerado no código de autoria do usuário nos arquivos de origem separados.</span><span class="sxs-lookup"><span data-stu-id="6269d-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="6269d-149">Por exemplo, o **Windows Form Designer** define classes parciais para controles, como <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="6269d-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="6269d-150">Você não deve modificar o código gerado nesses controles.</span><span class="sxs-lookup"><span data-stu-id="6269d-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="6269d-151">Todas as regras para a classe, estrutura, interface e criação de módulo, como aquelas para o uso de modificador e herança, se aplicam ao criar um tipo parcial.</span><span class="sxs-lookup"><span data-stu-id="6269d-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="6269d-152">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="6269d-152">Best Practices</span></span>  
  
-   <span data-ttu-id="6269d-153">Em circunstâncias normais, você não deve dividir o desenvolvimento de um único tipo entre dois ou mais declarações.</span><span class="sxs-lookup"><span data-stu-id="6269d-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="6269d-154">Portanto, na maioria dos casos você não precisa de `Partial` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="6269d-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
-   <span data-ttu-id="6269d-155">Para facilitar a leitura, cada declaração parcial de um tipo deve incluir o `Partial` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="6269d-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="6269d-156">O compilador permite no máximo uma declaração parcial omitir a palavra-chave; Se dois ou mais omiti-lo o compilador sinaliza um erro.</span><span class="sxs-lookup"><span data-stu-id="6269d-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6269d-157">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6269d-157">Behavior</span></span>  
  
-   <span data-ttu-id="6269d-158">**União de declarações.**</span><span class="sxs-lookup"><span data-stu-id="6269d-158">**Union of Declarations.**</span></span> <span data-ttu-id="6269d-159">O compilador trata o tipo como a união de todas as suas declarações parciais.</span><span class="sxs-lookup"><span data-stu-id="6269d-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="6269d-160">Cada modificador de cada definição parcial aplica-se ao tipo de inteiro e todos os membros de cada definição parcial estão disponível para o tipo inteiro.</span><span class="sxs-lookup"><span data-stu-id="6269d-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
-   <span data-ttu-id="6269d-161">**Promoção de tipo não permitida para tipos parciais em módulos.**</span><span class="sxs-lookup"><span data-stu-id="6269d-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="6269d-162">Se for uma definição parcial dentro de um módulo, promoção de tipo desse tipo é desfeita automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6269d-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="6269d-163">Nesse caso, um conjunto de definições parciais pode causar resultados inesperados e até mesmo erros de compilador.</span><span class="sxs-lookup"><span data-stu-id="6269d-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="6269d-164">Para obter mais informações, consulte [promoção de tipo](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="6269d-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="6269d-165">O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.</span><span class="sxs-lookup"><span data-stu-id="6269d-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="6269d-166">O `Partial` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="6269d-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6269d-167">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="6269d-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6269d-168">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="6269d-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6269d-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6269d-169">Example</span></span>  
 <span data-ttu-id="6269d-170">O exemplo a seguir divide a definição de classe `sampleClass` em duas declarações, cada uma delas define outro `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="6269d-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 <span data-ttu-id="6269d-171">As duas definições parciais no exemplo anterior podem ser no mesmo arquivo de origem ou em dois arquivos de origem diferente.</span><span class="sxs-lookup"><span data-stu-id="6269d-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6269d-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6269d-172">See Also</span></span>  
 [<span data-ttu-id="6269d-173">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="6269d-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="6269d-174">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="6269d-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="6269d-175">Tipo de promoção</span><span class="sxs-lookup"><span data-stu-id="6269d-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [<span data-ttu-id="6269d-176">Sombras</span><span class="sxs-lookup"><span data-stu-id="6269d-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="6269d-177">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6269d-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="6269d-178">Métodos Parciais</span><span class="sxs-lookup"><span data-stu-id="6269d-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
