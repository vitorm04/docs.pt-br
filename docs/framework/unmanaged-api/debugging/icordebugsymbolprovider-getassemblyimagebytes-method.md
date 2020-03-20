---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes Method
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 6361b12802876ef480acbe1cc13f32b77ba0be49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178488"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a>ICorDebugSymbolProvider::GetAssemblyImageBytes Method
Lê dados de um conjunto mesclado dado um endereço virtual relativo (RVA) no conjunto mesclado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `rva`  
 [em] Um endereço virtual relativo (RVA) em um conjunto mesclado.  
  
 `length`  
 O número de bytes a serem lidos da montagem fundida.  
  
 `ppMemoryBuffer`  
 Um ponteiro para o endereço de um objeto [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) que contém informações sobre o buffer de memória com metadados de montagem mesclados.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Este método está disponível apenas com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
