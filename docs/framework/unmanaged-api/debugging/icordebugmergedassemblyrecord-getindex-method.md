---
title: Método ICorDebugMergedAssemblyRecord::GetIndex
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0bcb5cdb4e93ae8ce6981bd86f125ecccb7d732
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a>Método ICorDebugMergedAssemblyRecord::GetIndex
Obtém o índice do prefixo do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pIndex`  
 [out] Um ponteiro para o índice de prefixo.  
  
## <a name="remarks"></a>Comentários  
 O índice de prefixo é usado para evitar colisões de nome nos nomes de tipo de metadados mesclada.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
