---
title: "Módulo &lt;palavra-chave&gt; (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ModuleAttribute
dev_langs:
- VB
helpviewer_keywords:
- Module keyword
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
caps.latest.revision: 13
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
ms.openlocfilehash: 7554c397fbfd3cd61cf19f760eb4664e2deb589b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="module-ltkeywordgt-visual-basic"></a><span data-ttu-id="69327-102">Módulo &lt;palavra-chave&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69327-102">Module &lt;keyword&gt; (Visual Basic)</span></span>
<span data-ttu-id="69327-103">Especifica que um atributo no início de um arquivo de origem se aplica ao módulo do assembly atual.</span><span class="sxs-lookup"><span data-stu-id="69327-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69327-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="69327-104">Remarks</span></span>  
 <span data-ttu-id="69327-105">Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="69327-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="69327-106">Você aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="69327-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="69327-107">Se um atributo pertence não apenas ao seguinte elemento mas ao módulo do assembly atual, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Module` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="69327-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="69327-108">Se ele se aplica ao conjunto inteiro, você usar o [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="69327-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="69327-109">O `Module` modificador não é igual a [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="69327-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69327-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69327-110">See Also</span></span>  
 <span data-ttu-id="69327-111">[Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) </span><span class="sxs-lookup"><span data-stu-id="69327-111">[Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) </span></span>  
<span data-ttu-id="69327-112"> [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="69327-112"> [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="69327-113"> [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span><span class="sxs-lookup"><span data-stu-id="69327-113"> [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span></span>


