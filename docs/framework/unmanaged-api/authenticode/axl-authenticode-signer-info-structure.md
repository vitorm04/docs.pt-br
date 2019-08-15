---
title: Estrutura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c69be0de98e2996176e7360bae0bb0736c1a797
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038435"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="a5fb7-102">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="a5fb7-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="a5fb7-103">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5fb7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5fb7-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a5fb7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a5fb7-105">Members</span></span>  
  
|<span data-ttu-id="a5fb7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a5fb7-106">Member</span></span>|<span data-ttu-id="a5fb7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5fb7-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="a5fb7-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="a5fb7-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="a5fb7-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="a5fb7-111">O hash.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="a5fb7-112">A descrição.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="a5fb7-113">A URL da descrição.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="a5fb7-114">O contexto da cadeia do signatário.</span><span class="sxs-lookup"><span data-stu-id="a5fb7-114">The chain context of the signer.</span></span> <span data-ttu-id="a5fb7-115">Consulte a estrutura [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) .</span><span class="sxs-lookup"><span data-stu-id="a5fb7-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5fb7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5fb7-116">See also</span></span>

- [<span data-ttu-id="a5fb7-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a5fb7-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
