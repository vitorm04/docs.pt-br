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
ms.openlocfilehash: 355e6c7b1cd77936d5ccfa5ccff7312c8e35ac63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941616"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="301ff-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="301ff-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="301ff-103">Libera recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="301ff-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301ff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="301ff-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="301ff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="301ff-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="301ff-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="301ff-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="301ff-107">Consulte a [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="301ff-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="301ff-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="301ff-108">Return Value</span></span>  
 <span data-ttu-id="301ff-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="301ff-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="301ff-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="301ff-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301ff-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="301ff-111">See also</span></span>

- [<span data-ttu-id="301ff-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="301ff-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
