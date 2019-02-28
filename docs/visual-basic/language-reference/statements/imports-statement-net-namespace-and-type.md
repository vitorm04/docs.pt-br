---
title: Instrução Imports - .NET Namespace e tipo (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 93b299ffd8d2be1b1fabfd752e75d18ef87714b2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974374"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="6eda3-102">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="6eda3-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="6eda3-103">Permite que digite o nome para ser referenciados sem qualificação de namespace.</span><span class="sxs-lookup"><span data-stu-id="6eda3-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eda3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6eda3-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="6eda3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="6eda3-105">Parts</span></span>  
  
|<span data-ttu-id="6eda3-106">Termo</span><span class="sxs-lookup"><span data-stu-id="6eda3-106">Term</span></span>|<span data-ttu-id="6eda3-107">Definição</span><span class="sxs-lookup"><span data-stu-id="6eda3-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="6eda3-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6eda3-108">Optional.</span></span> <span data-ttu-id="6eda3-109">Uma *alias de importação* ou o nome pelo qual o código pode se referir a `namespace` em vez da cadeia de caracteres de qualificação completa.</span><span class="sxs-lookup"><span data-stu-id="6eda3-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="6eda3-110">Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6eda3-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="6eda3-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6eda3-111">Required.</span></span> <span data-ttu-id="6eda3-112">O nome totalmente qualificado do namespace que está sendo importado.</span><span class="sxs-lookup"><span data-stu-id="6eda3-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="6eda3-113">Pode ser uma cadeia de caracteres de namespaces aninhada em qualquer nível.</span><span class="sxs-lookup"><span data-stu-id="6eda3-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="6eda3-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6eda3-114">Optional.</span></span> <span data-ttu-id="6eda3-115">O nome de um elemento de programação declarado no namespace.</span><span class="sxs-lookup"><span data-stu-id="6eda3-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="6eda3-116">Pode ser qualquer elemento de contêiner.</span><span class="sxs-lookup"><span data-stu-id="6eda3-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eda3-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="6eda3-117">Remarks</span></span>  
 <span data-ttu-id="6eda3-118">O `Imports` instrução permite tipos que estão contidos em um namespace específico a ser referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="6eda3-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="6eda3-119">Você pode fornecer um nome de namespace único ou uma cadeia de caracteres de namespaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="6eda3-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="6eda3-120">Cada namespace aninhado é separado do namespace de nível superior próximo por um período (`.`), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6eda3-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="6eda3-121">Cada arquivo de origem pode conter qualquer número de `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="6eda3-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="6eda3-122">Estas deve seguir qualquer declaração de opção, como o `Option Strict` instrução e eles devem preceder qualquer declaração de elemento de programação, como `Module` ou `Class` instruções.</span><span class="sxs-lookup"><span data-stu-id="6eda3-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="6eda3-123">Você pode usar `Imports` apenas no nível de arquivo.</span><span class="sxs-lookup"><span data-stu-id="6eda3-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="6eda3-124">Isso significa que o contexto da declaração de importação deve ser um arquivo de origem e não pode ser um namespace, classe, estrutura, módulo, interface, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="6eda3-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="6eda3-125">Observe que o `Imports` instrução não torna os elementos de outros projetos e assemblies disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6eda3-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="6eda3-126">Importar não toma o lugar de uma referência de configuração.</span><span class="sxs-lookup"><span data-stu-id="6eda3-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="6eda3-127">Ele apenas remove a necessidade de qualificar nomes que já estão disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6eda3-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="6eda3-128">Para obter mais informações, consulte "Importação de elementos que contém" na [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6eda3-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6eda3-129">Você pode definir implícita `Imports` instruções usando o [página referências, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6eda3-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="6eda3-130">Para obter mais informações, confira [Como: Adicionar ou remover Namespaces importados (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6eda3-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="6eda3-131">Aliases de importação</span><span class="sxs-lookup"><span data-stu-id="6eda3-131">Import Aliases</span></span>  
 <span data-ttu-id="6eda3-132">Uma *importação alias* define o alias para um namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="6eda3-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="6eda3-133">Aliases de importação são úteis quando você precisa usar itens com o mesmo nome que são declarados em um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="6eda3-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="6eda3-134">Para obter mais informações e um exemplo, consulte "Qualificando um nome de elemento" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6eda3-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="6eda3-135">Você não deve declarar um membro no nível de módulo com o mesmo nome que `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="6eda3-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="6eda3-136">Se você fizer isso, o compilador do Visual Basic usa `aliasname` somente para o membro declarado e não está mais reconhece como um alias de importação.</span><span class="sxs-lookup"><span data-stu-id="6eda3-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="6eda3-137">Embora a sintaxe usada para declarar um alias de importação é como aquela usada para importar um prefixo de namespace XML, os resultados são diferentes.</span><span class="sxs-lookup"><span data-stu-id="6eda3-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="6eda3-138">Um alias de importação pode ser usado como uma expressão em seu código, enquanto que um prefixo de namespace XML pode ser usado apenas em literais XML ou propriedades de eixo XML como o prefixo para um elemento qualificado ou o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="6eda3-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="6eda3-139">Nomes de elementos</span><span class="sxs-lookup"><span data-stu-id="6eda3-139">Element Names</span></span>  
 <span data-ttu-id="6eda3-140">Se você fornecer `element`, ele deve representar uma *elemento contêiner*, ou seja, um elemento de programação que pode conter outros elementos.</span><span class="sxs-lookup"><span data-stu-id="6eda3-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="6eda3-141">Elementos de contêiner incluem classes, estruturas, módulos, interfaces e enumerações.</span><span class="sxs-lookup"><span data-stu-id="6eda3-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="6eda3-142">O escopo dos elementos disponibilizado por um `Imports` instrução depende se você especificar `element`.</span><span class="sxs-lookup"><span data-stu-id="6eda3-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="6eda3-143">Se você especificar apenas `namespace`, tudo exclusivamente nomeada membros desse namespace e os elementos de contêiner dentro desse namespace, estão disponíveis sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="6eda3-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="6eda3-144">Se você especificar ambos `namespace` e `element`, somente os membros desse elemento estão disponíveis sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="6eda3-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eda3-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6eda3-145">Example</span></span>  
 <span data-ttu-id="6eda3-146">O exemplo a seguir retorna todas as pastas no diretório c:\. usando o <xref:System.IO.DirectoryInfo> classe.</span><span class="sxs-lookup"><span data-stu-id="6eda3-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="6eda3-147">O código não tem nenhum `Imports` instruções na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="6eda3-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="6eda3-148">Portanto, o `DirectoryInfo`, <xref:System.Text.StringBuilder>, e <xref:Microsoft.VisualBasic.ControlChars.CrLf> referências são todas totalmente qualificadas com os namespaces.</span><span class="sxs-lookup"><span data-stu-id="6eda3-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]  
  
## <a name="example"></a><span data-ttu-id="6eda3-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6eda3-149">Example</span></span>  
 <span data-ttu-id="6eda3-150">O exemplo a seguir inclui `Imports` instruções para os namespaces referenciados.</span><span class="sxs-lookup"><span data-stu-id="6eda3-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="6eda3-151">Portanto, os tipos não precisam ser totalmente qualificados com os namespaces.</span><span class="sxs-lookup"><span data-stu-id="6eda3-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]  
  
 [!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]  
  
