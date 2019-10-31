---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 036397928703aea6199a59ae9c1e66153c30ec7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132498"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="e14a5-102">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="e14a5-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="e14a5-103">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="e14a5-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e14a5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e14a5-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e14a5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e14a5-105">Members</span></span>  
  
|<span data-ttu-id="e14a5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e14a5-106">Member</span></span>|<span data-ttu-id="e14a5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e14a5-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="e14a5-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="e14a5-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="e14a5-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="e14a5-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="e14a5-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="e14a5-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="e14a5-111">A hora do carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="e14a5-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="e14a5-112">Contexto da cadeia do carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="e14a5-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="e14a5-113">Consulte a estrutura [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="e14a5-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e14a5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e14a5-114">See also</span></span>

- [<span data-ttu-id="e14a5-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e14a5-115">Authenticode</span></span>](index.md)
