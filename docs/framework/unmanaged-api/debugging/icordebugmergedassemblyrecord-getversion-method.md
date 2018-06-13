---
title: Método ICorDebugMergedAssemblyRecord::GetVersion
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb206d1bf39307852dd317613eb81028b777514d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414593"
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
  
#### <a name="parameters"></a>Parâmetros  
 `pMajor`  
 [out] Um ponteiro para o número de versão principal.  
  
 `pMinor`  
 [out] Um ponteiro para o número de versão secundária.  
  
 `pBuild`  
 [out] Um ponteiro para o número de compilação.  
  
 `pRevision`  
 [out] Um ponteiro para o número de revisão.  
  
## <a name="remarks"></a>Comentários  
 Para obter informações sobre números de versão do assembly, consulte o <xref:System.Version> tópico sobre a classe.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
