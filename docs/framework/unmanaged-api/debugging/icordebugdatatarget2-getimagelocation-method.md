---
title: Método ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: ba1cc8c91c53547c6ed4025ee67a69e253f3596d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783578"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a>Método ICorDebugDataTarget2::GetImageLocation
Retorna o caminho de um módulo de endereço base do módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `baseAddress`  
 no Um valor [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o endereço base do módulo.  
  
 `cchName`  
 [in] O número de caracteres no buffer que receberá o caminho do módulo.  
  
 `pcchName`  
 [out] Um ponteiro para o número de caracteres gravados para o buffer `szName`.  
  
 `szName`  
 [out] O caminho do módulo.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugDataTarget2](icordebugdatatarget2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
