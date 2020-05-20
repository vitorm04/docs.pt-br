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
ms.openlocfilehash: ea66c142afc097d1003df4e7f5f5b960a91e2ab0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703392"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="8eeb2-102">Método ICLRProbingAssemblyEnum::Get</span><span class="sxs-lookup"><span data-stu-id="8eeb2-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="8eeb2-103">Obtém a identidade do assembly no índice especificado.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eeb2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8eeb2-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eeb2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8eeb2-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="8eeb2-106">no O índice de base zero da identidade do assembly a ser retornado.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="8eeb2-107">fora Um buffer que contém os dados de identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="8eeb2-108">[entrada, saída] O tamanho do `pwzBuffer` buffer.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8eeb2-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8eeb2-109">Return Value</span></span>  
  
|<span data-ttu-id="8eeb2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8eeb2-110">HRESULT</span></span>|<span data-ttu-id="8eeb2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8eeb2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8eeb2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8eeb2-112">S_OK</span></span>|<span data-ttu-id="8eeb2-113">`Get`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="8eeb2-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8eeb2-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8eeb2-115">`pwzBuffer` é pequeno demais.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="8eeb2-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="8eeb2-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="8eeb2-117">A enumeração não contém mais itens.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="8eeb2-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8eeb2-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8eeb2-119">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8eeb2-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8eeb2-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8eeb2-121">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-121">The call timed out.</span></span>|  
|<span data-ttu-id="8eeb2-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8eeb2-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8eeb2-123">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8eeb2-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8eeb2-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8eeb2-125">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8eeb2-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8eeb2-126">E_FAIL</span></span>|<span data-ttu-id="8eeb2-127">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8eeb2-128">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8eeb2-129">As chamadas subsequentes para quaisquer métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eeb2-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="8eeb2-130">Remarks</span></span>  
 <span data-ttu-id="8eeb2-131">A identidade no índice 0 é a identidade específica para a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="8eeb2-132">A identidade no índice 1 é o assembly de arquitetura neutra para MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="8eeb2-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="8eeb2-133">A identidade no índice 2 não contém informações de arquitetura.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="8eeb2-134">`Get`normalmente é chamado duas vezes.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-134">`Get` is typically called twice.</span></span> <span data-ttu-id="8eeb2-135">A primeira chamada fornece um valor nulo para `pwzBuffer` e define `pcchBufferSize` o tamanho apropriado para `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="8eeb2-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="8eeb2-136">A segunda chamada fornece um tamanho adequado `pwzBuffer` e contém os dados de identidade do assembly canônico após a conclusão.</span><span class="sxs-lookup"><span data-stu-id="8eeb2-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eeb2-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8eeb2-137">Requirements</span></span>  
 <span data-ttu-id="8eeb2-138">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eeb2-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eeb2-139">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8eeb2-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8eeb2-140">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8eeb2-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8eeb2-141">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eeb2-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eeb2-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="8eeb2-142">See also</span></span>

- [<span data-ttu-id="8eeb2-143">Interface ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="8eeb2-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="8eeb2-144">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="8eeb2-144">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
