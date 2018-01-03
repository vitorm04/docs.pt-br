---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46c0646cfff79888db2b6b37184dd97da21e71e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="d1de0-102">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="d1de0-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="d1de0-103">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d1de0-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1de0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1de0-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d1de0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d1de0-105">Members</span></span>  
  
|<span data-ttu-id="d1de0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d1de0-106">Member</span></span>|<span data-ttu-id="d1de0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d1de0-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="d1de0-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="d1de0-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="d1de0-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="d1de0-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="d1de0-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="d1de0-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="d1de0-111">A hora do carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="d1de0-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="d1de0-112">Contexto da cadeia do carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="d1de0-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="d1de0-113">Consulte o [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="d1de0-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1de0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1de0-114">See Also</span></span>  
 [<span data-ttu-id="d1de0-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d1de0-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
