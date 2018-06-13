---
title: Função CertFreeAuthenticodeSignerInfo
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f15dc49d14e781f69d0f9da8f314eb71d8c034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401610"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="8d760-102">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="8d760-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="8d760-103">Libera os recursos alocados para o [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="8d760-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d760-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d760-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d760-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d760-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="8d760-106">[in, out] Informações de signatário a serem liberadas.</span><span class="sxs-lookup"><span data-stu-id="8d760-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="8d760-107">Consulte o [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="8d760-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d760-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8d760-108">Return Value</span></span>  
 <span data-ttu-id="8d760-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8d760-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="8d760-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="8d760-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d760-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d760-111">See Also</span></span>  
 [<span data-ttu-id="8d760-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8d760-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
