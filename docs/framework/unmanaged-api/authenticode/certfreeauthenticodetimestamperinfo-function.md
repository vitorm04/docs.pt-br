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
ms.openlocfilehash: 9c37a9af6a1532d03fa04ca151605cef7ab5244e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401762"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="0a3de-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="0a3de-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="0a3de-103">Libera os recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="0a3de-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a3de-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a3de-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0a3de-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="0a3de-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="0a3de-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="0a3de-107">Consulte o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="0a3de-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a3de-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0a3de-108">Return Value</span></span>  
 <span data-ttu-id="0a3de-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0a3de-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="0a3de-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="0a3de-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3de-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a3de-111">See Also</span></span>  
 [<span data-ttu-id="0a3de-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0a3de-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
