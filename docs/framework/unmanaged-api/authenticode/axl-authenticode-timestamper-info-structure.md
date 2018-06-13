---
title: Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c89845008307e4cfb00d0f9b9a168a43ba5378c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402357"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="2d6e3-102">Estrutura AXL_AUTHENTICODE_TIMESTAMPER_INFO</span><span class="sxs-lookup"><span data-stu-id="2d6e3-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="2d6e3-103">Define as informações sobre o carimbo de data/hora do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d6e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d6e3-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2d6e3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2d6e3-105">Members</span></span>  
  
|<span data-ttu-id="2d6e3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2d6e3-106">Member</span></span>|<span data-ttu-id="2d6e3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d6e3-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="2d6e3-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="2d6e3-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="2d6e3-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="2d6e3-111">A hora do carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="2d6e3-112">Contexto da cadeia do carimbo de hora.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="2d6e3-113">Consulte o [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="2d6e3-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d6e3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d6e3-114">See Also</span></span>  
 [<span data-ttu-id="2d6e3-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2d6e3-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
