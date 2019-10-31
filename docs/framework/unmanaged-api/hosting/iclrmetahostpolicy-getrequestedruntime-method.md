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
ms.openlocfilehash: 1b07029990ef529ded57bc569beff1061ad0f938
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140872"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>Método ICLRMetaHostPolicy::GetRequestedRuntime

Fornece uma interface para uma versão preferencial do Common Language Runtime (CLR) com base em uma política de hospedagem, assembly gerenciado, Cadeia de caracteres de versão e fluxo de configuração. Esse método, na verdade, não carrega nem ativa o CLR, mas simplesmente retorna a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) que representa o resultado da política. Esse método substitui os métodos [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)e [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) .

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

## <a name="parameters"></a>Parâmetros

|Name|Descrição|
|----------|-----------------|
|`dwPolicyFlags`|no Necessário. Especifica um membro da enumeração [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) , que representa uma política de associação e qualquer número de modificadores. A única política disponível atualmente é [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Os modificadores incluem [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md)e [METAHOST_POLICY_ ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|
|`pwzBinary`|[in] Opcional. Especifica o caminho do arquivo do assembly.|
|`pCfgStream`|[in] Opcional. Especifica o arquivo de configuração como um <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|`pwzVersion`|[entrada, saída] Adicional. Especifica ou retorna a versão de CLR preferida a ser carregada.|
|`pcchVersion`|[entrada, saída] Necessário. Especifica o tamanho esperado de `pwzVersion` como entrada, para evitar estouros de buffer. Se `pwzVersion` for NULL, `pcchVersion` conterá o tamanho esperado de `pwzVersion` quando `GetRequestedRuntime` retornar, para permitir a pré-autenticação; caso contrário, `pcchVersion` conterá o número de caracteres gravados em `pwzVersion`.|
|`pwzImageVersion`|fora Adicional. Quando `GetRequestedRuntime` retorna, contém a versão do CLR correspondente à interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) que é retornada.|
|`pcchImageVersion`|[entrada, saída] Adicional. Especifica o tamanho de `pwzImageVersion` como entrada para evitar estouros de buffer. Se `pwzImageVersion` for NULL, `pcchImageVersion` conterá o tamanho necessário de `pwzImageVersion` quando `GetRequestedRuntime` retornar, para permitir a pré-autenticação.|
|`pdwConfigFlags`|fora Adicional. Se `GetRequestedRuntime` usar um arquivo de configuração durante o processo de associação, quando ele retornar, `pdwConfigFlags` conterá um valor [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) que indica se o elemento [> de inicialização\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) tem o atributo de `useLegacyV2RuntimeActivationPolicy` definido e o valor de o atributo. Aplique a máscara [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) a `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy`.|
|`riid`|no Especifica o identificador de interface IID_ICLRRuntimeInfo para a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) solicitada.|
|`ppRuntime`|fora Quando `GetRequestedRuntime` retorna, contém um ponteiro para a interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) correspondente.|

## <a name="remarks"></a>Comentários

Quando esse método for bem sucedido, ele terá o efeito colateral de combinar sinalizadores adicionais com os sinalizadores de inicialização padrão atuais da interface de tempo de execução retornada, se e somente se um ou mais dos seguintes elementos existirem no fluxo de configuração dentro do `<configuration><runtime>` Section

- `<gcServer enabled="true"/>` faz `STARTUP_SERVER_GC` ser definido.

- `<etwEnable enabled="true"/>` faz `STARTUP_ETW` ser definido.

- `<appDomainResourceMonitoring enabled="true"/>` faz `STARTUP_ARM` ser definido.

O valor de `STARTUP_FLAGS` padrão resultante é a combinação de bits ou de valores definidos na lista anterior com os sinalizadores de inicialização padrão.

## <a name="return-value"></a>Valor retornado

Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.

|HRESULT|Descrição|
|-------------|-----------------|
|S_OK|O método foi concluído com êxito.|
|E_POINTER|`pwzVersion` não é nulo e `pcchVersion` é nulo.<br /><br /> \- ou -<br /><br /> `pwzImageVersion` não é nulo e `pcchImageVersion` é nulo.|
|E_INVALIDARG|`dwPolicyFlags` não especifica `METAHOST_POLICY_HIGHCOMPAT`.|
|ERROR_INSUFFICIENT_BUFFER|A memória alocada para `pwzVersion` é inadequada.<br /><br /> \- ou -<br /><br /> A memória alocada para `pwzImageVersion` é inadequada.|
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` inclui METAHOST_POLICY_APPLY_UPGRADE_POLICY e `pwzVersion` e `pcchVersion` são nulos.|

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).

**Cabeçalho:** MetaHost. h

**Biblioteca:** Incluído como um recurso em MSCorEE. dll

**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Consulte também

- [Interface ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)
- [Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
