---
title: ICorDebugMergeDRecord::GetPublicKeyToken Method
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 79df5c3e8b07879a26272f595664abab011101bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178719"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>ICorDebugMergeDRecord::GetPublicKeyToken Method
Recebe o símbolo da chave pública da assembléia.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cbPublicKeyToken`  
 [em] O número máximo de bytes na `pbPublicKeyToken` matriz.  
  
 `pcbPublicKeyToken`  
 [fora] Um ponteiro para o número real de `pbPublicKeyToken` bytes escritos para a matriz.  
  
 `pbPublicKeyToken`  
 [fora] Um ponteiro para uma matriz de bytes que contém o token de chave pública da montagem.  
  
## <a name="remarks"></a>Comentários  
 O símbolo de chave pública de uma assembléia é o último oito bytes de um hash SHA1 de sua chave pública.  
  
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
