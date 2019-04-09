---
title: Método IHostControl::SetAppDomainManager
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 118e75cb28a4e474427f35f4516ec41850ebe99f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150859"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="60f44-102">Método IHostControl::SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="60f44-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="60f44-103">Notifica o host que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="60f44-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f44-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60f44-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f44-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60f44-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="60f44-106">[in] O identificador numérico do selecionado <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="60f44-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="60f44-107">[in] Um ponteiro para o <xref:System.AppDomainManager> objeto que o host implementa como `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="60f44-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60f44-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="60f44-108">Return Value</span></span>  
  
|<span data-ttu-id="60f44-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60f44-109">HRESULT</span></span>|<span data-ttu-id="60f44-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="60f44-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60f44-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="60f44-111">S_OK</span></span>|`SetAppDomainManager` <span data-ttu-id="60f44-112">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="60f44-112">returned successfully.</span></span>|  
|<span data-ttu-id="60f44-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60f44-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60f44-114">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="60f44-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60f44-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60f44-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60f44-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="60f44-116">The call timed out.</span></span>|  
|<span data-ttu-id="60f44-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60f44-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60f44-118">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="60f44-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60f44-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60f44-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60f44-120">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="60f44-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60f44-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60f44-121">E_FAIL</span></span>|<span data-ttu-id="60f44-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="60f44-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60f44-123">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="60f44-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60f44-124">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="60f44-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60f44-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="60f44-125">Remarks</span></span>  
 <span data-ttu-id="60f44-126">O <xref:System.AppDomainManager> fornece o host com um mecanismo para inicializar em código gerenciado e controlar a criação e as configurações de cada <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="60f44-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="60f44-127">O <xref:System.AppDomainManager> é carregado em cada <xref:System.AppDomain> quando que <xref:System.AppDomain> é criado.</span><span class="sxs-lookup"><span data-stu-id="60f44-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="60f44-128">Se optar por, o CLR notifica o host que o domínio do aplicativo foi criado, definindo o valor da `pUnkAppDomainManager` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="60f44-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="60f44-129">Em sua implementação do `SetAppDomainManager` método, o host pode definir o nome do assembly e o tipo para o Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60f44-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f44-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="60f44-130">Requirements</span></span>  
 <span data-ttu-id="60f44-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f44-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f44-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="60f44-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60f44-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="60f44-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="60f44-134">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="60f44-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60f44-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60f44-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="60f44-136">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="60f44-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
