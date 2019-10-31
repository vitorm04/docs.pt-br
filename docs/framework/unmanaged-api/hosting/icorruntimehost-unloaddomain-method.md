---
title: Método ICorRuntimeHost::UnloadDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: dfdcb9b8aedeb3ccbbd27864e79ce43338942922
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133352"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="94404-102">Método ICorRuntimeHost::UnloadDomain</span><span class="sxs-lookup"><span data-stu-id="94404-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="94404-103">Descarrega o domínio de aplicativo especificado do processo atual.</span><span class="sxs-lookup"><span data-stu-id="94404-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94404-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94404-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94404-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94404-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="94404-106">no Um ponteiro do tipo <xref:System._AppDomain?displayProperty=nameWithType> que representa o domínio a ser descarregado.</span><span class="sxs-lookup"><span data-stu-id="94404-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94404-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="94404-107">Return Value</span></span>  
  
|<span data-ttu-id="94404-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94404-108">HRESULT</span></span>|<span data-ttu-id="94404-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="94404-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94404-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="94404-110">S_OK</span></span>|<span data-ttu-id="94404-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="94404-111">The operation was successful.</span></span>|  
|<span data-ttu-id="94404-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="94404-112">S_FALSE</span></span>|<span data-ttu-id="94404-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="94404-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="94404-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94404-114">E_FAIL</span></span>|<span data-ttu-id="94404-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="94404-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="94404-116">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="94404-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="94404-117">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="94404-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="94404-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94404-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94404-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="94404-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94404-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="94404-120">Requirements</span></span>  
 <span data-ttu-id="94404-121">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94404-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94404-122">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="94404-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94404-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="94404-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94404-124">**Versão do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="94404-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94404-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94404-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="94404-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="94404-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
