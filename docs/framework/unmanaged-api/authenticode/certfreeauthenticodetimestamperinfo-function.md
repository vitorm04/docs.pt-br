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
ms.openlocfilehash: 27c16cb5d85ddffc1646bee893c5644682812025
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560575"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="90516-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="90516-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="90516-103">Libera recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="90516-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90516-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90516-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90516-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90516-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="90516-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="90516-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="90516-107">Consulte a [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="90516-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90516-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="90516-108">Return Value</span></span>  
 <span data-ttu-id="90516-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="90516-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="90516-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="90516-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90516-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90516-111">See also</span></span>
- [<span data-ttu-id="90516-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="90516-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
