---
title: 'Método ICorDebugMergedAssemblyRecord:: GetPublicKey'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793114"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a>Método ICorDebugMergedAssemblyRecord:: GetPublicKey
Obtém a chave pública do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cbPublicKey`  
 no O número máximo de bytes na matriz de `pbPublicKey`.  
  
 `pcbPublicKey`  
 fora Um ponteiro para o número real de bytes gravados na matriz de `pbPublicKey`.  
  
 `pbPublicKey`  
 fora Um ponteiro para uma matriz de bytes que contém a chave pública do assembly.  
  
## <a name="remarks"></a>Comentários  
  
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
