---
title: Função CertFreeAuthenticodeTimestamperInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082ed24eb65de12f337ab4a379b088da0f6eea5a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497373"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="3c140-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="3c140-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="3c140-103">Libera recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="3c140-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c140-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c140-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c140-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c140-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="3c140-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="3c140-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="3c140-107">Consulte a [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="3c140-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c140-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3c140-108">Return Value</span></span>  
 <span data-ttu-id="3c140-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="3c140-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="3c140-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="3c140-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c140-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c140-111">See also</span></span>
- [<span data-ttu-id="3c140-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3c140-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
