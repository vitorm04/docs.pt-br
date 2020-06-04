---
title: Lista de Atributos
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: f2400334182d373ea49c130fd17bc4f9943248d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408439"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="09539-102">Lista de atributos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09539-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="09539-103">Especifica os atributos a serem aplicados a um elemento de programação declarado.</span><span class="sxs-lookup"><span data-stu-id="09539-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="09539-104">Vários atributos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="09539-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="09539-105">Veja a seguir a sintaxe de um atributo.</span><span class="sxs-lookup"><span data-stu-id="09539-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09539-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09539-106">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="09539-107">Partes</span><span class="sxs-lookup"><span data-stu-id="09539-107">Parts</span></span>  
|||
|---|---|
|`attributemodifier`|<span data-ttu-id="09539-108">Necessário para atributos aplicados no início de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="09539-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="09539-109">Pode ser [assembly](../modifiers/assembly.md) ou [módulo](../modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="09539-109">Can be [Assembly](../modifiers/assembly.md) or [Module](../modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="09539-110">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="09539-110">Required.</span></span> <span data-ttu-id="09539-111">Nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="09539-111">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="09539-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="09539-112">Optional.</span></span> <span data-ttu-id="09539-113">Lista de argumentos posicionais para este atributo.</span><span class="sxs-lookup"><span data-stu-id="09539-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="09539-114">Vários argumentos são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="09539-114">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="09539-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="09539-115">Optional.</span></span> <span data-ttu-id="09539-116">Lista de inicializadores de variável ou propriedade para este atributo.</span><span class="sxs-lookup"><span data-stu-id="09539-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="09539-117">Vários inicializadores são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="09539-117">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="09539-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="09539-118">Remarks</span></span>  
 <span data-ttu-id="09539-119">Você pode aplicar um ou mais atributos a praticamente qualquer elemento de programação (tipos, procedimentos, propriedades e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="09539-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="09539-120">Os atributos aparecem nos metadados do assembly e podem ajudá-lo a anotar seu código ou especificar como usar um elemento de programação específico.</span><span class="sxs-lookup"><span data-stu-id="09539-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="09539-121">Você pode aplicar atributos definidos por Visual Basic e o .NET Framework, e pode definir seus próprios atributos.</span><span class="sxs-lookup"><span data-stu-id="09539-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="09539-122">Para obter mais informações sobre quando usar atributos, consulte [visão geral de atributos](../../programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="09539-122">For more information on when to use attributes, see [Attributes overview](../../programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="09539-123">Para obter informações sobre nomes de atributo, consulte [nomes de elemento declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="09539-123">For information on attribute names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="09539-124">Regras</span><span class="sxs-lookup"><span data-stu-id="09539-124">Rules</span></span>  
  
- <span data-ttu-id="09539-125">**Placement.**</span><span class="sxs-lookup"><span data-stu-id="09539-125">**Placement.**</span></span> <span data-ttu-id="09539-126">Você pode aplicar atributos aos elementos de programação mais declarados.</span><span class="sxs-lookup"><span data-stu-id="09539-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="09539-127">Para aplicar um ou mais atributos, você coloca um *bloco de atributo* no início da declaração do elemento.</span><span class="sxs-lookup"><span data-stu-id="09539-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="09539-128">Cada entrada na lista de atributos especifica um atributo que você deseja aplicar e o modificador e os argumentos que você está usando para essa invocação do atributo.</span><span class="sxs-lookup"><span data-stu-id="09539-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="09539-129">**Colchetes angulares.**</span><span class="sxs-lookup"><span data-stu-id="09539-129">**Angle Brackets.**</span></span> <span data-ttu-id="09539-130">Se você fornecer uma lista de atributos, deverá colocá-la entre colchetes angulares (" `<` " e " `>` ").</span><span class="sxs-lookup"><span data-stu-id="09539-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="09539-131">**Parte da declaração.**</span><span class="sxs-lookup"><span data-stu-id="09539-131">**Part of the Declaration.**</span></span> <span data-ttu-id="09539-132">O atributo deve ser parte da declaração do elemento, não de uma instrução separada.</span><span class="sxs-lookup"><span data-stu-id="09539-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="09539-133">Você pode usar a sequência de continuação de linha (" `_` ") para estender a instrução de declaração para várias linhas de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="09539-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="09539-134">**Modificadores.**</span><span class="sxs-lookup"><span data-stu-id="09539-134">**Modifiers.**</span></span> <span data-ttu-id="09539-135">Um modificador de atributo ( `Assembly` ou `Module` ) é necessário em cada atributo aplicado a um elemento de programação no início de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="09539-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="09539-136">Modificadores de atributo não são permitidos em atributos aplicados a elementos que não estão no início de um arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="09539-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="09539-137">**Argumentos.**</span><span class="sxs-lookup"><span data-stu-id="09539-137">**Arguments.**</span></span> <span data-ttu-id="09539-138">Todos os argumentos posicionais de um atributo devem preceder qualquer inicializador de variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="09539-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09539-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09539-139">Example</span></span>  
 <span data-ttu-id="09539-140">O exemplo a seguir aplica o <xref:System.Runtime.InteropServices.DllImportAttribute> atributo a uma definição de esqueleto de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="09539-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="09539-141"><xref:System.Runtime.InteropServices.DllImportAttribute>indica que o procedimento atribuído representa um ponto de entrada em uma DLL (biblioteca de vínculo dinâmico) não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="09539-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="09539-142">O atributo fornece o nome da DLL como um argumento posicional e as outras informações como inicializadores de variável.</span><span class="sxs-lookup"><span data-stu-id="09539-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09539-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="09539-143">See also</span></span>

- [<span data-ttu-id="09539-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="09539-144">Assembly</span></span>](../modifiers/assembly.md)
- [<span data-ttu-id="09539-145">Modulo\<keyword></span><span class="sxs-lookup"><span data-stu-id="09539-145">Module \<keyword></span></span>](../modifiers/module-keyword.md)
- [<span data-ttu-id="09539-146">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="09539-146">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="09539-147">Como: Quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="09539-147">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
