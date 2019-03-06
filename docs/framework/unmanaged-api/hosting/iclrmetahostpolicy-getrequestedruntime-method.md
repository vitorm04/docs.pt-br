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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1516b6661402ee71448e0d6987e4ed32a0ce5296
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371457"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>Método ICLRMetaHostPolicy::GetRequestedRuntime

Fornece uma interface para uma versão de preferência do common language runtime (CLR) com base em uma política de hospedagem, assembly gerenciado, cadeia de caracteres de versão e fluxo de configuração. Esse método, na verdade não carregar ou ativar o CLR, mas simplesmente retorna o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que representa o resultado da política. Esse método substitui o [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), e [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) métodos.

## <a name="syntax"></a>Sintaxe

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

#### <a name="parameters"></a>Parâmetros

|Nome|Descrição|
|----------|-----------------|
|`dwPolicyFlags`|[in] Necessário. Especifica um membro do [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeração, que representa uma política de vinculação e qualquer número de modificadores. É a única política que está disponível no momento [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Os modificadores incluem [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), e [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|[in] Opcional. Especifica o caminho de arquivo do assembly.|
|`pCfgStream`|[in] Opcional. Especifica o arquivo de configuração como um <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[no, out] Opcional. Especifica ou retorna a versão do CLR preferencial para ser carregado.|
|`pcchVersion`|[no, out] Necessário. Especifica o tamanho esperado do `pwzVersion` como entrada, para evitar estouros de buffer. Se `pwzVersion` for nulo, `pcchVersion` contém o tamanho esperado do `pwzVersion` quando `GetRequestedRuntime` retorna, para permitir que a pré-alocação; caso contrário, `pcchVersion` contém o número de caracteres gravados `pwzVersion`.|
|`pwzImageVersion`|[out] Opcional. Quando `GetRequestedRuntime` retorna, contém a versão CLR correspondente para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que é retornado.|
|`pcchImageVersion`|[no, out] Opcional. Especifica o tamanho do `pwzImageVersion` como entrada para evitar estouros de buffer. Se `pwzImageVersion` for nulo, `pcchImageVersion` contém o tamanho necessário da `pwzImageVersion` quando `GetRequestedRuntime` retorna, para permitir que a pré-alocação.|
|`pdwConfigFlags`|[out] Opcional. Se `GetRequestedRuntime` usa um arquivo de configuração durante o processo de associação, quando ele é retornado, `pdwConfigFlags` contém uma [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) valor que indica se o [ \<inicialização >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) elemento tem o `useLegacyV2RuntimeActivationPolicy` conjunto e o valor do atributo do atributo. Aplicar a [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) mascarar a `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy`.|
|`riid`|[in] Especifica o identificador de interface IID_ICLRRuntimeInfo para solicitada [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.|
|`ppRuntime`|[out] Quando `GetRequestedRuntime` retorna, contém um ponteiro para os respectivos [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.|

## <a name="remarks"></a>Comentários

Quando esse método for bem-sucedido, ele tem o efeito colateral da combinação de sinalizadores adicionais com os sinalizadores de inicialização padrão atual da interface do tempo de execução retornado, se e somente se um ou mais dos seguintes elementos existem no fluxo de configuração dentro de `<configuration><runtime>` seção:

- `<gcServer enabled="true"/>` faz com que `STARTUP_SERVER_GC` a ser definido.

- `<etwEnable enabled="true"/>` faz com que `STARTUP_ETW` a ser definido.

- `<appDomainResourceMonitoring enabled="true"/>` faz com que `STARTUP_ARM` a ser definido.

O padrão resultante `STARTUP_FLAGS` valor é a combinação OR bit a bit dos valores que são definidos na lista anterior com os sinalizadores de inicialização padrão.

## <a name="return-value"></a>Valor de retorno

Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.

|HRESULT|Descrição|
|-------------|-----------------|
|S_OK|O método foi concluído com êxito.|
|E_POINTER|`pwzVersion` não é nulo e `pcchVersion` é nulo.<br /><br /> -ou-<br /><br /> `pwzImageVersion` não é nulo e `pcchImageVersion` é nulo.|
|E_INVALIDARG|`dwPolicyFlags` não especifique `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|A memória alocada para `pwzVersion` é inadequado.<br /><br /> -ou-<br /><br /> A memória alocada para `pwzImageVersion` é inadequado.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` inclui METAHOST_POLICY_APPLY_UPGRADE_POLICY e ambos `pwzVersion` e `pcchVersion` são nulos.|

## <a name="requirements"></a>Requisitos

**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** MetaHost.h

**Biblioteca:** Incluído como um recurso em mscoree. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
