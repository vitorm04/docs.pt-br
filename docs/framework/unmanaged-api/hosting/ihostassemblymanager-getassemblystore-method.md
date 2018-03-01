---
title: "Método IHostAssemblyManager::GetAssemblyStore"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 347947622601475147663b8838bef5f36a1f7e32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="b688a-102">Método IHostAssemblyManager::GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="b688a-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="b688a-103">Obtém um ponteiro de interface para um [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.</span><span class="sxs-lookup"><span data-stu-id="b688a-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b688a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b688a-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b688a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b688a-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="b688a-106">[out] Um ponteiro de função para um `IHostAssemblyStore` instância ou nulo, se o host não implementa `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="b688a-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b688a-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b688a-107">Return Value</span></span>  
  
|<span data-ttu-id="b688a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b688a-108">HRESULT</span></span>|<span data-ttu-id="b688a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b688a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b688a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b688a-110">S_OK</span></span>|<span data-ttu-id="b688a-111">`GetAssemblyStore`retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="b688a-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="b688a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b688a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b688a-113">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b688a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b688a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b688a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b688a-115">A chamada foi atingido.</span><span class="sxs-lookup"><span data-stu-id="b688a-115">The call timed out.</span></span>|  
|<span data-ttu-id="b688a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b688a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b688a-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b688a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b688a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b688a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b688a-119">Um evento foi cancelado durante um thread bloqueado ou fibra estava aguardando nele.</span><span class="sxs-lookup"><span data-stu-id="b688a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b688a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b688a-120">E_FAIL</span></span>|<span data-ttu-id="b688a-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b688a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b688a-122">Quando um método retornará E_FAIL, o CLR não será mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="b688a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b688a-123">As chamadas subsequentes para hospedagem métodos retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b688a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b688a-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="b688a-124">E_NOINTERFACE</span></span>|<span data-ttu-id="b688a-125">O host não fornece uma implementação de `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="b688a-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b688a-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b688a-126">Remarks</span></span>  
 <span data-ttu-id="b688a-127">`IHostAssemblyStore`fornece métodos que permitem que um host associar a assemblies e módulos independentemente do CLR.</span><span class="sxs-lookup"><span data-stu-id="b688a-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="b688a-128">Hosts normalmente fornecem repositórios de assembly para permitir que os assemblies sejam carregados a partir de formatos diferentes do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="b688a-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b688a-129">Se o host não implementa `IHostAssemblyStore`, `GetAssemblyStore` deve retornar um valor HRESULT de E_NOINTERFACE e deve definir `ppAssemblyStore` como null.</span><span class="sxs-lookup"><span data-stu-id="b688a-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b688a-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b688a-130">Requirements</span></span>  
 <span data-ttu-id="b688a-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b688a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b688a-132">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b688a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b688a-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b688a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b688a-134">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b688a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b688a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b688a-135">See Also</span></span>  
 [<span data-ttu-id="b688a-136">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="b688a-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="b688a-137">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="b688a-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
