---
title: Método ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36cf8647b3caafeaae2db3c2fd53471496e922fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666932"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>Método ICorDebugMergedAssemblyRecord::GetVersion
Obtém informações de versão do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pMajor`  
 [out] Um ponteiro para o número de versão principal.  
  
 `pMinor`  
 [out] Um ponteiro para o número de versão secundária.  
  
 `pBuild`  
 [out] Um ponteiro para o número da compilação.  
  
 `pRevision`  
 [out] Um ponteiro para o número de revisão.  
  
## <a name="remarks"></a>Comentários  
 Para obter informações sobre números de versão do assembly, consulte o <xref:System.Version> tópico da classe.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
