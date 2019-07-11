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
ms.openlocfilehash: 680d9c959c57620ff38f8e785c670b451e5805b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741223"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="b48ec-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="b48ec-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="b48ec-103">Libera recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="b48ec-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b48ec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b48ec-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b48ec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b48ec-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="b48ec-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="b48ec-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="b48ec-107">Consulte a [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="b48ec-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b48ec-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b48ec-108">Return Value</span></span>  
 <span data-ttu-id="b48ec-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b48ec-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="b48ec-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="b48ec-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48ec-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b48ec-111">See also</span></span>

- [<span data-ttu-id="b48ec-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b48ec-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
