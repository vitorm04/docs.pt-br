---
title: Método ICLRMetaHost::RequestRuntimeLoadedNotification
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f3ac053f12cb4bc37ab0bd16036fb561f8f176c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519119"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>Método ICLRMetaHost::RequestRuntimeLoadedNotification
Fornece uma função de retorno de chamada que é garantida para ser chamado quando uma versão do common language runtime (CLR) é carregado pela primeira vez, mas ainda não foi iniciada. Esse método substitui o [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallbackFunction`  
 [in] A função de retorno de chamada é invocada quando um novo tempo de execução foi carregado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pCallbackFunction` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada funciona da seguinte maneira:  
  
-   O retorno de chamada é invocado apenas quando um tempo de execução é carregado pela primeira vez.  
  
-   O retorno de chamada não é invocado para cargas reentrantes de tempo de execução do mesmo.  
  
-   Para cargas de tempo de execução não reentrante, chamadas para a função de retorno de chamada são serializadas.  
  
 A função de retorno de chamada tem o seguinte protótipo:  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Os protótipos de função de retorno de chamada são da seguinte maneira:  
  
-   `pfnCallbackThreadSet`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   `pfnCallbackThreadUnset`:  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Se o host pretende carregar ou fazer com que o outro runtime a ser carregado de forma reentrante, o `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` parâmetros que são fornecidos no retorno de chamada a função deve ser usada da seguinte maneira:  
  
-   `pfnCallbackThreadSet` deve ser chamado pelo thread que pode causar uma carga de tempo de execução antes da tentativa de tal carga.  
  
-   `pfnCallbackThreadUnset` deve ser chamado quando o thread não fará com que tal uma carga de tempo de execução (e antes de retornar do retorno de chamada inicial).  
  
-   `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` são ambos não reentrante.  
  
> [!NOTE]
>  Hospedar aplicativos não devem chamar `pfnCallbackThreadSet` e `pfnCallbackThreadUnset` fora do escopo de `pCallbackFunction` parâmetro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
