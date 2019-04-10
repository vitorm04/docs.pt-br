---
title: Método ICorRuntimeHost::CloseEnum
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f150fe80302cd03e872ca8bdf5d172caae1ce599
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230766"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="ca97e-102">Método ICorRuntimeHost::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="ca97e-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="ca97e-103">Redefine o enumerador de um domínio voltar ao início da lista de domínios.</span><span class="sxs-lookup"><span data-stu-id="ca97e-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca97e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca97e-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca97e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca97e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ca97e-106">[in] O enumerador para redefinir.</span><span class="sxs-lookup"><span data-stu-id="ca97e-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca97e-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ca97e-107">Return Value</span></span>  
  
|<span data-ttu-id="ca97e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca97e-108">HRESULT</span></span>|<span data-ttu-id="ca97e-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ca97e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca97e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca97e-110">S_OK</span></span>|<span data-ttu-id="ca97e-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ca97e-111">The operation was successful.</span></span>|  
|<span data-ttu-id="ca97e-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ca97e-112">S_FALSE</span></span>|<span data-ttu-id="ca97e-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="ca97e-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ca97e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ca97e-114">E_FAIL</span></span>|<span data-ttu-id="ca97e-115">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ca97e-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ca97e-116">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="ca97e-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ca97e-117">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ca97e-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ca97e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ca97e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ca97e-119">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="ca97e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca97e-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca97e-120">Requirements</span></span>  
 <span data-ttu-id="ca97e-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca97e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca97e-122">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca97e-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca97e-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ca97e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca97e-124">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ca97e-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca97e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca97e-125">See also</span></span>

- [<span data-ttu-id="ca97e-126">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="ca97e-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="ca97e-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ca97e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
