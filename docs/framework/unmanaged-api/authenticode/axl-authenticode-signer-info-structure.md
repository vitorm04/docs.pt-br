---
title: Estrutura AXL_AUTHENTICODE_SIGNER_INFO
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b9f54c7c57d122ac1214b9f31cc4e1d1cddd71c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039180"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="f6c40-102">Estrutura AXL_AUTHENTICODE_SIGNER_INFO</span><span class="sxs-lookup"><span data-stu-id="f6c40-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="f6c40-103">Define as informações sobre o signatário do Authenticode.</span><span class="sxs-lookup"><span data-stu-id="f6c40-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6c40-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f6c40-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f6c40-105">Members</span></span>  
  
|<span data-ttu-id="f6c40-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f6c40-106">Member</span></span>|<span data-ttu-id="f6c40-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6c40-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="f6c40-108">O tamanho desta estrutura.</span><span class="sxs-lookup"><span data-stu-id="f6c40-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="f6c40-109">O código de erro.</span><span class="sxs-lookup"><span data-stu-id="f6c40-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="f6c40-110">O algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="f6c40-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="f6c40-111">O hash.</span><span class="sxs-lookup"><span data-stu-id="f6c40-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="f6c40-112">A descrição.</span><span class="sxs-lookup"><span data-stu-id="f6c40-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="f6c40-113">A URL da descrição.</span><span class="sxs-lookup"><span data-stu-id="f6c40-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="f6c40-114">O contexto da cadeia do signatário.</span><span class="sxs-lookup"><span data-stu-id="f6c40-114">The chain context of the signer.</span></span> <span data-ttu-id="f6c40-115">Consulte a [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) estrutura.</span><span class="sxs-lookup"><span data-stu-id="f6c40-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6c40-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6c40-116">See Also</span></span>  
 [<span data-ttu-id="f6c40-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f6c40-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
