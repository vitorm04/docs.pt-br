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
ms.openlocfilehash: 42f5685a9a976be7a3a73badf286f77216e43106
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741237"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="4ac0d-102">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="4ac0d-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="4ac0d-103">Libera recursos alocados para o [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ac0d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ac0d-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ac0d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ac0d-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="4ac0d-106">[in, out] Informações de signatário a serem liberadas.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="4ac0d-107">Consulte a [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ac0d-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ac0d-108">Return Value</span></span>  
 <span data-ttu-id="4ac0d-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="4ac0d-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="4ac0d-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ac0d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ac0d-111">See also</span></span>

- [<span data-ttu-id="4ac0d-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="4ac0d-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
