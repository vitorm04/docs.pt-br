---
title: "Função CoUninitializeCor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeCor
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeCor
helpviewer_keywords: CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 57740ed8f20891b240bca5e9e19591484022b8ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="couninitializecor-function"></a><span data-ttu-id="43f11-102">Função CoUninitializeCor</span><span class="sxs-lookup"><span data-stu-id="43f11-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="43f11-103">`CoUninitializeCor` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="43f11-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f11-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43f11-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="43f11-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="43f11-105">Remarks</span></span>  
 <span data-ttu-id="43f11-106">O common language runtime não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="43f11-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="43f11-107">Para remover completamente o tempo de execução de um processo em execução, você deve desligar esse processo.</span><span class="sxs-lookup"><span data-stu-id="43f11-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f11-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43f11-108">See Also</span></span>  
 [<span data-ttu-id="43f11-109">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="43f11-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
