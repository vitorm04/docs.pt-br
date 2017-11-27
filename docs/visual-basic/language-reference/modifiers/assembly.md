---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef4434f0bc520abfc621567fc68e0b8bcfd6e381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="dca40-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dca40-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="dca40-103">Especifica que um atributo no início de um arquivo de origem se aplica ao assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="dca40-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dca40-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="dca40-104">Remarks</span></span>  
 <span data-ttu-id="dca40-105">Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="dca40-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="dca40-106">Aplicar um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="dca40-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="dca40-107">Se um atributo pertence não apenas ao seguinte elemento mas ao conjunto inteiro, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Assembly` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="dca40-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="dca40-108">Se ele se aplica ao módulo assembly atual, você usar o [módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="dca40-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="dca40-109">Você também pode aplicar um atributo a um assembly no arquivo AssemblyInfo vb, caso em que você não precisa usar um bloco de atributo em seu arquivo de código-fonte principal.</span><span class="sxs-lookup"><span data-stu-id="dca40-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca40-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dca40-110">See Also</span></span>  
 [<span data-ttu-id="dca40-111">Módulo \<palavra-chave ></span><span class="sxs-lookup"><span data-stu-id="dca40-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="dca40-112">Visão geral de atributos</span><span class="sxs-lookup"><span data-stu-id="dca40-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

