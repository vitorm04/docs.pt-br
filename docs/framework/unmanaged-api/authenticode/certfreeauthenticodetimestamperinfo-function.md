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
ms.openlocfilehash: b8b6392e57e641d25d07580fcb6bf630f8d983be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="6c66a-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="6c66a-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="6c66a-103">Libera os recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="6c66a-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c66a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c66a-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c66a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c66a-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="6c66a-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="6c66a-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="6c66a-107">Consulte o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="6c66a-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c66a-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6c66a-108">Return Value</span></span>  
 <span data-ttu-id="6c66a-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="6c66a-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="6c66a-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="6c66a-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c66a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c66a-111">See Also</span></span>  
 [<span data-ttu-id="6c66a-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6c66a-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
