---
title: Estrutura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 232c78db32aecd0ee1379d4d969fa0378db4159a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741361"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="5877d-102">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="5877d-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="5877d-103">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="5877d-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5877d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5877d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="5877d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5877d-105">Members</span></span>  
  
|<span data-ttu-id="5877d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5877d-106">Member</span></span>|<span data-ttu-id="5877d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5877d-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="5877d-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="5877d-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="5877d-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="5877d-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="5877d-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="5877d-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="5877d-111">O hash.</span><span class="sxs-lookup"><span data-stu-id="5877d-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="5877d-112">A descrição.</span><span class="sxs-lookup"><span data-stu-id="5877d-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="5877d-113">A URL da descrição.</span><span class="sxs-lookup"><span data-stu-id="5877d-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="5877d-114">O contexto da cadeia do signatário.</span><span class="sxs-lookup"><span data-stu-id="5877d-114">The chain context of the signer.</span></span> <span data-ttu-id="5877d-115">Consulte a [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) estrutura.</span><span class="sxs-lookup"><span data-stu-id="5877d-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5877d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5877d-116">See also</span></span>

- [<span data-ttu-id="5877d-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="5877d-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
