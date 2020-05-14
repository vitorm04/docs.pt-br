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
ms.openlocfilehash: 0e480db953131d7771e493a8f367154a7d17dada
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396636"
---
# <a name="icordebugtype2-interface"></a>Interface ICorDebugType2
Estende a interface ICorDebugType para recuperar o identificador de tipo de um tipo base ou tipo complexo (definido pelo usuário).  
  
## <a name="methods"></a>Métodos  
  
|Método||  
|------------|-|  
|[Método GetTypeID](icordebugtype2-gettypeid-method.md)|Obtém um [COR_TYPEID](cor-typeid-structure.md) para este tipo.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é uma extensão lógica da interface ICorDebugType.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="example"></a>Exemplo  
 O fragmento de código a seguir ilustra o uso do método [ICorDebugType2:: GetTypeId](icordebugtype2-gettypeid-method.md) .  
  
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
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
