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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6c93566d0909f1dbef46862760d47ede478d51a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434532"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="817b6-102">Método ICLRHostProtectionManager::SetProtectedCategories</span><span class="sxs-lookup"><span data-stu-id="817b6-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="817b6-103">Especifica quais categorias de tipos gerenciados e os membros devem ser bloqueadas em execução no código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="817b6-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="817b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="817b6-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="817b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="817b6-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="817b6-106">[in] Uma combinação de [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) valores, que indica quais categorias de tipos gerenciados e os membros devem ser bloqueadas em execução no código parcialmente confiável.</span><span class="sxs-lookup"><span data-stu-id="817b6-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="817b6-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="817b6-107">Return Value</span></span>  
  
|<span data-ttu-id="817b6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="817b6-108">HRESULT</span></span>|<span data-ttu-id="817b6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="817b6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="817b6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="817b6-110">S_OK</span></span>|<span data-ttu-id="817b6-111">`SetProtectedCategories` retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="817b6-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="817b6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="817b6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="817b6-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="817b6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="817b6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="817b6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="817b6-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="817b6-115">The call timed out.</span></span>|  
|<span data-ttu-id="817b6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="817b6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="817b6-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="817b6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="817b6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="817b6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="817b6-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="817b6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="817b6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="817b6-120">E_FAIL</span></span>|<span data-ttu-id="817b6-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="817b6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="817b6-122">Depois que um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="817b6-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="817b6-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="817b6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="817b6-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="817b6-124">Remarks</span></span>  
 <span data-ttu-id="817b6-125">Cada `EApiCategories` valor refere-se a uma lista de tipos gerenciados e de membros.</span><span class="sxs-lookup"><span data-stu-id="817b6-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="817b6-126">O `EApiCategories` enumeração e o `SetProtectedCategories` método estão diretamente relacionadas ao gerenciado <xref:System.Security.Permissions.HostProtectionAttribute> classe, que é usado para marcar tipos gerenciados e membros que expõem os recursos correspondentes às categorias descritas pelo `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="817b6-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="817b6-127">Para obter mais informações, consulte <xref:System.Security.Permissions.HostProtectionAttribute> e <xref:System.Security.Permissions.HostProtectionResource> enumeração, que corresponde diretamente às `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="817b6-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="817b6-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="817b6-128">Requirements</span></span>  
 <span data-ttu-id="817b6-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="817b6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817b6-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="817b6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="817b6-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="817b6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="817b6-132">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="817b6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="817b6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="817b6-133">See Also</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [<span data-ttu-id="817b6-134">Enumeração EApiCategories</span><span class="sxs-lookup"><span data-stu-id="817b6-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="817b6-135">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="817b6-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="817b6-136">Interface ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="817b6-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
