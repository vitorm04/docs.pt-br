---
title: Método ICorRuntimeHost::Stop
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ef92fbe5ba99d93eaf06aacc7efd943136e9785
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543192"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="8e6d3-102">Método ICorRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="8e6d3-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="8e6d3-103">Interrompe a execução de código no tempo de execução para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e6d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e6d3-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8e6d3-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8e6d3-105">Return Value</span></span>  
  
|<span data-ttu-id="8e6d3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e6d3-106">HRESULT</span></span>|<span data-ttu-id="8e6d3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e6d3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e6d3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e6d3-108">S_OK</span></span>|<span data-ttu-id="8e6d3-109">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-109">The operation was successful.</span></span>|  
|<span data-ttu-id="8e6d3-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8e6d3-110">S_FALSE</span></span>|<span data-ttu-id="8e6d3-111">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8e6d3-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8e6d3-112">E_FAIL</span></span>|<span data-ttu-id="8e6d3-113">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8e6d3-114">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8e6d3-115">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8e6d3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8e6d3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8e6d3-117">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e6d3-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="8e6d3-118">Remarks</span></span>  
 <span data-ttu-id="8e6d3-119">Não é geralmente necessário chamar o `Stop` método, porque o código para executar quando o processo é encerrado.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e6d3-120">Após uma chamada para `Stop`, o CLR não pode ser reinicializado no mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="8e6d3-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e6d3-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e6d3-121">Requirements</span></span>  
 <span data-ttu-id="8e6d3-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e6d3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e6d3-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8e6d3-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8e6d3-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8e6d3-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e6d3-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8e6d3-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6d3-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e6d3-126">See also</span></span>
- [<span data-ttu-id="8e6d3-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="8e6d3-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
