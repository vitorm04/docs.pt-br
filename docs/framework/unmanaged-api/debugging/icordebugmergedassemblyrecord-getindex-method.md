---
title: 'Método ICorDebugMergedAssemblyRecord:: GetIndex'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: c8fb5ace27fbf7fbebdaca5822af99cd6673e8cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793135"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a>Método ICorDebugMergedAssemblyRecord:: GetIndex
Obtém o índice de prefixo do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pIndex`  
 fora Um ponteiro para o índice de prefixo.  
  
## <a name="remarks"></a>Comentários  
 O índice de prefixo é usado para evitar colisões de nome nos nomes de tipos de metadados mesclados.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
