---
title: ICorDebugMergeDRecord::GetVersion Method
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178680"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergeDRecord::GetVersion Method
Obtém informações da versão da assembléia.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pMajor`  
 [fora] Um ponteiro para o número da versão principal.  
  
 `pMinor`  
 [fora] Um ponteiro para o número da versão menor.  
  
 `pBuild`  
 [fora] Um ponteiro para o número de compilação.  
  
 `pRevision`  
 [fora] Um ponteiro para o número de revisão.  
  
## <a name="remarks"></a>Comentários  
 Para obter informações sobre números <xref:System.Version> de versão de montagem, consulte o tópico da classe.  
  
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
