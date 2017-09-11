---
title: "Instruções &quot;#Region&quot; e &quot;#End Region&quot; não são válidas dentro lambdas multilinha corpos de método | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
dev_langs:
- VB
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 10
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
ms.openlocfilehash: 0800ab7134277ec4a73ebd5a3514ad4e15a5977d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="acc43-102">Instruções '#Region' e '#End Region' não são válidas dentro do método corpos/lambdas multilinha</span><span class="sxs-lookup"><span data-stu-id="acc43-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="acc43-103">O `#Region` bloco deve ser declarado em um nível de classe, módulo ou namespace.</span><span class="sxs-lookup"><span data-stu-id="acc43-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="acc43-104">Uma região recolhível pode incluir um ou mais procedimentos, mas ele não pode começar ou terminar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="acc43-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="acc43-105">**ID do erro:** BC32025</span><span class="sxs-lookup"><span data-stu-id="acc43-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="acc43-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="acc43-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="acc43-107">Certifique-se de que o procedimento anterior é encerrado corretamente com um `End Function` ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="acc43-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="acc43-108">Verifique se o `#Region` e `#End Region` diretivas estão no mesmo bloco de código.</span><span class="sxs-lookup"><span data-stu-id="acc43-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc43-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acc43-109">See Also</span></span>  
 [<span data-ttu-id="acc43-110">Diretiva #Region</span><span class="sxs-lookup"><span data-stu-id="acc43-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
