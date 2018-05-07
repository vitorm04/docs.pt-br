---
title: Método ICorDebugVirtualUnwinder::Next
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4bacbd9ef11f6f6cb6d9952290c00f1b8ce50aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvirtualunwindernext-method"></a>Método ICorDebugVirtualUnwinder::Next
Avança para o contexto do chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se o desenrolamento ocorreu com êxito, ou `CORDBG_S_AT_END_OF_STACK` se o desenrolamento não pode ser concluído porque não há nenhum quadro mais.  
  
 Se uma falha de HRESULT é retornado, ICorDebug APIs retornarão `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Comentários  
 O movimentador de pilha deve garantir que ele faz assim que eventualmente progresso, uma chamada para `Next` retornará uma falha HRESULT ou `CORDBG_S_AT_END_OF_STACK`. Retornando `S_OK` indefinidamente pode causar um loop infinito.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
