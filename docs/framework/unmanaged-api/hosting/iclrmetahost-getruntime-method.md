---
title: Método ICLRMetaHost::GetRuntime
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273891b0814d9383d9640c79f5df959f2b9398b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707890"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="c8e0e-102">Método ICLRMetaHost::GetRuntime</span><span class="sxs-lookup"><span data-stu-id="c8e0e-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="c8e0e-103">Obtém o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que corresponde a uma versão específica do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c8e0e-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="c8e0e-104">Esse método substitui o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função usada com o [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sinalizador.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e0e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8e0e-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8e0e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8e0e-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="c8e0e-107">[in] A versão de compilação do .NET Framework armazenada nos metadados, no formato "v*um*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="c8e0e-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="c8e0e-108">*Um*, *B*, e *X* são números decimais que correspondem da versão principal, a versão secundária e o número da compilação.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8e0e-109">Esse parâmetro deve corresponder ao nome de diretório para a versão do .NET Framework, como ele aparece sob C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="c8e0e-110">Os valores de exemplo são "v1.0.3705", "v1.1.4322", "v2.0.50727" e "v4.0. *X*", onde *X* depende do número de compilação instalado.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="c8e0e-111">O prefixo "v" é necessário.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="c8e0e-112">[in] O identificador para a interface desejada.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="c8e0e-113">Atualmente, o único valor válido para esse parâmetro é IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="c8e0e-114">[out] Um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que corresponde ao tempo de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8e0e-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c8e0e-115">Return Value</span></span>  
 <span data-ttu-id="c8e0e-116">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c8e0e-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8e0e-117">HRESULT</span></span>|<span data-ttu-id="c8e0e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8e0e-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8e0e-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8e0e-119">S_OK</span></span>|<span data-ttu-id="c8e0e-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="c8e0e-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="c8e0e-121">E_POINTER</span></span>|<span data-ttu-id="c8e0e-122">`pwzVersion` ou `ppRuntime` é nulo.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8e0e-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8e0e-123">Remarks</span></span>  
 <span data-ttu-id="c8e0e-124">Esse método consistentemente interage com interfaces herdadas, como o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface e herdado funções como preteridas `CorBindTo*` funções (consulte [preterido hospedando funções CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) na API de hospedagem do .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="c8e0e-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="c8e0e-125">Ou seja, tempos de execução que são carregados com a API herdada são visíveis para a nova API e tempos de execução que são carregados com a nova API são visíveis para a API herdada.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span> <span data-ttu-id="c8e0e-126">.</span><span class="sxs-lookup"><span data-stu-id="c8e0e-126">.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8e0e-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8e0e-127">Requirements</span></span>  
 <span data-ttu-id="c8e0e-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8e0e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8e0e-129">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c8e0e-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c8e0e-130">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c8e0e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8e0e-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8e0e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e0e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8e0e-132">See also</span></span>
- [<span data-ttu-id="c8e0e-133">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="c8e0e-133">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="c8e0e-134">Interfaces e coclasses de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="c8e0e-134">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="c8e0e-135">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="c8e0e-135">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="c8e0e-136">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="c8e0e-136">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="c8e0e-137">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c8e0e-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
