---
title: "Função CertFreeAuthenticodeTimestamperInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeTimestamperInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 353bba880cfa8a5ecf9ed826fbb529e31f790a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="852e6-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="852e6-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="852e6-103">Libera os recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="852e6-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="852e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="852e6-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="852e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="852e6-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="852e6-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="852e6-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="852e6-107">Consulte o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="852e6-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="852e6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="852e6-108">Return Value</span></span>  
 <span data-ttu-id="852e6-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="852e6-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="852e6-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="852e6-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852e6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="852e6-111">See Also</span></span>  
 [<span data-ttu-id="852e6-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="852e6-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
