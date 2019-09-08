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
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776733"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="126e1-102">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="126e1-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="126e1-103">Libera recursos alocados para a estrutura [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="126e1-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="126e1-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="126e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="126e1-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="126e1-106">[in, out] Informações de signatário a serem liberadas.</span><span class="sxs-lookup"><span data-stu-id="126e1-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="126e1-107">Consulte a estrutura [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="126e1-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="126e1-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="126e1-108">Return Value</span></span>  
 <span data-ttu-id="126e1-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="126e1-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="126e1-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="126e1-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126e1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="126e1-111">See also</span></span>

- [<span data-ttu-id="126e1-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="126e1-112">Authenticode</span></span>](index.md)
