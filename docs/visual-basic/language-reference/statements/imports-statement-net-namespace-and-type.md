---
title: Instrução Imports-namespace e tipo do .NET
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
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351074"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="d3d8c-102">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="d3d8c-102">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="d3d8c-103">Permite que nomes de tipos sejam referenciados sem qualificação de namespace.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-103">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3d8c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3d8c-104">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="d3d8c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d3d8c-105">Parts</span></span>

|<span data-ttu-id="d3d8c-106">Termo</span><span class="sxs-lookup"><span data-stu-id="d3d8c-106">Term</span></span>|<span data-ttu-id="d3d8c-107">Definição</span><span class="sxs-lookup"><span data-stu-id="d3d8c-107">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="d3d8c-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-108">Optional.</span></span> <span data-ttu-id="d3d8c-109">Um *alias de importação* ou nome pelo qual o código pode se referir a `namespace` em vez da cadeia de caracteres de qualificação completa.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="d3d8c-110">Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d3d8c-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="d3d8c-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-111">Required.</span></span> <span data-ttu-id="d3d8c-112">O nome totalmente qualificado do namespace que está sendo importado.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="d3d8c-113">Pode ser uma cadeia de caracteres de namespaces aninhados em qualquer nível.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-113">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="d3d8c-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-114">Optional.</span></span> <span data-ttu-id="d3d8c-115">O nome de um elemento de programação declarado no namespace.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="d3d8c-116">Pode ser qualquer elemento de contêiner.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-116">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d3d8c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3d8c-117">Remarks</span></span>

<span data-ttu-id="d3d8c-118">A instrução `Imports` permite que os tipos contidos em um determinado namespace sejam referenciados diretamente.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="d3d8c-119">Você pode fornecer um único nome de namespace ou uma cadeia de caracteres de namespaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="d3d8c-120">Cada namespace aninhado é separado do próximo namespace de nível mais alto por um ponto (`.`), como ilustra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d3d8c-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="d3d8c-121">Cada arquivo de origem pode conter qualquer número de instruções `Imports`.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="d3d8c-122">Eles devem seguir qualquer declaração de opção, como a instrução `Option Strict`, e devem preceder quaisquer declarações de elemento de programação, como `Module` ou `Class` instruções.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="d3d8c-123">Você pode usar `Imports` somente no nível de arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="d3d8c-124">Isso significa que o contexto de declaração para importação deve ser um arquivo de origem e não pode ser um namespace, classe, estrutura, módulo, interface, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="d3d8c-125">Observe que a instrução `Imports` não torna elementos de outros projetos e assemblies disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="d3d8c-126">A importação não tem o lugar de definir uma referência.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="d3d8c-127">Ele apenas remove a necessidade de qualificar nomes que já estão disponíveis para seu projeto.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="d3d8c-128">Para obter mais informações, consulte "importando elementos continentes" em [referências a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d8c-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d3d8c-129">Você pode definir instruções `Imports` implícitas usando a [página referências, designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d3d8c-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="d3d8c-130">Para obter mais informações, consulte [como: Adicionar ou remover namespaces importados (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d3d8c-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="d3d8c-131">Aliases de importação</span><span class="sxs-lookup"><span data-stu-id="d3d8c-131">Import Aliases</span></span>

<span data-ttu-id="d3d8c-132">Um *alias de importação* define o alias para um namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="d3d8c-133">Os aliases de importação são úteis quando você precisa usar itens com o mesmo nome que são declarados em um ou mais namespaces.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="d3d8c-134">Para obter mais informações e um exemplo, consulte "qualificando um nome de elemento" em [referências a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d8c-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="d3d8c-135">Você não deve declarar um membro no nível de módulo com o mesmo nome que `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="d3d8c-136">Se você fizer isso, o compilador Visual Basic usa `aliasname` apenas para o membro declarado e não o reconhece mais como um alias de importação.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="d3d8c-137">Embora a sintaxe usada para declarar um alias de importação seja como a usada para importar um prefixo de namespace XML, os resultados são diferentes.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="d3d8c-138">Um alias de importação pode ser usado como uma expressão em seu código, enquanto um prefixo de namespace XML pode ser usado somente em literais XML ou propriedades de eixo XML como o prefixo para um elemento qualificado ou nome de atributo.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="d3d8c-139">Nomes de elementos</span><span class="sxs-lookup"><span data-stu-id="d3d8c-139">Element Names</span></span>

<span data-ttu-id="d3d8c-140">Se você fornecer `element`, ele deve representar um *elemento de contêiner*, ou seja, um elemento de programação que pode conter outros elementos.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="d3d8c-141">Elementos de contêiner incluem classes, estruturas, módulos, interfaces e enumerações.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="d3d8c-142">O escopo dos elementos disponibilizados por uma instrução `Imports` depende se você especifica `element`.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="d3d8c-143">Se você especificar apenas `namespace`, todos os membros nomeados exclusivamente desse namespace e os membros dos elementos de contêiner dentro desse namespace estarão disponíveis sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="d3d8c-144">Se você especificar `namespace` e `element`, somente os membros desse elemento estarão disponíveis sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="d3d8c-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3d8c-145">Example</span></span>

<span data-ttu-id="d3d8c-146">O exemplo a seguir retorna todas as pastas no diretório *C:\\* usando a classe <xref:System.IO.DirectoryInfo>:</span><span class="sxs-lookup"><span data-stu-id="d3d8c-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="d3d8c-147">O código não tem instruções `Imports` na parte superior do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="d3d8c-148">Portanto, as referências <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>e <xref:Microsoft.VisualBasic.ControlChars.CrLf> são totalmente qualificadas com os namespaces.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="d3d8c-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3d8c-149">Example</span></span>

<span data-ttu-id="d3d8c-150">O exemplo a seguir inclui `Imports` instruções para os namespaces referenciados.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="d3d8c-151">Portanto, os tipos não precisam ser totalmente qualificados com os namespaces.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="d3d8c-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3d8c-152">Example</span></span>

<span data-ttu-id="d3d8c-153">O exemplo a seguir inclui `Imports` instruções que criam aliases para os namespaces referenciados.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="d3d8c-154">Os tipos são qualificados com os aliases.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-154">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="d3d8c-155">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3d8c-155">Example</span></span>

<span data-ttu-id="d3d8c-156">O exemplo a seguir inclui `Imports` instruções que criam aliases para os tipos referenciados.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="d3d8c-157">Os aliases são usados para especificar os tipos.</span><span class="sxs-lookup"><span data-stu-id="d3d8c-157">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="d3d8c-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3d8c-158">See also</span></span>

- [<span data-ttu-id="d3d8c-159">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="d3d8c-159">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="d3d8c-160">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3d8c-160">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="d3d8c-161">Referências e a Instrução Imports</span><span class="sxs-lookup"><span data-stu-id="d3d8c-161">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="d3d8c-162">Instrução Imports (Namespace de XML)</span><span class="sxs-lookup"><span data-stu-id="d3d8c-162">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="d3d8c-163">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="d3d8c-163">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
