---
title: "Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c286981def6f12f8e5b8fa5397f23535d4d4623
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a>Método ICorDebugMergedAssemblyRecord::GetPublicKeyToken
Obtém a chave pública do assembly token.  
  
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
 [in] O número máximo de bytes a `pbPublicKeyToken` matriz.  
  
 `pcbPublicKeyToken`  
 [out] Um ponteiro para o número real de bytes gravados para o `pbPublicKeyToken` matriz.  
  
 `pbPublicKeyToken`  
 [out] Um ponteiro para uma matriz de bytes que contém o token de chave pública do assembly.  
  
## <a name="remarks"></a>Comentários  
 Token de chave pública de um assembly é o último oito bytes de um hash SHA1 de sua chave pública.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
