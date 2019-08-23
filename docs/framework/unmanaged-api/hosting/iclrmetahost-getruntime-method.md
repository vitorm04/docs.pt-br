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
ms.openlocfilehash: f4b796942df153bf2c6ab703d748449331c9a0b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939853"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="87e62-102">Método ICLRMetaHost::GetRuntime</span><span class="sxs-lookup"><span data-stu-id="87e62-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="87e62-103">Obtém a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) que corresponde a uma versão específica do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="87e62-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="87e62-104">Esse método substitui a função [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) usada com o sinalizador [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="87e62-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e62-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87e62-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e62-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87e62-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="87e62-107">no A versão de compilação .NET Framework armazenada nos metadados, no formato "v*A*. *B* [. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="87e62-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="87e62-108">*A*, *B*e *X* são números decimais que correspondem à versão principal, à versão secundária e ao número da compilação.</span><span class="sxs-lookup"><span data-stu-id="87e62-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87e62-109">Esse parâmetro deve corresponder ao nome do diretório para a versão .NET Framework, pois ele aparece em C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="87e62-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="87e62-110">Os valores de exemplo são "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" e "v 4.0. *X*", em que *x* depende do número de Build instalado.</span><span class="sxs-lookup"><span data-stu-id="87e62-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="87e62-111">O prefixo "v" é necessário.</span><span class="sxs-lookup"><span data-stu-id="87e62-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="87e62-112">no O identificador para a interface desejada.</span><span class="sxs-lookup"><span data-stu-id="87e62-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="87e62-113">Atualmente, o único valor válido para esse parâmetro é IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="87e62-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="87e62-114">fora Um ponteiro para a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) que corresponde ao tempo de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="87e62-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87e62-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="87e62-115">Return Value</span></span>  
 <span data-ttu-id="87e62-116">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="87e62-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="87e62-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87e62-117">HRESULT</span></span>|<span data-ttu-id="87e62-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="87e62-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87e62-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="87e62-119">S_OK</span></span>|<span data-ttu-id="87e62-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="87e62-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="87e62-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="87e62-121">E_POINTER</span></span>|<span data-ttu-id="87e62-122">`pwzVersion` ou `ppRuntime` é nulo.</span><span class="sxs-lookup"><span data-stu-id="87e62-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e62-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="87e62-123">Remarks</span></span>  
 <span data-ttu-id="87e62-124">Esse método interage consistentemente com interfaces herdadas, como a interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) e funções herdadas, como as `CorBindTo*` funções preteridas (consulte [funções de Hospedagem de CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) preteridas na hospedagem .NET Framework 2,0 API).</span><span class="sxs-lookup"><span data-stu-id="87e62-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="87e62-125">Ou seja, os tempos de execução que são carregados com a API herdada são visíveis para a nova API, e os tempos de execução que são carregados com a nova API são visíveis para a API herdada.</span><span class="sxs-lookup"><span data-stu-id="87e62-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e62-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87e62-126">Requirements</span></span>  
 <span data-ttu-id="87e62-127">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e62-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e62-128">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="87e62-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="87e62-129">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87e62-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87e62-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e62-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e62-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87e62-131">See also</span></span>

- [<span data-ttu-id="87e62-132">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="87e62-132">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="87e62-133">Interfaces e coclasses de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="87e62-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="87e62-134">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="87e62-134">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="87e62-135">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="87e62-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="87e62-136">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="87e62-136">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
