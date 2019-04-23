---
title: Método ICLRRuntimeInfo::GetInterface
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f229e421cc69f2ff45110233c4c6c36d7a1fc4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152744"
---
# <a name="iclrruntimeinfogetinterface-method"></a>Método ICLRRuntimeInfo::GetInterface
Carrega o CLR no processo atual e retorna o tempo de execução de ponteiros de interface, tais como [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), e [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).  
  
 Esse método substitui todos o `CorBindTo`* funções na [funções de hospedagem de CLR preterido](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) seção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `rclsid`  
 [in] A interface do CLSID para coclass.  
  
 `riid`  
 [in] O IID da solicitada `rclsid` interface.  
  
 `ppUnk`  
 [out] Um ponteiro para a interface consultado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`ppUnk` é nulo.|  
|E_OUTOFMEMORY|Não há memória suficiente está disponível para tratar a solicitação.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Um tempo de execução diferente já foi associado à política de 2 de ativação de versão do CLR herdada.|  
  
## <a name="remarks"></a>Comentários  
 Esse método faz com que o CLR a ser carregado, mas não inicializado.  
  
 A tabela a seguir mostra as combinações com suporte para `rclsid` e `riid`.  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|CLSID_CorMetaDataDispenser|IID_IMetaDataDispenser, IID_IMetaDataDispenserEx|  
|CLSID_CorMetaDataDispenserRuntime|IID_IMetaDataDispenser, IID_IMetaDataDispenserEx|  
|CLSID_CorRuntimeHost|IID_ICorRuntimeHost|  
|CLSID_CLRRuntimeHost|IID_ICLRRuntimeHost|  
|CLSID_TypeNameFactory|IID_ITypeNameFactory|  
|CLSID_CLRDebuggingLegacy|IID_ICorDebug|  
|||  
|CLSID_CLRStrongName|IID_ICLRStrongName|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
