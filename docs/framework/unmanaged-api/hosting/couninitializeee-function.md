---
title: Função CoUninitializeEE
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef5faff6682ed6c043e81212f2cb27d4cfbd813d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601851"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="e8e02-102">Função CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="e8e02-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="e8e02-103">`CoUninitializeEE` é obsoleto e não fornece nenhuma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="e8e02-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e02-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8e02-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8e02-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8e02-105">Remarks</span></span>  
 <span data-ttu-id="e8e02-106">O mecanismo de execução do common language runtime não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="e8e02-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="e8e02-107">Para desligar a chamada de mecanismo de execução [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="e8e02-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e02-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8e02-108">See also</span></span>
- [<span data-ttu-id="e8e02-109">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="e8e02-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="e8e02-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="e8e02-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
