---
title: "Método ICorRuntimeHost::Stop"
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
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f9e27bd5d05b10f8db24a1119e4ed3717ce044e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="2ae8b-102">Método ICorRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="2ae8b-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="2ae8b-103">Interrompe a execução de código em tempo de execução para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ae8b-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2ae8b-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2ae8b-105">Return Value</span></span>  
  
|<span data-ttu-id="2ae8b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ae8b-106">HRESULT</span></span>|<span data-ttu-id="2ae8b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ae8b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ae8b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ae8b-108">S_OK</span></span>|<span data-ttu-id="2ae8b-109">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-109">The operation was successful.</span></span>|  
|<span data-ttu-id="2ae8b-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2ae8b-110">S_FALSE</span></span>|<span data-ttu-id="2ae8b-111">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="2ae8b-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ae8b-112">E_FAIL</span></span>|<span data-ttu-id="2ae8b-113">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="2ae8b-114">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="2ae8b-115">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2ae8b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ae8b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ae8b-117">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ae8b-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ae8b-118">Remarks</span></span>  
 <span data-ttu-id="2ae8b-119">Geralmente é desnecessário chamar o `Stop` método, porque o código interrompe a execução quando o processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ae8b-120">Após uma chamada para `Stop`, o CLR não pode ser reinicializado no mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="2ae8b-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae8b-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ae8b-121">Requirements</span></span>  
 <span data-ttu-id="2ae8b-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ae8b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae8b-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ae8b-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ae8b-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2ae8b-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ae8b-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="2ae8b-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae8b-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ae8b-126">See Also</span></span>  
 [<span data-ttu-id="2ae8b-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="2ae8b-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
