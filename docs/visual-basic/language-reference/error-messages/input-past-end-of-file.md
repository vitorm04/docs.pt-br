---
title: Entrada passou do final do arquivo
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 29a9b5ce3c3f8e6a02b52beda1338fd699143570
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491331"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="f6213-102">Entrada passou do final do arquivo</span><span class="sxs-lookup"><span data-stu-id="f6213-102">Input past end of file</span></span>
<span data-ttu-id="f6213-103">Qualquer um `Input` instrução está lendo de um arquivo que está vazio ou um em que todos os dados é usado, ou você tiver usado o `EOF` função com um arquivo aberto para acesso binário.</span><span class="sxs-lookup"><span data-stu-id="f6213-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6213-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f6213-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="f6213-105">Use o `EOF` funcionar imediatamente antes do `Input` instrução para detectar o final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f6213-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2.  <span data-ttu-id="f6213-106">Se o arquivo é aberto para acesso binário, use `Seek` e `Loc`.</span><span class="sxs-lookup"><span data-stu-id="f6213-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6213-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6213-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
