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
ms.openlocfilehash: a5a86df3ac1f50ca624490ad80a6fed903433436
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762364"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="e863d-102">Método ICorRuntimeHost::CloseEnum</span><span class="sxs-lookup"><span data-stu-id="e863d-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="e863d-103">Redefine um enumerador de domínio de volta para o início da lista de domínios.</span><span class="sxs-lookup"><span data-stu-id="e863d-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e863d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e863d-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e863d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e863d-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e863d-106">no O enumerador a ser redefinido.</span><span class="sxs-lookup"><span data-stu-id="e863d-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e863d-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="e863d-107">Return Value</span></span>  
  
|<span data-ttu-id="e863d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e863d-108">HRESULT</span></span>|<span data-ttu-id="e863d-109">Description</span><span class="sxs-lookup"><span data-stu-id="e863d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e863d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e863d-110">S_OK</span></span>|<span data-ttu-id="e863d-111">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e863d-111">The operation was successful.</span></span>|  
|<span data-ttu-id="e863d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e863d-112">S_FALSE</span></span>|<span data-ttu-id="e863d-113">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="e863d-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e863d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e863d-114">E_FAIL</span></span>|<span data-ttu-id="e863d-115">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e863d-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e863d-116">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="e863d-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e863d-117">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e863d-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e863d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e863d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e863d-119">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e863d-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e863d-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e863d-120">Requirements</span></span>  
 <span data-ttu-id="e863d-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e863d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e863d-122">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e863d-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e863d-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e863d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e863d-124">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e863d-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e863d-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="e863d-125">See also</span></span>

- [<span data-ttu-id="e863d-126">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="e863d-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="e863d-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e863d-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
