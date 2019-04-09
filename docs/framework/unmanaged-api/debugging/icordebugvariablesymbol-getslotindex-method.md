---
title: Método ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138782"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>Método ICorDebugVariableSymbol::GetSlotIndex
Obtém o índice de slot gerenciado de uma variável local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pSlotIndex`  
 [out] Um ponteiro para o índice de slot da variável local.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se for bem-sucedido. `E_FAIL` Se a variável é um argumento de função.  
  
## <a name="remarks"></a>Comentários  
 O índice de slot gerenciado de uma variável local pode ser usado para recuperar informações de metadados da variável  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
