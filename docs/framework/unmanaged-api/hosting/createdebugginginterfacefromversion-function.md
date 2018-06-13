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
ms.openlocfilehash: 1b51b924652019cf05401e1972797c18e74b82d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431542"
---
# <a name="createdebugginginterfacefromversion-function"></a>Função CreateDebuggingInterfaceFromVersion
Cria um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objeto com base nas informações de versão especificada.  
  
 Essa função é obsoleta no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Em vez disso, para obter uma interface para o common language runtime (CLR) 2.0, use o [Iclrruntimeinfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) método e especifique o identificador de classe CLSID_CLRDebuggingLegacy e o identificador de interface IID_ICorDebug. Para obter uma interface CLR 4 ou posterior, chame o [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) de função e especifique o identificador de classe CLSID_CLRDebugging e o identificador de interface IID_ICLRDebugging.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `iDebuggerVersion`  
 [in] A versão do `ICorDebug` que é esperado pelo depurador. Consulte o [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeração para os valores válidos.  
  
 `szDebuggeeVersion`  
 [in] A versão de tempo de execução language comuns associada ao aplicativo ou processo a ser depurado. Consulte o [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) método para obter informações sobre como recuperar esse valor.  
  
 `ppCordb`  
 [out] O local que recebe um ponteiro para o `ICorDebug` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna códigos de erro padrão COM conforme definido no arquivo de Winerror. H, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|`szDebuggeeVersion` ou `ppCordb` é nulo ou a versão de cadeia de caracteres está incorreta.|  
  
## <a name="remarks"></a>Comentários  
 O `szDebuggeeVersion` parâmetro mapeado para a versão correspondente do MSCorDbi.dll.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
