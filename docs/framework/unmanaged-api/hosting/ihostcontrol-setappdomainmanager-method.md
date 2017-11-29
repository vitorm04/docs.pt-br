---
title: "Método IHostControl::SetAppDomainManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl.SetAppDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97e853bc74babca5b5400953b63714a13419fcaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="a5b21-102">Método IHostControl::SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="a5b21-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="a5b21-103">Notifica o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="a5b21-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5b21-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5b21-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5b21-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a5b21-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="a5b21-106">[in] O identificador numérico do selecionado <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a5b21-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="a5b21-107">[in] Um ponteiro para o <xref:System.AppDomainManager> objeto que implementa o host como `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="a5b21-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5b21-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a5b21-108">Return Value</span></span>  
  
|<span data-ttu-id="a5b21-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5b21-109">HRESULT</span></span>|<span data-ttu-id="a5b21-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5b21-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a5b21-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5b21-111">S_OK</span></span>|<span data-ttu-id="a5b21-112">`SetAppDomainManager`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="a5b21-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="a5b21-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a5b21-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a5b21-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="a5b21-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a5b21-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a5b21-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a5b21-116">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="a5b21-116">The call timed out.</span></span>|  
|<span data-ttu-id="a5b21-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a5b21-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a5b21-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="a5b21-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a5b21-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a5b21-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a5b21-120">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="a5b21-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a5b21-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a5b21-121">E_FAIL</span></span>|<span data-ttu-id="a5b21-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="a5b21-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a5b21-123">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="a5b21-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a5b21-124">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a5b21-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b21-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5b21-125">Remarks</span></span>  
 <span data-ttu-id="a5b21-126">O <xref:System.AppDomainManager> fornece um mecanismo para inicializar em código gerenciado e controlar a criação e as configurações de cada host <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a5b21-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="a5b21-127">O <xref:System.AppDomainManager> é carregado em cada <xref:System.AppDomain> quando que <xref:System.AppDomain> é criado.</span><span class="sxs-lookup"><span data-stu-id="a5b21-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="a5b21-128">Se ele escolhe, o CLR notifica o host que o domínio de aplicativo foi criado, definindo o valor da `pUnkAppDomainManager` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a5b21-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="a5b21-129">Em sua implementação do `SetAppDomainManager` método, o host pode definir o nome do assembly e o tipo para o Gerenciador de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5b21-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b21-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5b21-130">Requirements</span></span>  
 <span data-ttu-id="a5b21-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5b21-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b21-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a5b21-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5b21-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a5b21-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5b21-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b21-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b21-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5b21-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="a5b21-136">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="a5b21-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
