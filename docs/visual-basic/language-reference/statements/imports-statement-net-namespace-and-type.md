---
title: "Instrução Imports (tipo e Namespace .NET) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Imports
- imports
dev_langs:
- VB
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
caps.latest.revision: 40
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: af177874c3278efd348b53a2b74b4d49d6628c61
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="59df4-102">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="59df4-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="59df4-103">Permite digitar os nomes para se referir a qualificação de namespace.</span><span class="sxs-lookup"><span data-stu-id="59df4-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59df4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59df4-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="59df4-105">Partes</span><span class="sxs-lookup"><span data-stu-id="59df4-105">Parts</span></span>  
  
|<span data-ttu-id="59df4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="59df4-106">Term</span></span>|<span data-ttu-id="59df4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="59df4-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="59df4-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59df4-108">Optional.</span></span> <span data-ttu-id="59df4-109">Um *alias de importação* ou nome pelo qual o código pode se referir a `namespace` em vez da cadeia de caracteres de qualificação completa.</span><span class="sxs-lookup"><span data-stu-id="59df4-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="59df4-110">Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="59df4-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="59df4-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="59df4-111">Required.</span></span> <span data-ttu-id="59df4-112">O nome totalmente qualificado do namespace sendo importado.</span><span class="sxs-lookup"><span data-stu-id="59df4-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="59df4-113">Pode ser uma cadeia de caracteres de namespaces aninhada em qualquer nível.</span><span class="sxs-lookup"><span data-stu-id="59df4-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="59df4-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59df4-114">Optional.</span></span> <span data-ttu-id="59df4-115">O nome de um elemento de programação declarado no namespace.</span><span class="sxs-lookup"><span data-stu-id="59df4-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="59df4-116">Pode ser qualquer elemento contêiner.</span><span class="sxs-lookup"><span data-stu-id="59df4-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59df4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="59df4-117">Remarks</span></span>  
 <span data-ttu-id="59df4-118">O `Imports` instrução permite tipos que estão contidos em um determinado namespace a ser referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="59df4-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="59df4-119">Você pode fornecer um único nome de namespace ou uma cadeia de caracteres de namespaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="59df4-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="59df4-120">Cada namespace aninhado é separado do namespace de nível superior próximo por um período (`.`), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="59df4-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="59df4-121">Cada arquivo de origem pode conter qualquer número de `Imports` instruções.</span><span class="sxs-lookup"><span data-stu-id="59df4-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="59df4-122">Estas deve seguir qualquer declaração de opção, como o `Option Strict` instrução e eles devem preceder qualquer declaração de elemento de programação, como `Module` ou `Class` instruções.</span><span class="sxs-lookup"><span data-stu-id="59df4-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="59df4-123">Você pode usar `Imports` somente no nível de arquivo.</span><span class="sxs-lookup"><span data-stu-id="59df4-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="59df4-124">Isso significa que o contexto da declaração para importação deve ser um arquivo de origem e não pode ser um namespace, classe, estrutura, módulo, interface, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="59df4-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="59df4-125">Observe que o `Imports` instrução não torna os elementos de outros projetos e assemblies disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="59df4-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="59df4-126">Importar não toma o lugar de configurar uma referência.</span><span class="sxs-lookup"><span data-stu-id="59df4-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="59df4-127">Ele apenas remove a necessidade de qualificar nomes que já estão disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="59df4-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="59df4-128">Para obter mais informações, consulte "Importing Containing Elements" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="59df4-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59df4-129">Você pode definir implícita `Imports` instruções usando o [referências de página, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="59df4-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="59df4-130">Para obter mais informações, consulte [como: Adicionar ou remover Namespaces importados (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e).</span><span class="sxs-lookup"><span data-stu-id="59df4-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="59df4-131">Aliases de importação</span><span class="sxs-lookup"><span data-stu-id="59df4-131">Import Aliases</span></span>  
 <span data-ttu-id="59df4-132">Um *alias de importação* define o alias para um namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="59df4-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="59df4-133">Aliases de importação são úteis quando você precisa usar itens com o mesmo nome declarado em um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="59df4-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="59df4-134">Para obter mais informações e um exemplo, consulte "Qualificar um nome de elemento" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="59df4-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="59df4-135">Você não deve declarar um membro no nível de módulo com o mesmo nome como `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="59df4-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="59df4-136">Se você fizer isso, o compilador do Visual Basic usa `aliasname` apenas para o membro declarado e não o reconhece como um alias de importação.</span><span class="sxs-lookup"><span data-stu-id="59df4-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="59df4-137">Embora a sintaxe usada para declarar um alias de importação é como aquela usada para importar um prefixo de namespace XML, os resultados são diferentes.</span><span class="sxs-lookup"><span data-stu-id="59df4-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="59df4-138">Um alias de importação pode ser usado como uma expressão em seu código, enquanto que um prefixo de namespace XML pode ser usado apenas em literais XML ou propriedades de eixo XML como o prefixo para um elemento qualificado ou o nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="59df4-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="59df4-139">Nomes de elementos</span><span class="sxs-lookup"><span data-stu-id="59df4-139">Element Names</span></span>  
 <span data-ttu-id="59df4-140">Se você fornecer `element`, ele deve representar um *elemento contêiner*, ou seja, um elemento de programação que pode conter outros elementos.</span><span class="sxs-lookup"><span data-stu-id="59df4-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="59df4-141">Elementos de contêiner incluem classes, estruturas, módulos, interfaces e enumerações.</span><span class="sxs-lookup"><span data-stu-id="59df4-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="59df4-142">O escopo dos elementos feitos disponíveis por uma `Imports` instrução depende de você especifica `element`.</span><span class="sxs-lookup"><span data-stu-id="59df4-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="59df4-143">Se você especificar apenas `namespace`, tudo exclusivamente nomeado membros do namespace e os elementos de contêiner dentro desse namespace, estão disponíveis sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="59df4-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="59df4-144">Se você especificar ambas `namespace` e `element`, somente os membros daquele elemento estão disponíveis sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="59df4-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59df4-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59df4-145">Example</span></span>  
 <span data-ttu-id="59df4-146">O exemplo a seguir retorna todas as pastas na pasta C:\ usando a <xref:System.IO.DirectoryInfo>classe.</xref:System.IO.DirectoryInfo></span><span class="sxs-lookup"><span data-stu-id="59df4-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="59df4-147">O código não tem nenhum `Imports` instruções na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="59df4-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="59df4-148">Portanto, o `DirectoryInfo`, <xref:System.Text.StringBuilder>, e <xref:Microsoft.VisualBasic.ControlChars.CrLf>referências são inteiramente qualificadas com os namespaces.</xref:Microsoft.VisualBasic.ControlChars.CrLf> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="59df4-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 <span data-ttu-id="59df4-149">[!code-vb[VbVbalrStatements&#152;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="59df4-149">[!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="59df4-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59df4-150">Example</span></span>  
 <span data-ttu-id="59df4-151">O exemplo a seguir inclui `Imports` instruções para os namespaces referenciados.</span><span class="sxs-lookup"><span data-stu-id="59df4-151">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="59df4-152">Portanto, os tipos não precisam ser totalmente qualificados com os namespaces.</span><span class="sxs-lookup"><span data-stu-id="59df4-152">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 <span data-ttu-id="59df4-153">[!code-vb[VbVbalrStatements&#153;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="59df4-153">[!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]</span></span>  
  
 <span data-ttu-id="59df4-154">[!code-vb[VbVbalrStatements&#154;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="59df4-154">[!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="59df4-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59df4-155">Example</span></span>  
 <span data-ttu-id="59df4-156">O exemplo a seguir inclui `Imports` instruções que crie aliases para os espaços para nome referenciados.</span><span class="sxs-lookup"><span data-stu-id="59df4-156">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="59df4-157">Os tipos são qualificados com os alias.</span><span class="sxs-lookup"><span data-stu-id="59df4-157">The types are qualified with the aliases.</span></span>  
  
 <span data-ttu-id="59df4-158">[!code-vb[VbVbalrStatements&#155;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="59df4-158">[!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]</span></span>  
  
 <span data-ttu-id="59df4-159">[!code-vb[VbVbalrStatements&#156;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="59df4-159">[!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="59df4-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59df4-160">Example</span></span>  
 <span data-ttu-id="59df4-161">O exemplo a seguir inclui `Imports` instruções que criam aliases para os tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="59df4-161">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="59df4-162">Os aliases são usados para especificar os tipos.</span><span class="sxs-lookup"><span data-stu-id="59df4-162">Aliases are used to specify the types.</span></span>  
  
 <span data-ttu-id="59df4-163">[!code-vb[VbVbalrStatements&#157;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="59df4-163">[!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]</span></span>  
  
 <span data-ttu-id="59df4-164">[!code-vb[VbVbalrStatements&#158;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="59df4-164">[!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59df4-165">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59df4-165">See Also</span></span>  
 <span data-ttu-id="59df4-166">[Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="59df4-166">[Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="59df4-167"> [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="59df4-167"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="59df4-168"> [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="59df4-168"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="59df4-169"> [Instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="59df4-169"> [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="59df4-170"> [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="59df4-170"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
