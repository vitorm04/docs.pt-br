---
title: Interface ICorDebugType2
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2f2c1e4c95c61eab4c9da6103d4ac479b4bbdb4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936050"
---
# <a name="icordebugtype2-interface"></a>Interface ICorDebugType2
Estende a interface ICorDebugType para recuperar o identificador de tipo de um tipo base ou tipo complexo (definido pelo usuário).  
  
## <a name="methods"></a>Métodos  
  
|Método||  
|------------|-|  
|[Método GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Obtém um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para este tipo.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é uma extensão lógica da interface ICorDebugType.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="example"></a>Exemplo  
 O fragmento de código a seguir ilustra o uso do método [ICorDebugType2::](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) GetTypeId.  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
