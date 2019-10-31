---
title: Função CoUninitializeEE
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: 3531cfc0815c3f8a9479e35b2df60b2825801b39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136859"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="6b31d-102">Função CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="6b31d-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="6b31d-103">`CoUninitializeEE` é obsoleto e não fornece nenhuma funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="6b31d-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b31d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b31d-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b31d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b31d-105">Remarks</span></span>  
 <span data-ttu-id="6b31d-106">O mecanismo de execução de Common Language Runtime não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="6b31d-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="6b31d-107">Para desligar a chamada do mecanismo de execução [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="6b31d-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b31d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b31d-108">See also</span></span>

- [<span data-ttu-id="6b31d-109">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="6b31d-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="6b31d-110">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="6b31d-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
