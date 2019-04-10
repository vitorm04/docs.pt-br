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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220390"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="f1af3-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="f1af3-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="f1af3-103">Libera recursos alocados para o [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="f1af3-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1af3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1af3-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1af3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1af3-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="f1af3-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="f1af3-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="f1af3-107">Consulte a [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="f1af3-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1af3-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f1af3-108">Return Value</span></span>  
 `S_OK` <span data-ttu-id="f1af3-109">Se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f1af3-109">if the function succeeds.</span></span> <span data-ttu-id="f1af3-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="f1af3-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1af3-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1af3-111">See also</span></span>

- [<span data-ttu-id="f1af3-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f1af3-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
