---
title: "Método ICLRMetaHost::RequestRuntimeLoadedNotification"
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
f1_keywords: ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32eb92263685bc3be9f0c28dea88ecfa78c2b52c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>Método ICLRMetaHost::RequestRuntimeLoadedNotification
Fornece uma função de retorno de chamada que é garantida para ser chamado quando uma versão de runtime (CLR) de linguagem comum é carregado pela primeira vez, mas ainda não começou. Esse método substitui o [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallbackFunction`  
 [in] A função de retorno de chamada que é chamada quando um novo tempo de execução foi carregado.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pCallbackFunction` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada funciona da seguinte maneira:  
  
-   O retorno de chamada é invocado apenas quando um tempo de execução é carregado pela primeira vez.  
  
-   O retorno de chamada não é invocado para cargas reentrantes de tempo de execução do mesmo.  
  
-   Para cargas de tempo de execução não reentrante chamadas para a função de retorno de chamada são serializadas.  
  
 A função de retorno de chamada tem o seguinte protótipo:  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Os protótipos de função de retorno de chamada são os seguintes:  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Se o host pretende carregar ou fazer com que o outro em tempo de execução a ser carregado de forma reentrante o `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` parâmetros que são fornecidas no retorno de chamada a função deve ser usada da seguinte maneira:  
  
-   `pfnCallbackThreadSet`deve ser chamado pelo thread que pode causar uma carga de tempo de execução antes de uma tentativa de tal carga.  
  
-   `pfnCallbackThreadUnset`deve ser chamado quando o thread não fará com que tal carga de tempo de execução (e antes de retornar de retorno de chamada inicial).  
  
-   `pfnCallbackThreadSet`e `pfnCallbackThreadUnset` são ambos não reentrante.  
  
> [!NOTE]
>  Hospedar aplicativos não devem chamar `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` fora do escopo de `pCallbackFunction` parâmetro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
