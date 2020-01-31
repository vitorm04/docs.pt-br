---
title: 'Método ICorDebugVariableSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 172eea452442aa94ea010e2c434908ab8d040a93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790919"
---
# <a name="icordebugvariablesymbolgetname-method"></a>Método ICorDebugVariableSymbol:: GetName
Obtém o nome de uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 no O número de caracteres no buffer de `szName`.  
  
 `pcchName`  
 fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.  
  
 `szName`  
 Um ponteiro para uma matriz de caracteres que contém o nome da variável.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
