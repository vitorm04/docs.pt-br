---
title: Método ICLRProbingAssemblyEnum::Get
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 268462db51435b87194aafc374d5d8e8ec1df165
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638640"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="8d4c9-102">Método ICLRProbingAssemblyEnum::Get</span><span class="sxs-lookup"><span data-stu-id="8d4c9-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="8d4c9-103">Obtém a identidade do assembly no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d4c9-104">Syntax</span></span>  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d4c9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d4c9-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="8d4c9-106">[in] O índice baseado em zero da identidade do assembly para retornar.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="8d4c9-107">[out] Um buffer que contém os dados de identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="8d4c9-108">[no, out] O tamanho do `pwzBuffer` buffer.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d4c9-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8d4c9-109">Return Value</span></span>  
  
|<span data-ttu-id="8d4c9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d4c9-110">HRESULT</span></span>|<span data-ttu-id="8d4c9-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d4c9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8d4c9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8d4c9-112">S_OK</span></span>|<span data-ttu-id="8d4c9-113">`Get` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="8d4c9-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8d4c9-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8d4c9-115">`pwzBuffer` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="8d4c9-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="8d4c9-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="8d4c9-117">A enumeração não contém mais itens.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="8d4c9-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8d4c9-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8d4c9-119">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8d4c9-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8d4c9-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8d4c9-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-121">The call timed out.</span></span>|  
|<span data-ttu-id="8d4c9-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8d4c9-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8d4c9-123">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8d4c9-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8d4c9-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8d4c9-125">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8d4c9-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8d4c9-126">E_FAIL</span></span>|<span data-ttu-id="8d4c9-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8d4c9-128">Se um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8d4c9-129">As chamadas subsequentes para todos os métodos hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d4c9-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d4c9-130">Remarks</span></span>  
 <span data-ttu-id="8d4c9-131">A identidade no índice 0 é a identidade específica da arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="8d4c9-132">A identidade no índice 1 é o assembly de arquitetura neutra para Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="8d4c9-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="8d4c9-133">A identidade no índice 2 não contém nenhuma informação de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="8d4c9-134">`Get` normalmente é chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-134">`Get` is typically called twice.</span></span> <span data-ttu-id="8d4c9-135">A primeira chamada fornece um valor nulo para `pwzBuffer`e define `pcchBufferSize` para o tamanho apropriado para `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="8d4c9-136">A segunda chamada fornece um tamanho apropriado `pwzBuffer`e contém os dados de identidade do assembly canônico após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d4c9-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d4c9-137">Requirements</span></span>  
 <span data-ttu-id="8d4c9-138">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d4c9-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d4c9-139">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8d4c9-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d4c9-140">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="8d4c9-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d4c9-141">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d4c9-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4c9-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d4c9-142">See also</span></span>

- [<span data-ttu-id="8d4c9-143">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="8d4c9-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="8d4c9-144">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="8d4c9-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
