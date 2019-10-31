---
title: Método ICLRHostProtectionManager::SetProtectedCategories
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: e3f2429462b4454e87690d98ad9fb446574add91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141042"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="b0e7e-102">Método ICLRHostProtectionManager::SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="b0e7e-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="b0e7e-103">Especifica quais categorias de tipos gerenciados e membros devem ser impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0e7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0e7e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0e7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0e7e-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="b0e7e-106">no Uma combinação de valores [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) , indicando quais categorias de tipos gerenciados e membros devem ser impedidos de serem executados em código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0e7e-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b0e7e-107">Return Value</span></span>  
  
|<span data-ttu-id="b0e7e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0e7e-108">HRESULT</span></span>|<span data-ttu-id="b0e7e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0e7e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0e7e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0e7e-110">S_OK</span></span>|<span data-ttu-id="b0e7e-111">`SetProtectedCategories` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="b0e7e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b0e7e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b0e7e-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b0e7e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b0e7e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b0e7e-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-115">The call timed out.</span></span>|  
|<span data-ttu-id="b0e7e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b0e7e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b0e7e-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b0e7e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b0e7e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b0e7e-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b0e7e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b0e7e-120">E_FAIL</span></span>|<span data-ttu-id="b0e7e-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b0e7e-122">Depois que um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b0e7e-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0e7e-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="b0e7e-124">Remarks</span></span>  
 <span data-ttu-id="b0e7e-125">Cada `EApiCategories` valor refere-se a uma lista de tipos e membros gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="b0e7e-126">A enumeração `EApiCategories` e o método `SetProtectedCategories` estão diretamente relacionados à classe <xref:System.Security.Permissions.HostProtectionAttribute> gerenciada, que é usada para marcar tipos gerenciados e membros que expõem recursos correspondentes às categorias descritas por `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="b0e7e-127">Para obter mais informações, consulte <xref:System.Security.Permissions.HostProtectionAttribute> e a enumeração <xref:System.Security.Permissions.HostProtectionResource>, que corresponde diretamente a `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="b0e7e-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0e7e-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b0e7e-128">Requirements</span></span>  
 <span data-ttu-id="b0e7e-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e7e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e7e-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b0e7e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0e7e-131">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b0e7e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0e7e-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e7e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e7e-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0e7e-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="b0e7e-134">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="b0e7e-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="b0e7e-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="b0e7e-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b0e7e-136">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="b0e7e-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
