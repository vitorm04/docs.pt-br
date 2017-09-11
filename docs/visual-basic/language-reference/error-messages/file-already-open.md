---
title: "Arquivo já aberto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID55
dev_langs:
- VB
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 7
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
ms.openlocfilehash: 4d9198e9963785e6231d48abb59c57d0647f2aeb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="file-already-open"></a><span data-ttu-id="cb820-102">Arquivo já aberto</span><span class="sxs-lookup"><span data-stu-id="cb820-102">File already open</span></span>
<span data-ttu-id="cb820-103">Às vezes, um arquivo deve ser fechado antes de outro `FileOpen` ou outra operação pode ocorrer.</span><span class="sxs-lookup"><span data-stu-id="cb820-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="cb820-104">Entre as causas possíveis desse erro são:</span><span class="sxs-lookup"><span data-stu-id="cb820-104">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="cb820-105">Um modo de saída sequencial `FileOpen` operação foi executada para um arquivo que já está aberto</span><span class="sxs-lookup"><span data-stu-id="cb820-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
-   <span data-ttu-id="cb820-106">Uma instrução refere-se a um arquivo aberto.</span><span class="sxs-lookup"><span data-stu-id="cb820-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb820-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="cb820-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="cb820-108">Feche o arquivo antes de executar a instrução.</span><span class="sxs-lookup"><span data-stu-id="cb820-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb820-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb820-109">See Also</span></span>  
 <span data-ttu-id="cb820-110"><xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></span><span class="sxs-lookup"><span data-stu-id="cb820-110"><xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A></span></span>
