---
title: 'Método ICorDebugMergedAssemblyRecord:: GetPublicKeyToken'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 4cd0ff788401a7b5d70e215209194c0eb6cad1f8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212107"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>Método ICorDebugMergedAssemblyRecord:: GetPublicKeyToken
Obtém o token de chave pública do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cbPublicKeyToken`  
 no O número máximo de bytes na `pbPublicKeyToken` matriz.  
  
 `pcbPublicKeyToken`  
 fora Um ponteiro para o número real de bytes gravados na `pbPublicKeyToken` matriz.  
  
 `pbPublicKeyToken`  
 fora Um ponteiro para uma matriz de bytes que contém o token de chave pública do assembly.  
  
## <a name="remarks"></a>Comentários  
 O token de chave pública de um assembly são os últimos oito bytes de um hash SHA1 de sua chave pública.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
