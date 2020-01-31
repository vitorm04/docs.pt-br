---
title: 'Método ICorDebugMergedAssemblyRecord:: GetVersion'
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 8b5995183be7f1c992cf3230e16456cb248eff0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793074"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>Método ICorDebugMergedAssemblyRecord:: GetVersion
Obtém as informações de versão do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pMajor`  
 fora Um ponteiro para o número de versão principal.  
  
 `pMinor`  
 fora Um ponteiro para o número de versão secundária.  
  
 `pBuild`  
 fora Um ponteiro para o número da compilação.  
  
 `pRevision`  
 fora Um ponteiro para o número de revisão.  
  
## <a name="remarks"></a>Comentários  
 Para obter informações sobre números de versão do assembly, consulte o tópico <xref:System.Version> classe.  
  
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
