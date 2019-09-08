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
ms.openlocfilehash: a8ecada29528b065ddad0abc80a850ee0f347f6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786999"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="bb9ee-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="bb9ee-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="bb9ee-103">Libera recursos alocados para a estrutura [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="bb9ee-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb9ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb9ee-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb9ee-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb9ee-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="bb9ee-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="bb9ee-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="bb9ee-107">Consulte a estrutura [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="bb9ee-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb9ee-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bb9ee-108">Return Value</span></span>  
 <span data-ttu-id="bb9ee-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bb9ee-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="bb9ee-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="bb9ee-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb9ee-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb9ee-111">See also</span></span>

- [<span data-ttu-id="bb9ee-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bb9ee-112">Authenticode</span></span>](index.md)
