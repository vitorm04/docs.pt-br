---
title: Método ICLRMetaHostPolicy::GetRequestedRuntime
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 37167b7a9aefa6cd9d5e4df043e8bbc1b0514261
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504115"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="35c41-102">Método ICLRMetaHostPolicy::GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="35c41-102">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="35c41-103">Fornece uma interface para uma versão preferencial do Common Language Runtime (CLR) com base em uma política de hospedagem, assembly gerenciado, Cadeia de caracteres de versão e fluxo de configuração.</span><span class="sxs-lookup"><span data-stu-id="35c41-103">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="35c41-104">Esse método, na verdade, não carrega nem ativa o CLR, mas simplesmente retorna a interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) que representa o resultado da política.</span><span class="sxs-lookup"><span data-stu-id="35c41-104">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="35c41-105">Esse método substitui os métodos [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)e [GetCORRequiredVersion](getcorrequiredversion-function.md) .</span><span class="sxs-lookup"><span data-stu-id="35c41-105">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="35c41-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35c41-106">Syntax</span></span>

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a><span data-ttu-id="35c41-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35c41-107">Parameters</span></span>

|<span data-ttu-id="35c41-108">Nome</span><span class="sxs-lookup"><span data-stu-id="35c41-108">Name</span></span>|<span data-ttu-id="35c41-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="35c41-109">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="35c41-110">no Necessário.</span><span class="sxs-lookup"><span data-stu-id="35c41-110">[in] Required.</span></span> <span data-ttu-id="35c41-111">Especifica um membro da enumeração de [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) , que representa uma política de associação e qualquer número de modificadores.</span><span class="sxs-lookup"><span data-stu-id="35c41-111">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="35c41-112">A única política disponível no momento é [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="35c41-112">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="35c41-113">Os modificadores incluem [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)e [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="35c41-113">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="35c41-114">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="35c41-114">[in] Optional.</span></span> <span data-ttu-id="35c41-115">Especifica o caminho do arquivo do assembly.</span><span class="sxs-lookup"><span data-stu-id="35c41-115">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="35c41-116">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="35c41-116">[in] Optional.</span></span> <span data-ttu-id="35c41-117">Especifica o arquivo de configuração como um <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="35c41-117">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="35c41-118">[entrada, saída] Adicional.</span><span class="sxs-lookup"><span data-stu-id="35c41-118">[in, out] Optional.</span></span> <span data-ttu-id="35c41-119">Especifica ou retorna a versão de CLR preferida a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="35c41-119">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="35c41-120">[entrada, saída] Necessário.</span><span class="sxs-lookup"><span data-stu-id="35c41-120">[in, out] Required.</span></span> <span data-ttu-id="35c41-121">Especifica o tamanho esperado de `pwzVersion` como entrada, para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="35c41-121">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="35c41-122">Se `pwzVersion` for NULL, `pcchVersion` conterá o tamanho esperado de `pwzVersion` quando `GetRequestedRuntime` retorna, para permitir pré-alocação; caso contrário, `pcchVersion` conterá o número de caracteres gravados `pwzVersion` .</span><span class="sxs-lookup"><span data-stu-id="35c41-122">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="35c41-123">fora Adicional.</span><span class="sxs-lookup"><span data-stu-id="35c41-123">[out] Optional.</span></span> <span data-ttu-id="35c41-124">Quando `GetRequestedRuntime` retorna, contém a versão do CLR correspondente à interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) que é retornada.</span><span class="sxs-lookup"><span data-stu-id="35c41-124">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="35c41-125">[entrada, saída] Adicional.</span><span class="sxs-lookup"><span data-stu-id="35c41-125">[in, out] Optional.</span></span> <span data-ttu-id="35c41-126">Especifica o tamanho de `pwzImageVersion` como entrada para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="35c41-126">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="35c41-127">Se `pwzImageVersion` for NULL, `pcchImageVersion` conterá o tamanho necessário de `pwzImageVersion` quando `GetRequestedRuntime` retorna, para permitir a pré-autenticação.</span><span class="sxs-lookup"><span data-stu-id="35c41-127">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="35c41-128">fora Adicional.</span><span class="sxs-lookup"><span data-stu-id="35c41-128">[out] Optional.</span></span> <span data-ttu-id="35c41-129">Se `GetRequestedRuntime` o usar um arquivo de configuração durante o processo de associação, quando ele retornar, `pdwConfigFlags` conterá um valor [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) que indica se o [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) elemento tem o `useLegacyV2RuntimeActivationPolicy` atributo definido e o valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="35c41-129">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="35c41-130">Aplique a máscara de [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) para `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="35c41-130">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="35c41-131">no Especifica o identificador de interface IID_ICLRRuntimeInfo para a interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) solicitada.</span><span class="sxs-lookup"><span data-stu-id="35c41-131">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="35c41-132">fora Quando `GetRequestedRuntime` retorna, contém um ponteiro para a interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) correspondente.</span><span class="sxs-lookup"><span data-stu-id="35c41-132">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="35c41-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="35c41-133">Remarks</span></span>

