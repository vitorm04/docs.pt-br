---
title: Entrada passou do final do arquivo | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID62
dev_langs:
- VB
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: 9
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
ms.openlocfilehash: dfbb8e0e7069960140824df1153e6fcab040a0c7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="input-past-end-of-file"></a><span data-ttu-id="eb9d5-102">Entrada passou do final do arquivo</span><span class="sxs-lookup"><span data-stu-id="eb9d5-102">Input past end of file</span></span>
<span data-ttu-id="eb9d5-103">Qualquer um `Input` instrução está lendo de um arquivo que está vazio ou um em que todos os dados são usados ou você usou o `EOF` função com um arquivo aberto para acesso binário.</span><span class="sxs-lookup"><span data-stu-id="eb9d5-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eb9d5-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="eb9d5-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="eb9d5-105">Use o `EOF` funcionar imediatamente antes do `Input` instrução para detectar o final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="eb9d5-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2.  <span data-ttu-id="eb9d5-106">Se o arquivo é aberto para acesso binário, use `Seek` e `Loc`.</span><span class="sxs-lookup"><span data-stu-id="eb9d5-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9d5-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb9d5-107">See Also</span></span>  
 <span data-ttu-id="eb9d5-108"><xref:Microsoft.VisualBasic.FileSystem.Input%2A></xref:Microsoft.VisualBasic.FileSystem.Input%2A></span><span class="sxs-lookup"><span data-stu-id="eb9d5-108"><xref:Microsoft.VisualBasic.FileSystem.Input%2A></span></span>   
 <span data-ttu-id="eb9d5-109"><xref:Microsoft.VisualBasic.FileSystem.EOF%2A></xref:Microsoft.VisualBasic.FileSystem.EOF%2A></span><span class="sxs-lookup"><span data-stu-id="eb9d5-109"><xref:Microsoft.VisualBasic.FileSystem.EOF%2A></span></span>   
 <span data-ttu-id="eb9d5-110"><xref:Microsoft.VisualBasic.FileSystem.Seek%2A></xref:Microsoft.VisualBasic.FileSystem.Seek%2A></span><span class="sxs-lookup"><span data-stu-id="eb9d5-110"><xref:Microsoft.VisualBasic.FileSystem.Seek%2A></span></span>   
 <span data-ttu-id="eb9d5-111"><xref:Microsoft.VisualBasic.FileSystem.Loc%2A></xref:Microsoft.VisualBasic.FileSystem.Loc%2A></span><span class="sxs-lookup"><span data-stu-id="eb9d5-111"><xref:Microsoft.VisualBasic.FileSystem.Loc%2A></span></span>
