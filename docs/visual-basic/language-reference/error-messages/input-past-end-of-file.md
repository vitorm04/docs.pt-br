---
title: Entrada passou do final do arquivo
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: abd5f5c6e5df262d1deadd74f0a146a8d436ceb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="9cc0a-102">Entrada passou do final do arquivo</span><span class="sxs-lookup"><span data-stu-id="9cc0a-102">Input past end of file</span></span>
<span data-ttu-id="9cc0a-103">Qualquer um `Input` instrução está lendo de um arquivo que está vazio ou um no qual todos os dados é usado, ou você usou o `EOF` função com um arquivo aberto para acesso binário.</span><span class="sxs-lookup"><span data-stu-id="9cc0a-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9cc0a-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9cc0a-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="9cc0a-105">Use o `EOF` função imediatamente antes do `Input` instrução para detectar o final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="9cc0a-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2.  <span data-ttu-id="9cc0a-106">Se o arquivo é aberto para acesso binário, use `Seek` e `Loc`.</span><span class="sxs-lookup"><span data-stu-id="9cc0a-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc0a-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cc0a-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
