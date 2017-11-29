---
title: "Função CoUninitializeEE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeEE
helpviewer_keywords: CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d64064c29d2a03578305f71a37e759907814727e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="couninitializeee-function"></a><span data-ttu-id="1b057-102">Função CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="1b057-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="1b057-103">`CoUninitializeEE`está obsoleto e não fornece nenhuma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="1b057-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b057-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b057-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1b057-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b057-105">Remarks</span></span>  
 <span data-ttu-id="1b057-106">O mecanismo de execução do common language runtime não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="1b057-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="1b057-107">Para desligar a chamada de mecanismo de execução [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="1b057-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b057-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b057-108">See Also</span></span>  
 [<span data-ttu-id="1b057-109">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="1b057-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="1b057-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="1b057-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
