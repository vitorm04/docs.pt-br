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
ms.openlocfilehash: b1af01559e65bd80fc62cb2eba44bf21d4fa3113
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770901"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="ee15e-102">Método ICorRuntimeHost::Stop</span><span class="sxs-lookup"><span data-stu-id="ee15e-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="ee15e-103">Interrompe a execução de código no tempo de execução para o processo atual.</span><span class="sxs-lookup"><span data-stu-id="ee15e-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee15e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee15e-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ee15e-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ee15e-105">Return Value</span></span>  
  
|<span data-ttu-id="ee15e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee15e-106">HRESULT</span></span>|<span data-ttu-id="ee15e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee15e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee15e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee15e-108">S_OK</span></span>|<span data-ttu-id="ee15e-109">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ee15e-109">The operation was successful.</span></span>|  
|<span data-ttu-id="ee15e-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ee15e-110">S_FALSE</span></span>|<span data-ttu-id="ee15e-111">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="ee15e-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ee15e-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ee15e-112">E_FAIL</span></span>|<span data-ttu-id="ee15e-113">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ee15e-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ee15e-114">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="ee15e-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ee15e-115">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ee15e-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ee15e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ee15e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ee15e-117">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ee15e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee15e-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="ee15e-118">Remarks</span></span>  
 <span data-ttu-id="ee15e-119">Não é geralmente necessário chamar o `Stop` método, porque o código para executar quando o processo é encerrado.</span><span class="sxs-lookup"><span data-stu-id="ee15e-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee15e-120">Após uma chamada para `Stop`, o CLR não pode ser reinicializado no mesmo processo.</span><span class="sxs-lookup"><span data-stu-id="ee15e-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee15e-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee15e-121">Requirements</span></span>  
 <span data-ttu-id="ee15e-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee15e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee15e-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ee15e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee15e-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ee15e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee15e-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ee15e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee15e-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee15e-126">See also</span></span>

- [<span data-ttu-id="ee15e-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ee15e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
