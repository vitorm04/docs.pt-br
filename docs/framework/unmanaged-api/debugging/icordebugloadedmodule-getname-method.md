---
title: Método ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 628f85f3045533ead7ace47b11573a0b1a46df46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782043"
---
# <a name="icordebugloadedmodulegetname-method"></a>Método ICorDebugLoadedModule::GetName
Obtém o nome do módulo carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 no O número de caracteres no buffer de `szName`.  
  
 `pcchName`  
 fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.  
  
 `szName`  
 fora Uma matriz de caracteres que contém o nome do módulo carregado.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugLoadedModule](icordebugloadedmodule-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
