---
title: Módulo &lt;palavra-chave&gt; (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 3b4b09469a3f22b5e5c7faa98d5db7b3522ed236
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586469"
---
# <a name="module-ltkeywordgt-visual-basic"></a><span data-ttu-id="a862c-102">Módulo &lt;palavra-chave&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a862c-102">Module &lt;keyword&gt; (Visual Basic)</span></span>
<span data-ttu-id="a862c-103">Especifica que um atributo no início de um arquivo de origem se aplica ao módulo assembly atual.</span><span class="sxs-lookup"><span data-stu-id="a862c-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a862c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a862c-104">Remarks</span></span>  
 <span data-ttu-id="a862c-105">Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="a862c-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="a862c-106">Aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="a862c-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="a862c-107">Se um atributo pertence não apenas para o próximo elemento, mas para o módulo do assembly atual, coloque o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Module` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="a862c-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="a862c-108">Se ele se aplica a todo o assembly, você usa o [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="a862c-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="a862c-109">O `Module` modificador não é igual a [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a862c-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a862c-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a862c-110">See also</span></span>
- [<span data-ttu-id="a862c-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="a862c-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="a862c-112">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="a862c-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="a862c-113">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="a862c-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

