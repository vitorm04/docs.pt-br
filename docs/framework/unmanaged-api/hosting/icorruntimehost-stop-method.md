---
title: "Método ICorRuntimeHost::Stop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f6bf66065293107efae7f401a584b7342f29125
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="e82c7-102">Método ICorRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="e82c7-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="e82c7-103">Interrompe a execução de código em tempo de execução para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="e82c7-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e82c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e82c7-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e82c7-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e82c7-105">Return Value</span></span>  
  
|<span data-ttu-id="e82c7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e82c7-106">HRESULT</span></span>|<span data-ttu-id="e82c7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e82c7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e82c7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e82c7-108">S_OK</span></span>|<span data-ttu-id="e82c7-109">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e82c7-109">The operation was successful.</span></span>|  
|<span data-ttu-id="e82c7-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e82c7-110">S_FALSE</span></span>|<span data-ttu-id="e82c7-111">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="e82c7-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e82c7-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e82c7-112">E_FAIL</span></span>|<span data-ttu-id="e82c7-113">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e82c7-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e82c7-114">Se um método retornará E_FAIL, o common language runtime (CLR) não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e82c7-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e82c7-115">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e82c7-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e82c7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e82c7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e82c7-117">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e82c7-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e82c7-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="e82c7-118">Remarks</span></span>  
 <span data-ttu-id="e82c7-119">Geralmente é desnecessário chamar o `Stop` método, porque o código interrompe a execução quando o processo foi encerrado.</span><span class="sxs-lookup"><span data-stu-id="e82c7-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e82c7-120">Após uma chamada para `Stop`, o CLR não pode ser reinicializado no mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="e82c7-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e82c7-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e82c7-121">Requirements</span></span>  
 <span data-ttu-id="e82c7-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e82c7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e82c7-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e82c7-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e82c7-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e82c7-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e82c7-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e82c7-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82c7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e82c7-126">See Also</span></span>  
 [<span data-ttu-id="e82c7-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e82c7-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
