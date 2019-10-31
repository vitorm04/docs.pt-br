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
ms.openlocfilehash: a233e0b8d17b9ee61b1991086f794c9fb20f89e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099830"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="035de-102">Função CertFreeAuthenticodeSignerInfo</span><span class="sxs-lookup"><span data-stu-id="035de-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="035de-103">Libera recursos alocados para a estrutura [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="035de-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="035de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="035de-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="035de-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="035de-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="035de-106">[in, out] Informações de signatário a serem liberadas.</span><span class="sxs-lookup"><span data-stu-id="035de-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="035de-107">Consulte a estrutura [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="035de-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="035de-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="035de-108">Return Value</span></span>  
 <span data-ttu-id="035de-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="035de-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="035de-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="035de-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035de-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="035de-111">See also</span></span>

- [<span data-ttu-id="035de-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="035de-112">Authenticode</span></span>](index.md)
