---
title: "Método ICLRMetaHost::QueryLegacyV2RuntimeBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>Método ICLRMetaHost::QueryLegacyV2RuntimeBinding
Retorna uma interface que representa um tempo de execução para o qual a política de ativação herdadas foi associada, por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo no [ \<inicialização > elemento](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) entrada do arquivo de configuração, pelo uso direto de ativação herdada APIs, ou chamando o [Bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `riid`  
 [in] Required.Currently é o único valor válido para este parâmetro `IID_ICLRRuntimeInfo`.  
  
 `ppUnk`  
 [out] Necessário. Quando este método retorna, contém um ponteiro para o [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface que representa um tempo de execução que foi associado à política de ativação herdadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluída com êxito e retornou um tempo de execução que foi associado à política de ativação herdadas.|  
|S_FALSE|O método foi concluída com êxito, mas um tempo de execução herdado não ainda estiver associado.|  
|E_NOINTERFACE|O método encontrado um tempo de execução que foi associado à política de ativação herdadas, mas `riid` em tempo de execução que não tem suporte.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
