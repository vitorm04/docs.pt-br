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
ms.openlocfilehash: e23dfb86c2129a02a0ca95de8c89d8294e97ad81
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136845"
---
# <a name="createdebugginginterfacefromversion-function"></a>Função CreateDebuggingInterfaceFromVersion
Cria um objeto [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) com base nas informações de versão especificadas.  
  
 Essa função está obsoleta no .NET Framework 4. Em vez disso, para obter uma interface para o Common Language Runtime (CLR) 2,0, use o método [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) e especifique o identificador de classe CLSID_CLRDebuggingLegacy e o identificador de interface IID_ICorDebug. Para obter uma interface para o CLR 4 ou posterior, chame a função [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) e especifique o identificador de classe CLSID_CLRDebugging e o identificador de interface IID_ICLRDebugging.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iDebuggerVersion`  
 no A versão do `ICorDebug` esperada pelo depurador. Consulte a enumeração [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) para obter os valores válidos.  
  
 `szDebuggeeVersion`  
 no A versão de Common Language Runtime associada ao aplicativo ou processo a ser depurado. Consulte o método [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) para obter informações sobre como recuperar esse valor.  
  
 `ppCordb`  
 fora O local que recebe um ponteiro para o objeto `ICorDebug`.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna códigos de erro COM padrão, conforme definido no arquivo WinError. h, além dos valores a seguir.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com êxito.|  
|E_INVALIDARG|`szDebuggeeVersion` ou `ppCordb` é nulo ou a cadeia de caracteres da versão está incorreta.|  
  
## <a name="remarks"></a>Comentários  
 O parâmetro `szDebuggeeVersion` é mapeado para a versão correspondente do MSCorDbi. dll.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Funções de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
