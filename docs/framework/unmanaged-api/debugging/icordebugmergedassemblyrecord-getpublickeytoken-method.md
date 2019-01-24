---
title: Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f77871c8547f250d4b46c11c1a0be25b6ef68a88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581922"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken
Obtém o token de chave pública do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cbPublicKeyToken`  
 [in] O número máximo de bytes no `pbPublicKeyToken` matriz.  
  
 `pcbPublicKeyToken`  
 [out] Um ponteiro para o número real de bytes gravados para o `pbPublicKeyToken` matriz.  
  
 `pbPublicKeyToken`  
 [out] Um ponteiro para uma matriz de bytes que contém o token de chave pública do assembly.  
  
## <a name="remarks"></a>Comentários  
 O token de chave pública do assembly é os último oito bytes de um hash SHA1 de sua chave pública.  
  
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
