---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae7879e1f6598108d839287792ed441391764ae2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776650"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="d2ae6-102">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="d2ae6-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="d2ae6-103">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="d2ae6-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ae6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2ae6-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d2ae6-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d2ae6-105">Members</span></span>  
  
|<span data-ttu-id="d2ae6-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d2ae6-106">Member</span></span>|<span data-ttu-id="d2ae6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2ae6-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="d2ae6-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="d2ae6-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="d2ae6-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="d2ae6-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="d2ae6-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="d2ae6-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="d2ae6-111">A hora do carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="d2ae6-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="d2ae6-112">Contexto da cadeia do carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="d2ae6-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="d2ae6-113">Consulte a estrutura [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="d2ae6-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2ae6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2ae6-114">See also</span></span>

- [<span data-ttu-id="d2ae6-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d2ae6-115">Authenticode</span></span>](index.md)
