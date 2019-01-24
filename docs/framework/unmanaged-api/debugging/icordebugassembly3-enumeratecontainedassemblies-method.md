---
title: Método ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa99e7289e0e86032f7bb85bbe209932f5c50d16
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627571"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>Método ICorDebugAssembly3::EnumerateContainedAssemblies
Obtém um enumerador para os assemblies contidos neste assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppAssemblies`  
 [out] Um ponteiro para o endereço de um objeto de interface ICorDebugAssemblyEnum que é o enumerador.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se este objeto `ICorDebugAssembly3` for um contêiner; caso contrário, `S_FALSE`, e a enumeração está vazia.  
  
## <a name="remarks"></a>Comentários  
 Símbolos são necessários para enumerar os assemblies contidos. Se eles não estiverem presentes, o método retorna `S_FALSE`, e nenhum enumerador válido é fornecido.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
