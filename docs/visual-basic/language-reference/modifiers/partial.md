---
title: Parcial
ms.date: 07/20/2015
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
ms.openlocfilehash: df85571b757fd54496677bad1195fab9690b79cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351353"
---
# <a name="partial-visual-basic"></a><span data-ttu-id="6dbca-102">Parcial (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6dbca-102">Partial (Visual Basic)</span></span>
<span data-ttu-id="6dbca-103">Indica que uma declaração de tipo é uma definição parcial do tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-103">Indicates that a type declaration is a partial definition of the type.</span></span>  
  
 <span data-ttu-id="6dbca-104">Você pode dividir a definição de um tipo entre várias declarações usando a palavra-chave `Partial`.</span><span class="sxs-lookup"><span data-stu-id="6dbca-104">You can divide the definition of a type among several declarations by using the `Partial` keyword.</span></span> <span data-ttu-id="6dbca-105">Você pode usar quantas declarações parciais desejar, em quantos arquivos de origem diferentes desejar.</span><span class="sxs-lookup"><span data-stu-id="6dbca-105">You can use as many partial declarations as you want, in as many different source files as you want.</span></span> <span data-ttu-id="6dbca-106">No entanto, todas as declarações devem estar no mesmo assembly e no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="6dbca-106">However, all the declarations must be in the same assembly and the same namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6dbca-107">O Visual Basic dá suporte a *métodos parciais*, que normalmente são implementados em classes parciais.</span><span class="sxs-lookup"><span data-stu-id="6dbca-107">Visual Basic supports *partial methods*, which are typically implemented in partial classes.</span></span> <span data-ttu-id="6dbca-108">Para obter mais informações, consulte [partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) e [sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-108">For more information, see [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) and [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dbca-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6dbca-109">Syntax</span></span>  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a><span data-ttu-id="6dbca-110">Partes</span><span class="sxs-lookup"><span data-stu-id="6dbca-110">Parts</span></span>  
  
|<span data-ttu-id="6dbca-111">Termo</span><span class="sxs-lookup"><span data-stu-id="6dbca-111">Term</span></span>|<span data-ttu-id="6dbca-112">Definição</span><span class="sxs-lookup"><span data-stu-id="6dbca-112">Definition</span></span>|  
|---|---|  
|`attrlist`|<span data-ttu-id="6dbca-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-113">Optional.</span></span> <span data-ttu-id="6dbca-114">Lista de atributos que se aplicam a este tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-114">List of attributes that apply to this type.</span></span> <span data-ttu-id="6dbca-115">Você deve colocar a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares (`< >`).</span><span class="sxs-lookup"><span data-stu-id="6dbca-115">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets (`< >`).</span></span>|  
|`accessmodifier`|<span data-ttu-id="6dbca-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-116">Optional.</span></span> <span data-ttu-id="6dbca-117">Especifica qual código pode acessar este tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-117">Specifies what code can access this type.</span></span> <span data-ttu-id="6dbca-118">Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-118">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`Shadows`|<span data-ttu-id="6dbca-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-119">Optional.</span></span> <span data-ttu-id="6dbca-120">Consulte [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>|  
|`MustInherit`|<span data-ttu-id="6dbca-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-121">Optional.</span></span> <span data-ttu-id="6dbca-122">Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-122">See [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>|  
|`NotInheritable`|<span data-ttu-id="6dbca-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-123">Optional.</span></span> <span data-ttu-id="6dbca-124">Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-124">See [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).</span></span>|  
|`name`|<span data-ttu-id="6dbca-125">Necessária.</span><span class="sxs-lookup"><span data-stu-id="6dbca-125">Required.</span></span> <span data-ttu-id="6dbca-126">Nome deste tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-126">Name of this type.</span></span> <span data-ttu-id="6dbca-127">Deve corresponder ao nome definido em todas as outras declarações parciais do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-127">Must match the name defined in all other partial declarations of the same type.</span></span>|  
|`Of`|<span data-ttu-id="6dbca-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-128">Optional.</span></span> <span data-ttu-id="6dbca-129">Especifica que este é um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="6dbca-129">Specifies that this is a generic type.</span></span> <span data-ttu-id="6dbca-130">Consulte [tipos genéricos em Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-130">See [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span>|  
|`typelist`|<span data-ttu-id="6dbca-131">Necessário se você usar [do](../../../visual-basic/language-reference/statements/of-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-131">Required if you use [Of](../../../visual-basic/language-reference/statements/of-clause.md).</span></span> <span data-ttu-id="6dbca-132">Consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-132">See [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>|  
|`Inherits`|<span data-ttu-id="6dbca-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-133">Optional.</span></span> <span data-ttu-id="6dbca-134">Consulte a [instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-134">See [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md).</span></span>|  
|`classname`|<span data-ttu-id="6dbca-135">Necessário se você usar `Inherits`.</span><span class="sxs-lookup"><span data-stu-id="6dbca-135">Required if you use `Inherits`.</span></span> <span data-ttu-id="6dbca-136">O nome da classe ou interface da qual essa classe deriva.</span><span class="sxs-lookup"><span data-stu-id="6dbca-136">The name of the class or interface from which this class derives.</span></span>|  
|`Implements`|<span data-ttu-id="6dbca-137">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-137">Optional.</span></span> <span data-ttu-id="6dbca-138">Consulte a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-138">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>|  
|`interfacenames`|<span data-ttu-id="6dbca-139">Necessário se você usar `Implements`.</span><span class="sxs-lookup"><span data-stu-id="6dbca-139">Required if you use `Implements`.</span></span> <span data-ttu-id="6dbca-140">Os nomes das interfaces que esse tipo implementa.</span><span class="sxs-lookup"><span data-stu-id="6dbca-140">The names of the interfaces this type implements.</span></span>|  
|`variabledeclarations`|<span data-ttu-id="6dbca-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-141">Optional.</span></span> <span data-ttu-id="6dbca-142">Instruções que declaram variáveis e eventos adicionais para o tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-142">Statements which declare additional variables and events for the type.</span></span>|  
|`proceduredeclarations`|<span data-ttu-id="6dbca-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6dbca-143">Optional.</span></span> <span data-ttu-id="6dbca-144">Instruções que declaram e definem procedimentos adicionais para o tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-144">Statements which declare and define additional procedures for the type.</span></span>|  
|<span data-ttu-id="6dbca-145">`End Class` ou `End Structure`</span><span class="sxs-lookup"><span data-stu-id="6dbca-145">`End Class` or `End Structure`</span></span>|<span data-ttu-id="6dbca-146">Encerra este `Class` parcial ou `Structure` definição.</span><span class="sxs-lookup"><span data-stu-id="6dbca-146">Ends this partial `Class` or `Structure` definition.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dbca-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="6dbca-147">Remarks</span></span>  
 <span data-ttu-id="6dbca-148">Visual Basic usa definições de classe parcial para separar o código gerado do código criado pelo usuário em arquivos de origem separados.</span><span class="sxs-lookup"><span data-stu-id="6dbca-148">Visual Basic uses partial-class definitions to separate generated code from user-authored code in separate source files.</span></span> <span data-ttu-id="6dbca-149">Por exemplo, o **Windows Form Designer** define classes parciais para controles, como <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="6dbca-149">For example, the **Windows Form Designer** defines partial classes for controls such as <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="6dbca-150">Você não deve modificar o código gerado nesses controles.</span><span class="sxs-lookup"><span data-stu-id="6dbca-150">You should not modify the generated code in these controls.</span></span>  
  
 <span data-ttu-id="6dbca-151">Todas as regras para classe, estrutura, interface e criação de módulo, como aquelas para uso e herança de modificador, se aplicam ao criar um tipo parcial.</span><span class="sxs-lookup"><span data-stu-id="6dbca-151">All the rules for class, structure, interface, and module creation, such as those for modifier usage and inheritance, apply when creating a partial type.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="6dbca-152">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="6dbca-152">Best Practices</span></span>  
  
- <span data-ttu-id="6dbca-153">Em circunstâncias normais, você não deve dividir o desenvolvimento de um único tipo entre duas ou mais declarações.</span><span class="sxs-lookup"><span data-stu-id="6dbca-153">Under normal circumstances, you should not split the development of a single type across two or more declarations.</span></span> <span data-ttu-id="6dbca-154">Portanto, na maioria dos casos, você não precisa da palavra-chave `Partial`.</span><span class="sxs-lookup"><span data-stu-id="6dbca-154">Therefore, in most cases you do not need the `Partial` keyword.</span></span>  
  
- <span data-ttu-id="6dbca-155">Para facilitar a leitura, todas as declarações parciais de um tipo devem incluir a palavra-chave `Partial`.</span><span class="sxs-lookup"><span data-stu-id="6dbca-155">For readability, every partial declaration of a type should include the `Partial` keyword.</span></span> <span data-ttu-id="6dbca-156">O compilador permite no máximo uma declaração parcial para omitir a palavra-chave; se dois ou mais omitirem, o compilador sinalizará um erro.</span><span class="sxs-lookup"><span data-stu-id="6dbca-156">The compiler allows at most one partial declaration to omit the keyword; if two or more omit it the compiler signals an error.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6dbca-157">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6dbca-157">Behavior</span></span>  
  
- <span data-ttu-id="6dbca-158">**União de declarações.**</span><span class="sxs-lookup"><span data-stu-id="6dbca-158">**Union of Declarations.**</span></span> <span data-ttu-id="6dbca-159">O compilador trata o tipo como a União de todas as suas declarações parciais.</span><span class="sxs-lookup"><span data-stu-id="6dbca-159">The compiler treats the type as the union of all its partial declarations.</span></span> <span data-ttu-id="6dbca-160">Cada modificador de cada definição parcial se aplica a todo o tipo e todos os membros de todas as definições parciais estão disponíveis para todo o tipo.</span><span class="sxs-lookup"><span data-stu-id="6dbca-160">Every modifier from every partial definition applies to the entire type, and every member from every partial definition is available to the entire type.</span></span>  
  
- <span data-ttu-id="6dbca-161">**Promoção de tipos não permitida para tipos parciais em módulos.**</span><span class="sxs-lookup"><span data-stu-id="6dbca-161">**Type Promotion Not Allowed For Partial Types in Modules.**</span></span> <span data-ttu-id="6dbca-162">Se uma definição parcial estiver dentro de um módulo, a promoção de tipos desse tipo será automaticamente derrotada.</span><span class="sxs-lookup"><span data-stu-id="6dbca-162">If a partial definition is inside a module, type promotion of that type is automatically defeated.</span></span> <span data-ttu-id="6dbca-163">Nesse caso, um conjunto de definições parciais pode causar resultados inesperados e até mesmo erros de compilador.</span><span class="sxs-lookup"><span data-stu-id="6dbca-163">In such a case, a set of partial definitions can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="6dbca-164">Para obter mais informações, consulte [promoção de tipos](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span><span class="sxs-lookup"><span data-stu-id="6dbca-164">For more information, see [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).</span></span>  
  
     <span data-ttu-id="6dbca-165">O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.</span><span class="sxs-lookup"><span data-stu-id="6dbca-165">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
 <span data-ttu-id="6dbca-166">A palavra-chave `Partial` pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="6dbca-166">The `Partial` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6dbca-167">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="6dbca-167">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6dbca-168">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="6dbca-168">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6dbca-169">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6dbca-169">Example</span></span>  
 <span data-ttu-id="6dbca-170">O exemplo a seguir divide a definição da classe `sampleClass` em duas declarações, cada uma delas define um procedimento de `Sub` diferente.</span><span class="sxs-lookup"><span data-stu-id="6dbca-170">The following example splits the definition of class `sampleClass` into two declarations, each of which defines a different `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 <span data-ttu-id="6dbca-171">As duas definições parciais no exemplo anterior podem estar no mesmo arquivo de origem ou em dois arquivos de origem diferentes.</span><span class="sxs-lookup"><span data-stu-id="6dbca-171">The two partial definitions in the preceding example could be in the same source file or in two different source files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbca-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dbca-172">See also</span></span>

- [<span data-ttu-id="6dbca-173">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="6dbca-173">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="6dbca-174">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="6dbca-174">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="6dbca-175">Tipo de promoção</span><span class="sxs-lookup"><span data-stu-id="6dbca-175">Type Promotion</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
- [<span data-ttu-id="6dbca-176">Sombras</span><span class="sxs-lookup"><span data-stu-id="6dbca-176">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6dbca-177">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6dbca-177">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="6dbca-178">Métodos Parciais</span><span class="sxs-lookup"><span data-stu-id="6dbca-178">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
