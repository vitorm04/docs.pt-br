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
ms.openlocfilehash: e01affb5edb8b0766edf8548ae34cf8220bcc62d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a>Método ICLRMetaHostPolicy::GetRequestedRuntime
Fornece uma interface para uma versão preferencial do common language runtime (CLR) com base em uma política de hospedagem, assembly gerenciado, cadeia de caracteres de versão e fluxo de configuração. Esse método não carregar ou ativar o CLR, mas simplesmente retorna o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que representa o resultado da política. Esse método substitui o [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md), e [GetCORRequiredVersion](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md) métodos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`dwPolicyFlags`|[in] Necessário. Especifica um membro do [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeração, que representa uma política de vinculação e qualquer número de modificadores. A única política que está disponível no momento é [METAHOST_POLICY_HIGHCOMPAT](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).<br /><br /> Modificadores de incluem [METAHOST_POLICY_EMULATE_EXE_LAUNCH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md), e [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md).|  
|`pwzBinary`|[in] Opcional. Especifica o caminho do arquivo de assembly.|  
|`pCfgStream`|[in] Opcional. Especifica o arquivo de configuração como um <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|  
|`pwzVersion`|[out no] Opcional. Especifica ou retorna a versão do CLR preferencial para ser carregado.|  
|`pcchVersion`|[out no] Necessário. Especifica o tamanho esperado do `pwzVersion` como entrada, para evitar estouros de buffer. Se `pwzVersion` for nulo, `pcchVersion` contém o tamanho esperado do `pwzVersion` quando `GetRequestedRuntime` retorna, para permitir a pré-alocação; caso contrário, `pcchVersion` contém o número de caracteres gravados `pwzVersion`.|  
|`pwzImageVersion`|[out] Opcional. Quando `GetRequestedRuntime` retorna, contém a versão CLR correspondente para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface é retornada.|  
|`pcchImageVersion`|[out no] Opcional. Especifica o tamanho do `pwzImageVersion` como entrada para evitar estouros de buffer. Se `pwzImageVersion` for nulo, `pcchImageVersion` contém o tamanho necessário do `pwzImageVersion` quando `GetRequestedRuntime` retorna, para permitir a pré-alocação.|  
|`pdwConfigFlags`|[out] Opcional. Se `GetRequestedRuntime` usa um arquivo de configuração durante o processo de associação, quando ela retorna, `pdwConfigFlags` contém um [METAHOST_CONFIG_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) valor que indica se o [ \<inicialização >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) elemento tem o `useLegacyV2RuntimeActivationPolicy` conjunto e o valor do atributo do atributo. Aplicar o [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](../../../../docs/framework/unmanaged-api/hosting/metahost-config-flags-enumeration.md) máscara para `pdwConfigFlags` para obter os valores relevantes para `useLegacyV2RuntimeActivationPolicy`.|  
|`riid`|[in] Especifica o identificador de interface IID_ICLRRuntimeInfo para a solicitação [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.|  
|`ppRuntime`|[out] Quando `GetRequestedRuntime` retorna, contém um ponteiro para o correspondente [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.|  
  
## <a name="remarks"></a>Comentários  
 Quando esse método for bem-sucedido, ele tem como efeito colateral da combinação de sinalizadores adicionais com os sinalizadores de inicialização padrão atual da interface do tempo de execução retornado, se e somente se um ou mais dos seguintes elementos existem no fluxo de configuração dentro de `<configuration><runtime>` seção:  
  
-   `<gcServer enabled="true"/>` faz com que `STARTUP_SERVER_GC` a ser definido.  
  
-   `<etwEnable enabled="true"/>` faz com que `STARTUP_ETW` a ser definido.  
  
-   `<appDomainResourceMonitoring enabled="true"/>` faz com que `STARTUP_ARM` a ser definido.  
  
 O padrão resultante `STARTUP_FLAGS` valor é a combinação de OR bit a bit dos valores que são definidos na lista anterior com os sinalizadores de inicialização padrão.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pwzVersion` não é nulo e `pcchVersion` é nulo.<br /><br /> -ou-<br /><br /> `pwzImageVersion` não é nulo e `pcchImageVersion` é nulo.|  
|E_INVALIDARG|`dwPolicyFlags` não especifique `METAHOST_POLICY_HIGHCOMPAT`.|  
|ERROR_INSUFFICIENT_BUFFER|A memória alocada para `pwzVerison` é inadequado.<br /><br /> -ou-<br /><br /> A memória alocada para `pwzImageVerison` é inadequado.|  
|CLR_E_SHIM_RUNTIMELOAD|`dwPolicyFlags` inclui METAHOST_POLICY_APPLY_UPGRADE_POLICY e ambos `pwzVersion` e `pcchVersion` são nulos.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 [Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
