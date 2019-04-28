---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 819fa9cf1bd25e9426fb1e75925a269fcf7a71cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801979"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="ebb7d-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebb7d-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="ebb7d-103">Especifica que um atributo no início de um arquivo de origem se aplica a todo o assembly.</span><span class="sxs-lookup"><span data-stu-id="ebb7d-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebb7d-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebb7d-104">Remarks</span></span>  
 <span data-ttu-id="ebb7d-105">Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="ebb7d-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="ebb7d-106">Aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="ebb7d-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="ebb7d-107">Se um atributo pertence não apenas para o seguinte elemento mas ao conjunto inteiro, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Assembly` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ebb7d-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="ebb7d-108">Se ele se aplica ao módulo assembly atual, você usar o [módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ebb7d-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="ebb7d-109">Você também pode aplicar um atributo a um assembly no arquivo AssemblyInfo vb, caso em que você não precisa usar um bloco de atributo em seu arquivo de código-fonte principal.</span><span class="sxs-lookup"><span data-stu-id="ebb7d-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb7d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebb7d-110">See also</span></span>

- [<span data-ttu-id="ebb7d-111">Módulo \<palavra-chave ></span><span class="sxs-lookup"><span data-stu-id="ebb7d-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="ebb7d-112">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="ebb7d-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
