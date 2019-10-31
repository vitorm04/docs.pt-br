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
ms.openlocfilehash: 4f0806e0273b111e3398fb8f2884231b96cf1116
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099767"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="90e6a-102">Função CertFreeAuthenticodeTimestamperInfo</span><span class="sxs-lookup"><span data-stu-id="90e6a-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="90e6a-103">Libera recursos alocados para a estrutura [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="90e6a-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90e6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90e6a-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90e6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90e6a-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="90e6a-106">[in, out] As informações do carimbo de data/hora que será liberado.</span><span class="sxs-lookup"><span data-stu-id="90e6a-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="90e6a-107">Consulte a estrutura [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="90e6a-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90e6a-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="90e6a-108">Return Value</span></span>  
 <span data-ttu-id="90e6a-109">`S_OK` se a função for bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="90e6a-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="90e6a-110">Caso contrário, retornará um código de erro.</span><span class="sxs-lookup"><span data-stu-id="90e6a-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e6a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90e6a-111">See also</span></span>

- [<span data-ttu-id="90e6a-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="90e6a-112">Authenticode</span></span>](index.md)