<span data-ttu-id="35c41-134">Quando esse método for bem sucedido, ele terá o efeito colateral de combinar sinalizadores adicionais com os sinalizadores de inicialização padrão atuais da interface de tempo de execução retornada, se e somente se um ou mais dos seguintes elementos existirem no fluxo de configuração dentro da `<configuration><runtime>` seção:</span><span class="sxs-lookup"><span data-stu-id="35c41-134">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="35c41-135">`<gcServer enabled="true"/>`faz com que `STARTUP_SERVER_GC` seja definido.</span><span class="sxs-lookup"><span data-stu-id="35c41-135">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="35c41-136">`<etwEnable enabled="true"/>`faz com que `STARTUP_ETW` seja definido.</span><span class="sxs-lookup"><span data-stu-id="35c41-136">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="35c41-137">`<appDomainResourceMonitoring enabled="true"/>`faz com que `STARTUP_ARM` seja definido.</span><span class="sxs-lookup"><span data-stu-id="35c41-137">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="35c41-138">O valor padrão resultante `STARTUP_FLAGS` é a combinação de bits ou de valores definidos na lista anterior com os sinalizadores de inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="35c41-138">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="35c41-139">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="35c41-139">Return Value</span></span>

<span data-ttu-id="35c41-140">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="35c41-140">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="35c41-141">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35c41-141">HRESULT</span></span>|<span data-ttu-id="35c41-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="35c41-142">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="35c41-143">S_OK</span><span class="sxs-lookup"><span data-stu-id="35c41-143">S_OK</span></span>|<span data-ttu-id="35c41-144">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="35c41-144">The method completed successfully.</span></span>|
|<span data-ttu-id="35c41-145">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="35c41-145">E_POINTER</span></span>|<span data-ttu-id="35c41-146">`pwzVersion`Não é nulo e `pcchVersion` é nulo.</span><span class="sxs-lookup"><span data-stu-id="35c41-146">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="35c41-147">-ou-</span><span class="sxs-lookup"><span data-stu-id="35c41-147">-or-</span></span><br /><br /> <span data-ttu-id="35c41-148">`pwzImageVersion`Não é nulo e `pcchImageVersion` é nulo.</span><span class="sxs-lookup"><span data-stu-id="35c41-148">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="35c41-149">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="35c41-149">E_INVALIDARG</span></span>|<span data-ttu-id="35c41-150">`dwPolicyFlags`não especifica `METAHOST_POLICY_HIGHCOMPAT` .</span><span class="sxs-lookup"><span data-stu-id="35c41-150">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="35c41-151">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="35c41-151">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="35c41-152">A memória alocada para `pwzVersion` é inadequada.</span><span class="sxs-lookup"><span data-stu-id="35c41-152">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="35c41-153">-ou-</span><span class="sxs-lookup"><span data-stu-id="35c41-153">-or-</span></span><br /><br /> <span data-ttu-id="35c41-154">A memória alocada para `pwzImageVersion` é inadequada.</span><span class="sxs-lookup"><span data-stu-id="35c41-154">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="35c41-155">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="35c41-155">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="35c41-156">`dwPolicyFlags`inclui METAHOST_POLICY_APPLY_UPGRADE_POLICY e ambos `pwzVersion` e `pcchVersion` são nulos.</span><span class="sxs-lookup"><span data-stu-id="35c41-156">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="35c41-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35c41-157">Requirements</span></span>

<span data-ttu-id="35c41-158">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35c41-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="35c41-159">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="35c41-159">**Header:** MetaHost.h</span></span>

<span data-ttu-id="35c41-160">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="35c41-160">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="35c41-161">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35c41-161">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="35c41-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="35c41-162">See also</span></span>

- [<span data-ttu-id="35c41-163">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="35c41-163">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="35c41-164">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="35c41-164">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="35c41-165">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="35c41-165">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="35c41-166">Hosting</span><span class="sxs-lookup"><span data-stu-id="35c41-166">Hosting</span></span>](index.md)
