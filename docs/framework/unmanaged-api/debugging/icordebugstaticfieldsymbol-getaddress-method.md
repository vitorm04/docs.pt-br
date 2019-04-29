---
title: Método ICorDebugStaticFieldSymbol::GetAddress
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e233fe78f6b2c721114f0307a8ca414625a0087e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782636"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a>Método ICorDebugStaticFieldSymbol::GetAddress
Obtém o endereço de um campo estático.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pRVA  
 [out] Um ponteiro para o endereço virtual relativo (RVA) do campo estático.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
