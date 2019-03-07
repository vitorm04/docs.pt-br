---
title: Método ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b60bad75cb6286bda026e5b67e0a4fa8e2347dd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487143"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>Método ICorDebugProcess6::GetExportStepInfo
Fornece informações sobre funções exportadas de tempo de execução para ajudar a percorrer o código gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pszExportName  
 [in] O nome de uma função de exportação de tempo de execução gravada na tabela de exportação PE.  
  
 invokeKind  
 [out] Um ponteiro para um membro do [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) enumeração que descreve como a função exportada invocará o código gerenciado.  
  
 invokePurpose  
 [out] Um ponteiro para um membro do [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) enumeração que descreve por que a função exportada chamará o código gerenciado.  
  
## <a name="return-value"></a>Valor de retorno  
 O método pode retornar os valores listados na tabela a seguir.  
  
|Valor de retorno|Descrição|  
|------------------|-----------------|  
|`S_OK`|A chamada de método foi bem-sucedida.|  
|`E_POINTER`|`pInvokeKind` ou `pInvokePurpose` está **nulo**.|  
|Outros valores `HRESULT` com falha.|Conforme apropriado.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
