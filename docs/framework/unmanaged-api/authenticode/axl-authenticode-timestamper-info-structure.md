---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f4fff4f2c2b3dd04625f4cf50b8b19a0ef6f39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525075"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="32321-102">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="32321-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="32321-103">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="32321-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32321-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32321-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="32321-105">Membros</span><span class="sxs-lookup"><span data-stu-id="32321-105">Members</span></span>  
  
|<span data-ttu-id="32321-106">Membro</span><span class="sxs-lookup"><span data-stu-id="32321-106">Member</span></span>|<span data-ttu-id="32321-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="32321-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="32321-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="32321-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="32321-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="32321-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="32321-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="32321-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="32321-111">A hora do carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="32321-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="32321-112">Contexto da cadeia do carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="32321-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="32321-113">Consulte a [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) estrutura.</span><span class="sxs-lookup"><span data-stu-id="32321-113">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32321-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32321-114">See Also</span></span>  
 [<span data-ttu-id="32321-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="32321-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
