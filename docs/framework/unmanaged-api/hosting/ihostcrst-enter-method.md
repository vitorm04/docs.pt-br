---
title: Método IHostCrst::Enter
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: 79afaac4dce1c4baa9802d81af90c425f5de7a08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804914"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="e8274-102">Método IHostCrst::Enter</span><span class="sxs-lookup"><span data-stu-id="e8274-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="e8274-103">Insere a seção crítica que é representada pela instância de [IHostCrst](ihostcrst-interface.md) atual.</span><span class="sxs-lookup"><span data-stu-id="e8274-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8274-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8274-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8274-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8274-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="e8274-106">no Um dos valores de [WAIT_OPTION](wait-option-enumeration.md) , que indica a ação que o host deve executar se a operação for bloqueada.</span><span class="sxs-lookup"><span data-stu-id="e8274-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8274-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="e8274-107">Return Value</span></span>  
  
|<span data-ttu-id="e8274-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8274-108">HRESULT</span></span>|<span data-ttu-id="e8274-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e8274-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8274-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8274-110">S_OK</span></span>|<span data-ttu-id="e8274-111">`Enter`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="e8274-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="e8274-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e8274-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e8274-113">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e8274-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e8274-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e8274-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e8274-115">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="e8274-115">The call timed out.</span></span>|  
|<span data-ttu-id="e8274-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e8274-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e8274-117">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="e8274-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e8274-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e8274-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e8274-119">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="e8274-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e8274-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e8274-120">E_FAIL</span></span>|<span data-ttu-id="e8274-121">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e8274-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e8274-122">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e8274-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e8274-123">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e8274-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8274-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8274-124">Remarks</span></span>  
 <span data-ttu-id="e8274-125">`Enter`espelha a função do Win32 `EnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="e8274-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8274-126">Esse método não retorna até que a seção crítica seja inserida.</span><span class="sxs-lookup"><span data-stu-id="e8274-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8274-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8274-127">Requirements</span></span>  
 <span data-ttu-id="e8274-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8274-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8274-129">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e8274-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e8274-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e8274-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8274-131">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8274-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8274-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8274-132">See also</span></span>

- [<span data-ttu-id="e8274-133">Interface ICLRSyncManager</span><span class="sxs-lookup"><span data-stu-id="e8274-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e8274-134">Interface IHostCrst</span><span class="sxs-lookup"><span data-stu-id="e8274-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="e8274-135">Interface IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="e8274-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
