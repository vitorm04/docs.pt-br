---
title: Método ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream
helpviewer_keywords:
- GetBindingIdentityFromStream method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
topic_type:
- apiref
ms.openlocfilehash: abba19600616cad8ba3377ae2ebb23459449d2a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615976"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromstream-method"></a><span data-ttu-id="02cde-102">Método ICLRAssemblyIdentityManager::GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="02cde-102">ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method</span></span>
<span data-ttu-id="02cde-103">Obtém os dados de identidade do assembly canônico para o assembly no fluxo especificado.</span><span class="sxs-lookup"><span data-stu-id="02cde-103">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02cde-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02cde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02cde-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02cde-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="02cde-106">no O fluxo do assembly a ser avaliado.</span><span class="sxs-lookup"><span data-stu-id="02cde-106">[in] The assembly stream to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="02cde-107">no Fornecido para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="02cde-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="02cde-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT é o único valor para o qual a versão atual do Common Language Runtime (CLR) dá suporte.</span><span class="sxs-lookup"><span data-stu-id="02cde-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="02cde-109">fora Um buffer que contém os dados de identidade do assembly opaco.</span><span class="sxs-lookup"><span data-stu-id="02cde-109">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="02cde-110">[entrada, saída] O tamanho de `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="02cde-110">[in, out] The size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02cde-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="02cde-111">Return Value</span></span>  
  
|<span data-ttu-id="02cde-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02cde-112">HRESULT</span></span>|<span data-ttu-id="02cde-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="02cde-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02cde-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="02cde-114">S_OK</span></span>|<span data-ttu-id="02cde-115">O método foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="02cde-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="02cde-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="02cde-116">E_INVALIDARG</span></span>|<span data-ttu-id="02cde-117">O fornecido `pStream` é nulo.</span><span class="sxs-lookup"><span data-stu-id="02cde-117">The supplied `pStream` is null.</span></span>|  
|<span data-ttu-id="02cde-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="02cde-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="02cde-119">O tamanho de `pwzBuffer` é muito pequeno.</span><span class="sxs-lookup"><span data-stu-id="02cde-119">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="02cde-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="02cde-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="02cde-121">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="02cde-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="02cde-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="02cde-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="02cde-123">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="02cde-123">The call timed out.</span></span>|  
|<span data-ttu-id="02cde-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="02cde-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="02cde-125">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="02cde-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="02cde-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="02cde-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="02cde-127">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="02cde-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="02cde-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="02cde-128">E_FAIL</span></span>|<span data-ttu-id="02cde-129">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="02cde-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="02cde-130">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="02cde-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="02cde-131">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="02cde-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02cde-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="02cde-132">Requirements</span></span>  
 <span data-ttu-id="02cde-133">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02cde-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02cde-134">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="02cde-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02cde-135">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="02cde-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02cde-136">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02cde-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02cde-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="02cde-137">See also</span></span>

- [<span data-ttu-id="02cde-138">Interface ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="02cde-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="02cde-139">Interface ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="02cde-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
