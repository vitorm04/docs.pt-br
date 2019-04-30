---
title: Função CreateDebuggingInterfaceFromVersion
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d1c49e8762d00e3e154c598c2542c4a76b9b28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985706"
---
# <a name="createdebugginginterfacefromversion-function"></a>Função CreateDebuggingInterfaceFromVersion
Cria uma [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objeto com base nas informações de versão especificadas.  
  
 Essa função é obsoleta no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Em vez disso, para obter uma interface para o common language runtime (CLR) 2.0, use o [iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) método e especifique o identificador de classe CLSID_CLRDebuggingLegacy e o identificador de interface IID_ICorDebug. Para obter uma interface CLR 4 ou posterior, chame o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) de função e especifique o identificador de classe CLSID_CLRDebugging e o identificador de interface IID_ICLRDebugging.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iDebuggerVersion`  
 [in] A versão do `ICorDebug` que é esperado pelo depurador. Consulte a [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeração para os valores válidos.  
  
 `szDebuggeeVersion`  
 [in] A versão common language runtime associado com o aplicativo ou processo a ser depurado. Consulte a [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) método para obter informações sobre como recuperar esse valor.  
  
 `ppCordb`  
 [out] O local que recebe um ponteiro para o `ICorDebug` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro padrão COM conforme definido no arquivo Winerror h, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|`szDebuggeeVersion` ou `ppCordb` é nulo ou a versão de cadeia de caracteres está incorreta.|  
  
## <a name="remarks"></a>Comentários  
 O `szDebuggeeVersion` parâmetro é mapeado para a versão correspondente do mscordbi.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
