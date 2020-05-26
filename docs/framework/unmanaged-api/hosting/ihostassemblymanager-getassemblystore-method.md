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
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805078"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="b4bbf-102">Método IHostAssemblyManager::GetAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="b4bbf-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="b4bbf-103">Obtém um ponteiro de interface para um [IHostAssemblyStore](ihostassemblystore-interface.md) que representa a lista de assemblies carregados pelo host.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-103">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4bbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4bbf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4bbf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b4bbf-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="b4bbf-106">fora Um ponteiro de função para uma `IHostAssemblyStore` instância, ou NULL, se o host não implementar `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="b4bbf-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4bbf-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="b4bbf-107">Return Value</span></span>  
  
|<span data-ttu-id="b4bbf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4bbf-108">HRESULT</span></span>|<span data-ttu-id="b4bbf-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4bbf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4bbf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4bbf-110">S_OK</span></span>|<span data-ttu-id="b4bbf-111">`GetAssemblyStore`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="b4bbf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4bbf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4bbf-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b4bbf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b4bbf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b4bbf-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-115">The call timed out.</span></span>|  
|<span data-ttu-id="b4bbf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b4bbf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b4bbf-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b4bbf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b4bbf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b4bbf-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b4bbf-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4bbf-120">E_FAIL</span></span>|<span data-ttu-id="b4bbf-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b4bbf-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b4bbf-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b4bbf-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="b4bbf-124">E_NOINTERFACE</span></span>|<span data-ttu-id="b4bbf-125">O host não fornece uma implementação de `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="b4bbf-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4bbf-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4bbf-126">Remarks</span></span>  
 <span data-ttu-id="b4bbf-127">`IHostAssemblyStore`fornece métodos que permitem que um host se associe a assemblies e módulos independentemente do CLR.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="b4bbf-128">Normalmente, os hosts fornecem armazenamentos de assembly para permitir que os assemblies sejam carregados a partir de formatos diferentes do sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4bbf-129">Se o host não implementar `IHostAssemblyStore` , `GetAssemblyStore` deverá retornar um valor HRESULT de E_NOINTERFACE e deverá definir `ppAssemblyStore` como NULL.</span><span class="sxs-lookup"><span data-stu-id="b4bbf-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4bbf-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4bbf-130">Requirements</span></span>  
 <span data-ttu-id="b4bbf-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4bbf-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4bbf-132">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b4bbf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4bbf-133">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b4bbf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4bbf-134">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4bbf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4bbf-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="b4bbf-135">See also</span></span>

- [<span data-ttu-id="b4bbf-136">Interface IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="b4bbf-136">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="b4bbf-137">Interface IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="b4bbf-137">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
