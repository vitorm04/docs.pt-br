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
ms.openlocfilehash: cbed2ece8b10c6385341c0af44a81dfa16b6f60c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497477"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="752c1-102">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="752c1-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="752c1-103">Libera recursos alocados para o [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="752c1-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="752c1-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="752c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="752c1-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="752c1-106">[in, out] Informações de signatário a serem liberadas.</span><span class="sxs-lookup"><span data-stu-id="752c1-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="752c1-107">Consulte a [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="752c1-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="752c1-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="752c1-108">Return Value</span></span>  
 <span data-ttu-id="752c1-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="752c1-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="752c1-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="752c1-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752c1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="752c1-111">See also</span></span>
- [<span data-ttu-id="752c1-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="752c1-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
