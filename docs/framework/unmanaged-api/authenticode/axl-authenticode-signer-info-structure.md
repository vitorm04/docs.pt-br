---
title: Estrutura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 024837870aade6b0beb76fe758a571b15fd14d59
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107660"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="c4bdd-102">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="c4bdd-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="c4bdd-103">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4bdd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4bdd-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c4bdd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="c4bdd-105">Members</span></span>  
  
|<span data-ttu-id="c4bdd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="c4bdd-106">Member</span></span>|<span data-ttu-id="c4bdd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4bdd-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="c4bdd-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="c4bdd-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="c4bdd-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="c4bdd-111">O hash.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="c4bdd-112">A descrição.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="c4bdd-113">A URL da descrição.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="c4bdd-114">O contexto da cadeia do signatário.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-114">The chain context of the signer.</span></span> <span data-ttu-id="c4bdd-115">Consulte a [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) estrutura.</span><span class="sxs-lookup"><span data-stu-id="c4bdd-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4bdd-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4bdd-116">See also</span></span>

- [<span data-ttu-id="c4bdd-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c4bdd-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
