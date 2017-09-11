---
title: Atributo lista (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
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
ms.openlocfilehash: 6aea239e2e0d8a266b8eb6ba2876fb109e077c46
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="d87dc-102">Lista de atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d87dc-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="d87dc-103">Especifica os atributos a serem aplicadas a um elemento de programação declarado.</span><span class="sxs-lookup"><span data-stu-id="d87dc-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="d87dc-104">Vários atributos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d87dc-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="d87dc-105">A seguir está a sintaxe para um atributo.</span><span class="sxs-lookup"><span data-stu-id="d87dc-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87dc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d87dc-106">Syntax</span></span>  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="d87dc-107">Partes</span><span class="sxs-lookup"><span data-stu-id="d87dc-107">Parts</span></span>  
 `attributemodifier`  
 <span data-ttu-id="d87dc-108">Necessário para os atributos aplicados no início de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="d87dc-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="d87dc-109">Pode ser [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou [módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="d87dc-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>  
  
 `attributename`  
 <span data-ttu-id="d87dc-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d87dc-110">Required.</span></span> <span data-ttu-id="d87dc-111">Nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="d87dc-111">Name of the attribute.</span></span>  
  
 `attributearguments`  
 <span data-ttu-id="d87dc-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d87dc-112">Optional.</span></span> <span data-ttu-id="d87dc-113">Lista de argumentos posicionais para este atributo.</span><span class="sxs-lookup"><span data-stu-id="d87dc-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="d87dc-114">Vários argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d87dc-114">Multiple arguments are separated by commas.</span></span>  
  
 `attributeinitializer`  
 <span data-ttu-id="d87dc-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d87dc-115">Optional.</span></span> <span data-ttu-id="d87dc-116">Lista de inicializadores de variável ou propriedade para este atributo.</span><span class="sxs-lookup"><span data-stu-id="d87dc-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="d87dc-117">Inicializadores múltiplos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="d87dc-117">Multiple initializers are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d87dc-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="d87dc-118">Remarks</span></span>  
 <span data-ttu-id="d87dc-119">Você pode aplicar um ou mais atributos para praticamente qualquer elemento de programação (tipos, procedimentos, propriedades e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="d87dc-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="d87dc-120">Atributos aparecem nos metadados do assembly, e eles podem ajudar você anotar o código ou especificar como usar um determinado elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="d87dc-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="d87dc-121">Você pode aplicar atributos definidos pelo Visual Basic e o .NET Framework, e você pode definir seus próprios atributos.</span><span class="sxs-lookup"><span data-stu-id="d87dc-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="d87dc-122">Para obter mais informações sobre quando usar atributos, consulte [visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="d87dc-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="d87dc-123">Para obter informações sobre nomes de atributo, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d87dc-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d87dc-124">Regras</span><span class="sxs-lookup"><span data-stu-id="d87dc-124">Rules</span></span>  
  
-   <span data-ttu-id="d87dc-125">**Posicionamento.**</span><span class="sxs-lookup"><span data-stu-id="d87dc-125">**Placement.**</span></span> <span data-ttu-id="d87dc-126">Você pode aplicar atributos para elementos de programação mais declarados.</span><span class="sxs-lookup"><span data-stu-id="d87dc-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="d87dc-127">Para aplicar um ou mais atributos, você deve colocar um *bloco de atributo* no início da declaração do elemento.</span><span class="sxs-lookup"><span data-stu-id="d87dc-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="d87dc-128">Cada entrada na lista de atributos especifica um atributo que você deseja aplicar, e o modificador e argumentos que você está usando para esta chamada do atributo.</span><span class="sxs-lookup"><span data-stu-id="d87dc-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
-   <span data-ttu-id="d87dc-129">**Colchetes angulares.**</span><span class="sxs-lookup"><span data-stu-id="d87dc-129">**Angle Brackets.**</span></span> <span data-ttu-id="d87dc-130">Se você fornecer uma lista de atributos, você deve colocá-lo entre colchetes angulares ("`<`"e"`>`").</span><span class="sxs-lookup"><span data-stu-id="d87dc-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
-   <span data-ttu-id="d87dc-131">**Parte da declaração.**</span><span class="sxs-lookup"><span data-stu-id="d87dc-131">**Part of the Declaration.**</span></span> <span data-ttu-id="d87dc-132">O atributo deve ser parte da declaração do elemento, não uma instrução separada.</span><span class="sxs-lookup"><span data-stu-id="d87dc-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="d87dc-133">Você pode usar a sequência de continuação de linha (" `_`") para estender a instrução de declaração em várias linhas de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="d87dc-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
-   <span data-ttu-id="d87dc-134">**Modificadores.**</span><span class="sxs-lookup"><span data-stu-id="d87dc-134">**Modifiers.**</span></span> <span data-ttu-id="d87dc-135">Um modificador de atributo (`Assembly` ou `Module`) é necessário em cada atributo aplicado a um elemento de programação no início de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="d87dc-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="d87dc-136">Modificadores de atributo não são permitidos em atributos aplicados aos elementos que não estão no início de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="d87dc-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
-   <span data-ttu-id="d87dc-137">**Argumentos.**</span><span class="sxs-lookup"><span data-stu-id="d87dc-137">**Arguments.**</span></span> <span data-ttu-id="d87dc-138">Todos os argumentos posicionais para um atributo devem preceder qualquer variável ou inicializadores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d87dc-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d87dc-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d87dc-139">Example</span></span>  
 <span data-ttu-id="d87dc-140">O exemplo a seguir aplica-se a <xref:System.Runtime.InteropServices.DllImportAttribute>atributo a uma definição de uma `Function` procedimento.</xref:System.Runtime.InteropServices.DllImportAttribute></span><span class="sxs-lookup"><span data-stu-id="d87dc-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 <span data-ttu-id="d87dc-141">[!code-vb[VbVbalrStatements n º&1;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d87dc-141">[!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]</span></span>  
  
 <span data-ttu-id="d87dc-142"><xref:System.Runtime.InteropServices.DllImportAttribute>indica que o procedimento atribuído representa um ponto de entrada em uma biblioteca de vínculo dinâmico (DLL) não gerenciada.</xref:System.Runtime.InteropServices.DllImportAttribute></span><span class="sxs-lookup"><span data-stu-id="d87dc-142"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="d87dc-143">O atributo fornece o nome da DLL como um argumento posicional e as outras informações como inicializadores de variável.</span><span class="sxs-lookup"><span data-stu-id="d87dc-143">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d87dc-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d87dc-144">See Also</span></span>  
 <span data-ttu-id="d87dc-145">[Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) </span><span class="sxs-lookup"><span data-stu-id="d87dc-145">[Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) </span></span>  
<span data-ttu-id="d87dc-146"> [Módulo \<palavra-chave >](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span><span class="sxs-lookup"><span data-stu-id="d87dc-146"> [Module \<keyword>](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span></span>  
<span data-ttu-id="d87dc-147"> [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="d87dc-147"> [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="d87dc-148"> [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span><span class="sxs-lookup"><span data-stu-id="d87dc-148"> [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)</span></span>