## <a name="example"></a><span data-ttu-id="6eda3-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6eda3-152">Example</span></span>  
 <span data-ttu-id="6eda3-153">O exemplo a seguir inclui `Imports` instruções que criam aliases para os namespaces referenciados.</span><span class="sxs-lookup"><span data-stu-id="6eda3-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="6eda3-154">Os tipos são qualificados com os aliases.</span><span class="sxs-lookup"><span data-stu-id="6eda3-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]  
  
 [!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]  
  
## <a name="example"></a><span data-ttu-id="6eda3-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6eda3-155">Example</span></span>  
 <span data-ttu-id="6eda3-156">O exemplo a seguir inclui `Imports` instruções que criam aliases para tipos referenciados.</span><span class="sxs-lookup"><span data-stu-id="6eda3-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="6eda3-157">Os aliases são usados para especificar os tipos.</span><span class="sxs-lookup"><span data-stu-id="6eda3-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]  
  
 [!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]  
  
## <a name="see-also"></a><span data-ttu-id="6eda3-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6eda3-158">See also</span></span>
- [<span data-ttu-id="6eda3-159">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="6eda3-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="6eda3-160">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6eda3-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="6eda3-161">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="6eda3-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="6eda3-162">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="6eda3-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="6eda3-163">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="6eda3-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
