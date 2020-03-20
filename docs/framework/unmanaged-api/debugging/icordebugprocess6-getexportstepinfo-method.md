---
title: Método ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178525"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>Método ICorDebugProcess6::GetExportStepInfo
Fornece informações sobre funções exportadas de runtime para ajudar a percorrer o código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>parâmetros  
 pszExportName  
 [in] O nome de uma função de exportação de runtime gravada na tabela de exportação PE.  
  
 invokeKind  
 [fora] Um ponteiro para um membro da enumeração [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) que descreve como a função exportada invocará código gerenciado.  
  
 invokePurpose  
 [fora] Um ponteiro para um membro da enumeração [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) que descreve por que a função exportada chamará código gerenciado.  
  
## <a name="return-value"></a>Valor retornado  
 O método pode retornar os valores listados na tabela a seguir.  
  
|Valor retornado|Descrição|  
|------------------|-----------------|  
|`S_OK`|A chamada de método foi bem-sucedida.|  
|`E_POINTER`|`pInvokeKind`ou `pInvokePurpose` é **nulo.**|  
|Outros valores `HRESULT` com falha.|Conforme apropriado.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Este método está disponível apenas com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugProcess6](icordebugprocess6-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
