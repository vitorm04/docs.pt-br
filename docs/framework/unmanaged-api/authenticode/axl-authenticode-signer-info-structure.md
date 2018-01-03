---
title: Estrutura AXL_AUTHENTICODE_SIGNER_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a952dd8ae31cadad250111d9bbcd4c42466547e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="9bbac-102">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="9bbac-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="9bbac-103">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="9bbac-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bbac-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="9bbac-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9bbac-105">Members</span></span>  
  
|<span data-ttu-id="9bbac-106">Membro</span><span class="sxs-lookup"><span data-stu-id="9bbac-106">Member</span></span>|<span data-ttu-id="9bbac-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bbac-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="9bbac-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="9bbac-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="9bbac-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="9bbac-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="9bbac-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="9bbac-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="9bbac-111">O hash.</span><span class="sxs-lookup"><span data-stu-id="9bbac-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="9bbac-112">A descrição.</span><span class="sxs-lookup"><span data-stu-id="9bbac-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="9bbac-113">A URL da descrição.</span><span class="sxs-lookup"><span data-stu-id="9bbac-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="9bbac-114">O contexto da cadeia do signatário.</span><span class="sxs-lookup"><span data-stu-id="9bbac-114">The chain context of the signer.</span></span> <span data-ttu-id="9bbac-115">Consulte o [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) estrutura.</span><span class="sxs-lookup"><span data-stu-id="9bbac-115">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bbac-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bbac-116">See Also</span></span>  
 [<span data-ttu-id="9bbac-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="9bbac-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
