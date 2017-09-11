---
title: "Não é possível criar arquivo temporário necessário | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID322
dev_langs:
- VB
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: 6
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
ms.openlocfilehash: 4a6e92e3f4ce78dcd73800644a9aa5f7cac513ff
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="5b0c9-102">Não é possível criar arquivo temporário necessário</span><span class="sxs-lookup"><span data-stu-id="5b0c9-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="5b0c9-103">Ou a unidade está cheia que contém o diretório especificado pela variável de ambiente TEMP ou variável de ambiente TEMP especifica uma unidade inválida ou somente leitura ou diretório.</span><span class="sxs-lookup"><span data-stu-id="5b0c9-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5b0c9-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5b0c9-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="5b0c9-105">Exclua arquivos da unidade, se cheia.</span><span class="sxs-lookup"><span data-stu-id="5b0c9-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="5b0c9-106">Especifique uma unidade diferente na variável de ambiente TEMP.</span><span class="sxs-lookup"><span data-stu-id="5b0c9-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="5b0c9-107">Especifique uma unidade válida para a variável de ambiente TEMP.</span><span class="sxs-lookup"><span data-stu-id="5b0c9-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="5b0c9-108">Remova a restrição somente leitura da unidade especificada no momento ou do diretório.</span><span class="sxs-lookup"><span data-stu-id="5b0c9-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0c9-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b0c9-109">See Also</span></span>  
 [<span data-ttu-id="5b0c9-110">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="5b0c9-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
