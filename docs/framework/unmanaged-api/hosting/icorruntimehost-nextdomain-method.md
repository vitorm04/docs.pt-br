---
title: Método ICorRuntimeHost::NextDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 36eacedfb83c1248fc252091872bcfeecdbcd874
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139499"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="566ad-102">Método ICorRuntimeHost::NextDomain</span><span class="sxs-lookup"><span data-stu-id="566ad-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="566ad-103">Obtém um ponteiro de interface para o próximo domínio na enumeração.</span><span class="sxs-lookup"><span data-stu-id="566ad-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="566ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="566ad-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="566ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="566ad-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="566ad-106">no O enumerador que foi obtido por meio de uma chamada para [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="566ad-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="566ad-107">fora Um ponteiro de interface para o tipo de <xref:System._AppDomain?displayProperty=nameWithType> que representa o próximo domínio na enumeração, ou NULL, se não houver mais domínios.</span><span class="sxs-lookup"><span data-stu-id="566ad-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="566ad-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="566ad-108">Return Value</span></span>  
  
|<span data-ttu-id="566ad-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="566ad-109">HRESULT</span></span>|<span data-ttu-id="566ad-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="566ad-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="566ad-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="566ad-111">S_OK</span></span>|<span data-ttu-id="566ad-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="566ad-112">The operation was successful.</span></span>|  
|<span data-ttu-id="566ad-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="566ad-113">S_FALSE</span></span>|<span data-ttu-id="566ad-114">A operação não foi concluída ou não há mais domínios na enumeração.</span><span class="sxs-lookup"><span data-stu-id="566ad-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="566ad-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="566ad-115">E_FAIL</span></span>|<span data-ttu-id="566ad-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="566ad-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="566ad-117">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="566ad-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="566ad-118">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="566ad-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="566ad-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="566ad-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="566ad-120">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="566ad-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="566ad-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="566ad-121">Requirements</span></span>  
 <span data-ttu-id="566ad-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="566ad-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="566ad-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="566ad-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="566ad-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="566ad-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="566ad-125">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="566ad-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566ad-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="566ad-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="566ad-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="566ad-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
