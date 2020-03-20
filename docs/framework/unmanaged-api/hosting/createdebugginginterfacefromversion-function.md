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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176442"
---
# <a name="createdebugginginterfacefromversion-function"></a>Função CreateDebuggingInterfaceFromVersion
Cria um objeto [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) com base nas informações da versão especificada.  
  
 Esta função está obsoleta no Quadro .NET 4. Em vez disso, para obter uma interface para o tempo de execução de idioma comum (CLR) 2.0, use o método [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) e especifique o identificador de classe CLSID_CLRDebuggingLegacy e o identificador de interface IID_ICorDebug. Para obter uma interface para CLR 4 ou posterior, ligue para a função [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) e especifique o identificador de classe CLSID_CLRDebugging e o identificador de interface IID_ICLRDebugging.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,
    [in]  LPCWSTR  szDebuggeeVersion,
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `iDebuggerVersion`  
 [em] A versão `ICorDebug` disso é esperada pelo depurador. Consulte a [enumeração CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) para obter valores válidos.  
  
 `szDebuggeeVersion`  
 [em] A versão em tempo de execução do idioma comum associada ao aplicativo ou processo a ser depurado. Consulte o método [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) ou [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) para obter informações sobre como recuperar esse valor.  
  
 `ppCordb`  
 [fora] O local que recebe `ICorDebug` um ponteiro para o objeto.  
  
## <a name="return-value"></a>Valor retornado  
 Este método retorna códigos de erro COM padrão conforme definido no arquivo WinError.h, além dos seguintes valores.  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|S_OK|O método foi concluído com sucesso.|  
|E_INVALIDARG|`szDebuggeeVersion`ou `ppCordb` é nulo, ou a seqüência de versão está incorreta.|  
  
## <a name="remarks"></a>Comentários  
 O `szDebuggeeVersion` parâmetro mapeia a versão correspondente de MSCorDbi.dll.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
