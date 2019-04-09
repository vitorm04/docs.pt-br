---
title: Método ICLRReferenceAssemblyEnum::Get
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31d26ed6249bad8a7e2fbaab01264c1b32e1ff55
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194468"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="7311f-102">Método ICLRReferenceAssemblyEnum::Get</span><span class="sxs-lookup"><span data-stu-id="7311f-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="7311f-103">Obtém a identidade do assembly no índice fornecido.</span><span class="sxs-lookup"><span data-stu-id="7311f-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7311f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7311f-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7311f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7311f-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="7311f-106">[in] O índice baseado em zero da identidade do assembly para retornar.</span><span class="sxs-lookup"><span data-stu-id="7311f-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="7311f-107">[out] Um buffer que contém os dados de identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="7311f-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="7311f-108">[no, out] O tamanho do `pwzBuffer` buffer.</span><span class="sxs-lookup"><span data-stu-id="7311f-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7311f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7311f-109">Return Value</span></span>  
  
|<span data-ttu-id="7311f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7311f-110">HRESULT</span></span>|<span data-ttu-id="7311f-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="7311f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7311f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7311f-112">S_OK</span></span>|`Get` <span data-ttu-id="7311f-113">retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="7311f-113">returned successfully.</span></span>|  
|<span data-ttu-id="7311f-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7311f-114">ERROR_INSUFFICIENT_BUFFER</span></span>|`pwzBuffer` <span data-ttu-id="7311f-115">é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="7311f-115">is too small.</span></span>|  
|<span data-ttu-id="7311f-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="7311f-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="7311f-117">A enumeração não contém mais itens.</span><span class="sxs-lookup"><span data-stu-id="7311f-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="7311f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7311f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7311f-119">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="7311f-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7311f-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7311f-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7311f-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="7311f-121">The call timed out.</span></span>|  
|<span data-ttu-id="7311f-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7311f-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7311f-123">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="7311f-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7311f-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7311f-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7311f-125">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="7311f-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7311f-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7311f-126">E_FAIL</span></span>|<span data-ttu-id="7311f-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="7311f-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7311f-128">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="7311f-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7311f-129">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7311f-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7311f-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="7311f-130">Remarks</span></span>  
 `Get` <span data-ttu-id="7311f-131">normalmente é chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="7311f-131">is typically called twice.</span></span> <span data-ttu-id="7311f-132">A primeira chamada fornece um valor nulo para `pwzBuffer`e define `pcchBufferSize` para o tamanho apropriado para `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7311f-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="7311f-133">A segunda chamada fornece um tamanho apropriado `pwzBuffer`e contém os dados de identidade do assembly canônico após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="7311f-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7311f-134">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7311f-134">Requirements</span></span>  
 <span data-ttu-id="7311f-135">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7311f-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7311f-136">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7311f-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7311f-137">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7311f-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7311f-138">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7311f-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7311f-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7311f-139">See also</span></span>

- [<span data-ttu-id="7311f-140">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="7311f-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="7311f-141">Interface ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="7311f-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
