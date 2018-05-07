---
title: Método ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb34ac2568ac88797441306820e6e762b5ac46e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>Método ICorDebugAssembly3::GetContainerAssembly
Retorna o assembly do contêiner desse objeto `ICorDebugAssembly3`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppAssembly`  
 Um ponteiro para o endereço de um objeto ICorDebugAssembly que representa o assembly de contêiner, ou **nulo** se a chamada de método falhar.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se a chamada do método for bem-sucedida; Caso contrário, `S_FALSE`, e `ppAssembly` é **nulo**.  
  
## <a name="remarks"></a>Comentários  
 Se esse assembly foi mesclado com outros dentro de um assembly de contêiner único, esse método retorna o assembly do contêiner. Para obter mais informações e terminologia, consulte o [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tópico.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
