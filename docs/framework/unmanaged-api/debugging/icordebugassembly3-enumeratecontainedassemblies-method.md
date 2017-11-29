---
title: "Método ICorDebugAssembly3::EnumerateContainedAssemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b927d065f26a13d496aec8cd6c8cbc69cf3a8bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
