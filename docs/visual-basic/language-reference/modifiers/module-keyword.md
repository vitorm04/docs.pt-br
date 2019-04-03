---
title: Módulo <keyword> (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: f6ded1184aedf1702f4b6e5eebb85709cf8e39f4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814270"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="845bc-102">Módulo \<palavra-chave > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="845bc-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="845bc-103">Especifica que um atributo no início de um arquivo de origem se aplica ao módulo assembly atual.</span><span class="sxs-lookup"><span data-stu-id="845bc-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="845bc-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="845bc-104">Remarks</span></span>  
 <span data-ttu-id="845bc-105">Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="845bc-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="845bc-106">Aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="845bc-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="845bc-107">Se um atributo pertence não apenas para o próximo elemento, mas para o módulo do assembly atual, coloque o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Module` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="845bc-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="845bc-108">Se ele se aplica a todo o assembly, você usa o [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="845bc-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="845bc-109">O `Module` modificador não é igual a [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="845bc-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845bc-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="845bc-110">See also</span></span>

- [<span data-ttu-id="845bc-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="845bc-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="845bc-112">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="845bc-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="845bc-113">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="845bc-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
