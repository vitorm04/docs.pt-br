---
title: 'Método ICorDebugMergedAssemblyRecord:: GetPublicKeyToken'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 543083703cd0cbbce9dc0660383713202fa2f0b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793100"
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
 no O número máximo de bytes na matriz de `pbPublicKeyToken`.  
  
 `pcbPublicKeyToken`  
 fora Um ponteiro para o número real de bytes gravados na matriz de `pbPublicKeyToken`.  
  
 `pbPublicKeyToken`  
 fora Um ponteiro para uma matriz de bytes que contém o token de chave pública do assembly.  
  
## <a name="remarks"></a>Comentários  
 O token de chave pública de um assembly são os últimos oito bytes de um hash SHA1 de sua chave pública.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
