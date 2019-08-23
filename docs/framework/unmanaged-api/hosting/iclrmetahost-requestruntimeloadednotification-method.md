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
ms.openlocfilehash: 539f69c33b67ad1a8a514062c5d777deaced1599
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965001"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>Método ICLRMetaHost::RequestRuntimeLoadedNotification
Fornece uma função de retorno de chamada que tem a garantia de ser chamada quando uma versão Common Language Runtime (CLR) é carregada pela primeira vez, mas ainda não foi iniciada. Esse método substitui a função [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pCallbackFunction`  
 no A função de retorno de chamada que é invocada quando um novo tempo de execução é carregado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_POINTER|`pCallbackFunction` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 O retorno de chamada funciona da seguinte maneira:  
  
- O retorno de chamada é invocado somente quando um tempo de execução é carregado pela primeira vez.  
  
- O retorno de chamada não é invocado para cargas reentrante do mesmo tempo de execução.  
  
- Para cargas de tempo de execução não reentrante, as chamadas para a função de retorno de chamada são serializadas.  
  
 A função de retorno de chamada tem o seguinte protótipo:  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Os protótipos de função de retorno de chamada são os seguintes:  
  
- `pfnCallbackThreadSet`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Se o host pretende carregar ou fazer com que outro tempo de execução seja carregado de maneira reentrante, os `pfnCallbackThreadSet` parâmetros e `pfnCallbackThreadUnset` fornecidos na função de retorno de chamada devem ser usados da seguinte maneira:  
  
- `pfnCallbackThreadSet`deve ser chamado pelo thread que pode causar uma carga de tempo de execução antes que essa carga seja tentada.  
  
- `pfnCallbackThreadUnset`deve ser chamado quando o thread não causar mais tal carga de tempo de execução (e antes de retornar do retorno de chamada inicial).  
  
- `pfnCallbackThreadSet`e `pfnCallbackThreadUnset` que não são reentrante.  
  
> [!NOTE]
> Os aplicativos host não devem `pfnCallbackThreadSet` chamar `pfnCallbackThreadUnset` e `pCallbackFunction` fora do escopo do parâmetro.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost.h  
  
 **Biblioteca** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
