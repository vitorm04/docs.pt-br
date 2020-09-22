---
title: Assembly
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
ms.openlocfilehash: 34d6b94f31336e3e99b8ca981a9c4899e5a3d912
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875522"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="cced2-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cced2-102">Assembly (Visual Basic)</span></span>

<span data-ttu-id="cced2-103">Especifica que um atributo no início de um arquivo de origem se aplica a todo o assembly.</span><span class="sxs-lookup"><span data-stu-id="cced2-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cced2-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="cced2-104">Remarks</span></span>  

 <span data-ttu-id="cced2-105">Muitos atributos pertencem a um elemento de programação individual, como uma classe ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="cced2-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="cced2-106">Você aplica esse atributo, anexando o bloco de atributo, entre colchetes angulares ( `< >` ), diretamente à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="cced2-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="cced2-107">Se um atributo pertencer não apenas ao elemento a seguir, mas ao assembly inteiro, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com a `Assembly` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="cced2-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="cced2-108">Se se aplicar ao módulo do assembly atual, você usará a palavra-chave do [módulo](module-keyword.md) .</span><span class="sxs-lookup"><span data-stu-id="cced2-108">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="cced2-109">Você também pode aplicar um atributo a um assembly no arquivo AssemblyInfo. vb, caso em que você não precisa usar um bloco de atributos em seu arquivo de código-fonte principal.</span><span class="sxs-lookup"><span data-stu-id="cced2-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cced2-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="cced2-110">See also</span></span>

- [<span data-ttu-id="cced2-111">Modulo \<keyword></span><span class="sxs-lookup"><span data-stu-id="cced2-111">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="cced2-112">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="cced2-112">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
