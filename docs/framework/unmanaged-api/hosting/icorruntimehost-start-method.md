---
title: "Método ICorRuntimeHost::Start"
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
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d79046db904de68e5b24b2f96206bb1de2de470
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="9b488-102">Método ICorRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="9b488-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="9b488-103">Inicia o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9b488-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b488-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b488-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9b488-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9b488-105">Return Value</span></span>  
  
|<span data-ttu-id="9b488-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b488-106">HRESULT</span></span>|<span data-ttu-id="9b488-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b488-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b488-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b488-108">S_OK</span></span>|<span data-ttu-id="9b488-109">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9b488-109">The operation was successful.</span></span>|  
|<span data-ttu-id="9b488-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9b488-110">S_FALSE</span></span>|<span data-ttu-id="9b488-111">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9b488-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9b488-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b488-112">E_FAIL</span></span>|<span data-ttu-id="9b488-113">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="9b488-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9b488-114">Se um método retornará E_FAIL, o CLR não será mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="9b488-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="9b488-115">As chamadas subsequentes para hospedagem de APIs retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9b488-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9b488-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b488-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b488-117">O CLR não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="9b488-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b488-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b488-118">Remarks</span></span>  
 <span data-ttu-id="9b488-119">Normalmente não é necessário chamar o `Start` método, porque o CLR será iniciado automaticamente após a primeira solicitação para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9b488-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b488-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b488-120">Requirements</span></span>  
 <span data-ttu-id="9b488-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b488-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b488-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b488-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b488-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9b488-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b488-124">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9b488-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b488-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b488-125">See Also</span></span>  
 [<span data-ttu-id="9b488-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9b488-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
