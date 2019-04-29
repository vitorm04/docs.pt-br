---
title: Método ICorRuntimeHost::NextDomain
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c3ff0c91713a6bb7449791bae6a754c43659335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700157"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="e50fc-102">Método ICorRuntimeHost::NextDomain</span><span class="sxs-lookup"><span data-stu-id="e50fc-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="e50fc-103">Obtém um ponteiro de interface para o próximo domínio na enumeração.</span><span class="sxs-lookup"><span data-stu-id="e50fc-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e50fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e50fc-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e50fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e50fc-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e50fc-106">[in] O enumerador que foi obtido por meio de uma chamada para [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="e50fc-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="e50fc-107">[out] Um ponteiro de interface para o <xref:System._AppDomain?displayProperty=nameWithType> tipo que representa o próximo domínio na enumeração, ou null, se não existir nenhum domínio mais.</span><span class="sxs-lookup"><span data-stu-id="e50fc-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e50fc-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e50fc-108">Return Value</span></span>  
  
|<span data-ttu-id="e50fc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e50fc-109">HRESULT</span></span>|<span data-ttu-id="e50fc-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="e50fc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e50fc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e50fc-111">S_OK</span></span>|<span data-ttu-id="e50fc-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e50fc-112">The operation was successful.</span></span>|  
|<span data-ttu-id="e50fc-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e50fc-113">S_FALSE</span></span>|<span data-ttu-id="e50fc-114">Falha ao concluir a operação ou não há nenhum mais domínios na enumeração.</span><span class="sxs-lookup"><span data-stu-id="e50fc-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="e50fc-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e50fc-115">E_FAIL</span></span>|<span data-ttu-id="e50fc-116">Ocorreu uma falha catastrófica, desconhecida.</span><span class="sxs-lookup"><span data-stu-id="e50fc-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e50fc-117">Se um método retornar E_FAIL, o common language runtime (CLR) não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="e50fc-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e50fc-118">As chamadas subsequentes para todas as APIs de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e50fc-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e50fc-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e50fc-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e50fc-120">O CLR não tenha sido carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="e50fc-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e50fc-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e50fc-121">Requirements</span></span>  
 <span data-ttu-id="e50fc-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e50fc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e50fc-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e50fc-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e50fc-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e50fc-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e50fc-125">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e50fc-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e50fc-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e50fc-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e50fc-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="e50fc-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
