---
title: iCorDebugStaticFieldSymbol::Método GetName
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178511"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a>iCorDebugStaticFieldSymbol::Método GetName
Obtém o nome do campo estático.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cchName`  
 [em] O número de `szName` caracteres no buffer.  
  
 `pcchName`  
 [fora] Um ponteiro para o número de `szName` caracteres realmente escrito no buffer.  
  
 `szName`  
 [fora] Uma matriz de caracteres que armazena o nome retornado.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Este método está disponível apenas com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
