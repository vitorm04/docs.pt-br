---
title: 'Método ICorDebugStaticFieldSymbol:: GetAddress'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: be4d59fe668026c4b40be4c6d0afcf718c8157bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791843"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a>Método ICorDebugStaticFieldSymbol:: GetAddress
Obtém o endereço de um campo estático.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pRVA  
 fora Um ponteiro para o endereço virtual relativo (RVA) do campo estático.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
