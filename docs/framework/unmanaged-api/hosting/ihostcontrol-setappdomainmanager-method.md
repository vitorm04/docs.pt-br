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
ms.openlocfilehash: de264135450190fd028eb8cf12017d94cc65ffac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134716"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="53af5-102">Método IHostControl::SetAppDomainManager</span><span class="sxs-lookup"><span data-stu-id="53af5-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="53af5-103">Notifica o host de que um domínio de aplicativo foi criado.</span><span class="sxs-lookup"><span data-stu-id="53af5-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53af5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53af5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53af5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53af5-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="53af5-106">no O identificador numérico do <xref:System.AppDomain>selecionado.</span><span class="sxs-lookup"><span data-stu-id="53af5-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="53af5-107">no Um ponteiro para o objeto de <xref:System.AppDomainManager> que o host implementa como `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="53af5-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53af5-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="53af5-108">Return Value</span></span>  
  
|<span data-ttu-id="53af5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53af5-109">HRESULT</span></span>|<span data-ttu-id="53af5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="53af5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53af5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="53af5-111">S_OK</span></span>|<span data-ttu-id="53af5-112">`SetAppDomainManager` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="53af5-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="53af5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53af5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53af5-114">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="53af5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53af5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53af5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53af5-116">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="53af5-116">The call timed out.</span></span>|  
|<span data-ttu-id="53af5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53af5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53af5-118">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="53af5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53af5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53af5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53af5-120">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="53af5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53af5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53af5-121">E_FAIL</span></span>|<span data-ttu-id="53af5-122">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="53af5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53af5-123">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="53af5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53af5-124">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53af5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53af5-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="53af5-125">Remarks</span></span>  
 <span data-ttu-id="53af5-126">O <xref:System.AppDomainManager> fornece ao host um mecanismo para inicializar o código gerenciado e controlar a criação e as configurações de cada <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="53af5-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="53af5-127">O <xref:System.AppDomainManager> é carregado em cada <xref:System.AppDomain> quando esse <xref:System.AppDomain> é criado.</span><span class="sxs-lookup"><span data-stu-id="53af5-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="53af5-128">Se escolher, o CLR notifica o host de que o domínio do aplicativo foi criado definindo o valor do parâmetro `pUnkAppDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="53af5-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="53af5-129">Em sua implementação do método `SetAppDomainManager`, o host pode definir o nome do assembly e o tipo para o Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53af5-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53af5-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53af5-130">Requirements</span></span>  
 <span data-ttu-id="53af5-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53af5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53af5-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="53af5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53af5-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53af5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53af5-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53af5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53af5-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53af5-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="53af5-136">Interface IHostControl</span><span class="sxs-lookup"><span data-stu-id="53af5-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
