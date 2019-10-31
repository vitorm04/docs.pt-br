---
title: Método IHostAssemblyManager::GetAssemblyStore
ms.date: 03/30/2017
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
ms.openlocfilehash: 91c9a92d83312efcfd90a15aa0a60cccb6b44d7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134733"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="8d2fd-102">Método IHostAssemblyManager::GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="8d2fd-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="8d2fd-103">Obtém um ponteiro de interface para um [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d2fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d2fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d2fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d2fd-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="8d2fd-106">fora Um ponteiro de função para uma instância `IHostAssemblyStore`, ou NULL, se o host não implementar `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d2fd-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8d2fd-107">Return Value</span></span>  
  
|<span data-ttu-id="8d2fd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d2fd-108">HRESULT</span></span>|<span data-ttu-id="8d2fd-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d2fd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d2fd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d2fd-110">S_OK</span></span>|<span data-ttu-id="8d2fd-111">`GetAssemblyStore` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="8d2fd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d2fd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d2fd-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d2fd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d2fd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d2fd-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-115">The call timed out.</span></span>|  
|<span data-ttu-id="8d2fd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d2fd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d2fd-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d2fd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d2fd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d2fd-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d2fd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d2fd-120">E_FAIL</span></span>|<span data-ttu-id="8d2fd-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d2fd-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d2fd-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8d2fd-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="8d2fd-124">E_NOINTERFACE</span></span>|<span data-ttu-id="8d2fd-125">O host não fornece uma implementação de `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d2fd-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d2fd-126">Remarks</span></span>  
 <span data-ttu-id="8d2fd-127">`IHostAssemblyStore` fornece métodos que permitem que um host se associe a assemblies e módulos independentemente do CLR.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="8d2fd-128">Normalmente, os hosts fornecem armazenamentos de assembly para permitir que os assemblies sejam carregados a partir de formatos diferentes do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d2fd-129">Se o host não implementar `IHostAssemblyStore`, `GetAssemblyStore` deverá retornar um valor HRESULT de E_NOINTERFACE e deverá definir `ppAssemblyStore` como NULL.</span><span class="sxs-lookup"><span data-stu-id="8d2fd-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d2fd-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d2fd-130">Requirements</span></span>  
 <span data-ttu-id="8d2fd-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d2fd-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d2fd-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8d2fd-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d2fd-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8d2fd-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d2fd-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d2fd-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2fd-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d2fd-135">See also</span></span>

- [<span data-ttu-id="8d2fd-136">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="8d2fd-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="8d2fd-137">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="8d2fd-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
