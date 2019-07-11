---
title: Método ICorRuntimeHost::Start
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ac86fdc0852c701b66986b6a304695fbdc8e755
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780392"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="23efb-102">Método ICorRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="23efb-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="23efb-103">Inicia o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="23efb-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23efb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23efb-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="23efb-105">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="23efb-105">Return Value</span></span>  
  
|<span data-ttu-id="23efb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23efb-106">HRESULT</span></span>|<span data-ttu-id="23efb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="23efb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23efb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="23efb-108">S_OK</span></span>|<span data-ttu-id="23efb-109">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="23efb-109">The operation was successful.</span></span>|  
|<span data-ttu-id="23efb-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="23efb-110">S_FALSE</span></span>|<span data-ttu-id="23efb-111">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="23efb-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="23efb-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23efb-112">E_FAIL</span></span>|<span data-ttu-id="23efb-113">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="23efb-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="23efb-114">Se um método retornar E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="23efb-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="23efb-115">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="23efb-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="23efb-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23efb-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23efb-117">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="23efb-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23efb-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="23efb-118">Remarks</span></span>  
 <span data-ttu-id="23efb-119">Normalmente não é necessário chamar o `Start` método, pois o CLR é iniciado automaticamente após a primeira solicitação para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="23efb-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23efb-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23efb-120">Requirements</span></span>  
 <span data-ttu-id="23efb-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23efb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23efb-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="23efb-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23efb-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="23efb-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23efb-124">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="23efb-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23efb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23efb-125">See also</span></span>

- [<span data-ttu-id="23efb-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23efb-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
