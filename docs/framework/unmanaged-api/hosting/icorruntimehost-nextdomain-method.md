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
ms.openlocfilehash: 079164d15141983711e976e0209cc22c818d9cd9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760414"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="382f6-102">Método ICorRuntimeHost::NextDomain</span><span class="sxs-lookup"><span data-stu-id="382f6-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="382f6-103">Obtém um ponteiro de interface para o próximo domínio na enumeração.</span><span class="sxs-lookup"><span data-stu-id="382f6-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="382f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="382f6-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="382f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="382f6-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="382f6-106">no O enumerador que foi obtido por meio de uma chamada para [EnumDomains](icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="382f6-106">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="382f6-107">fora Um ponteiro de interface para o <xref:System._AppDomain?displayProperty=nameWithType> tipo que representa o próximo domínio na enumeração, ou NULL, se não houver mais domínios.</span><span class="sxs-lookup"><span data-stu-id="382f6-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="382f6-108">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="382f6-108">Return Value</span></span>  
  
|<span data-ttu-id="382f6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="382f6-109">HRESULT</span></span>|<span data-ttu-id="382f6-110">Description</span><span class="sxs-lookup"><span data-stu-id="382f6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="382f6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="382f6-111">S_OK</span></span>|<span data-ttu-id="382f6-112">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="382f6-112">The operation was successful.</span></span>|  
|<span data-ttu-id="382f6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="382f6-113">S_FALSE</span></span>|<span data-ttu-id="382f6-114">A operação não foi concluída ou não há mais domínios na enumeração.</span><span class="sxs-lookup"><span data-stu-id="382f6-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="382f6-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="382f6-115">E_FAIL</span></span>|<span data-ttu-id="382f6-116">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="382f6-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="382f6-117">Se um método retornar E_FAIL, o Common Language Runtime (CLR) não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="382f6-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="382f6-118">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="382f6-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="382f6-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="382f6-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="382f6-120">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="382f6-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="382f6-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="382f6-121">Requirements</span></span>  
 <span data-ttu-id="382f6-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="382f6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="382f6-123">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="382f6-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="382f6-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="382f6-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="382f6-125">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="382f6-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382f6-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="382f6-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="382f6-127">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="382f6-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
