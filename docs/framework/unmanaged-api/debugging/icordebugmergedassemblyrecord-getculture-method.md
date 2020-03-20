---
title: ICorDebugMergeDRecord::Método GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178746"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergeDRecord::Método GetCulture
Fica a seqüência de nomes de cultura da assembléia.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cchCulture`  
 [em] O número de `szCulture` caracteres no buffer.  
  
 `pcchCulture`  
 [fora] O número de caracteres `szCulture` realmente escritos para o buffer.  
  
 `szCulture`  
 [fora] Uma matriz de caracteres que contém o nome da cultura.  
  
## <a name="remarks"></a>Comentários  
 O nome da cultura é uma cadeia única que identifica uma cultura, como "en-US" (para a cultura inglesa (Estados Unidos) ou "neutra" (para uma cultura neutra).  
  
> [!NOTE]
> Este método está disponível apenas com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
