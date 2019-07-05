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
ms.openlocfilehash: 004122e9bb52dfe2e51ca00cd5362b2b7a06f30e
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569567"
---
# <a name="iclrmetahostgetruntime-method"></a><span data-ttu-id="90eb2-102">Método ICLRMetaHost::GetRuntime</span><span class="sxs-lookup"><span data-stu-id="90eb2-102">ICLRMetaHost::GetRuntime Method</span></span>
<span data-ttu-id="90eb2-103">Obtém o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que corresponde a uma versão específica do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="90eb2-103">Gets the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to a particular version of the common language runtime (CLR).</span></span> <span data-ttu-id="90eb2-104">Esse método substitui o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função usada com o [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sinalizador.</span><span class="sxs-lookup"><span data-stu-id="90eb2-104">This method supersedes the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90eb2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90eb2-105">Syntax</span></span>  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90eb2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90eb2-106">Parameters</span></span>  
 `pwzVersion`  
 <span data-ttu-id="90eb2-107">[in] A versão de compilação do .NET Framework armazenada nos metadados, no formato "v*um*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="90eb2-107">[in] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="90eb2-108">*Um*, *B*, e *X* são números decimais que correspondem da versão principal, a versão secundária e o número da compilação.</span><span class="sxs-lookup"><span data-stu-id="90eb2-108">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90eb2-109">Esse parâmetro deve corresponder ao nome de diretório para a versão do .NET Framework, como ele aparece sob C:\Windows\Microsoft.NET\Framework ou C:\Windows\Microsoft.NET\Framework64.</span><span class="sxs-lookup"><span data-stu-id="90eb2-109">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework or C:\Windows\Microsoft.NET\Framework64.</span></span>  
  
 <span data-ttu-id="90eb2-110">Os valores de exemplo são "v1.0.3705", "v1.1.4322", "v2.0.50727" e "v4.0. *X*", onde *X* depende do número de compilação instalado.</span><span class="sxs-lookup"><span data-stu-id="90eb2-110">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="90eb2-111">O prefixo "v" é necessário.</span><span class="sxs-lookup"><span data-stu-id="90eb2-111">The "v" prefix is required.</span></span>  
  
 `riid`  
 <span data-ttu-id="90eb2-112">[in] O identificador para a interface desejada.</span><span class="sxs-lookup"><span data-stu-id="90eb2-112">[in] The identifier for the desired interface.</span></span> <span data-ttu-id="90eb2-113">Atualmente, o único valor válido para esse parâmetro é IID_ICLRRuntimeInfo.</span><span class="sxs-lookup"><span data-stu-id="90eb2-113">Currently, the only valid value for this parameter is IID_ICLRRuntimeInfo.</span></span>  
  
 `ppRuntime`  
 <span data-ttu-id="90eb2-114">[out] Um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que corresponde ao tempo de execução solicitado.</span><span class="sxs-lookup"><span data-stu-id="90eb2-114">[out] A pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that corresponds to the requested runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90eb2-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="90eb2-115">Return Value</span></span>  
 <span data-ttu-id="90eb2-116">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="90eb2-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90eb2-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90eb2-117">HRESULT</span></span>|<span data-ttu-id="90eb2-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="90eb2-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90eb2-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="90eb2-119">S_OK</span></span>|<span data-ttu-id="90eb2-120">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="90eb2-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="90eb2-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="90eb2-121">E_POINTER</span></span>|<span data-ttu-id="90eb2-122">`pwzVersion` ou `ppRuntime` é nulo.</span><span class="sxs-lookup"><span data-stu-id="90eb2-122">`pwzVersion` or `ppRuntime` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90eb2-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="90eb2-123">Remarks</span></span>  
 <span data-ttu-id="90eb2-124">Esse método consistentemente interage com interfaces herdadas, como o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface e herdado funções como preteridas `CorBindTo*` funções (consulte [preterido hospedando funções CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) na API de hospedagem do .NET Framework 2.0).</span><span class="sxs-lookup"><span data-stu-id="90eb2-124">This method interacts consistently with legacy interfaces such as the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface and legacy functions such as the deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span> <span data-ttu-id="90eb2-125">Ou seja, tempos de execução que são carregados com a API herdada são visíveis para a nova API e tempos de execução que são carregados com a nova API são visíveis para a API herdada.</span><span class="sxs-lookup"><span data-stu-id="90eb2-125">That is, runtimes that are loaded with the legacy API are visible to the new API, and runtimes that are loaded with the new API are visible to the legacy API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90eb2-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90eb2-126">Requirements</span></span>  
 <span data-ttu-id="90eb2-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90eb2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90eb2-128">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="90eb2-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="90eb2-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="90eb2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90eb2-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90eb2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90eb2-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90eb2-131">See also</span></span>

- [<span data-ttu-id="90eb2-132">Interface ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="90eb2-132">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="90eb2-133">Interfaces e coclasses de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="90eb2-133">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)
- [<span data-ttu-id="90eb2-134">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="90eb2-134">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="90eb2-135">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="90eb2-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="90eb2-136">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="90eb2-136">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
