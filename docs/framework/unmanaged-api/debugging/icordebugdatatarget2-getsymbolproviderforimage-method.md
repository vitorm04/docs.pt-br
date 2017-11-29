---
title: "Método ICorDebugDataTarget2::GetSymbolProviderForImage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 868e1e8d670a438d7a93bfac27f213c9c35ea58c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a>Método ICorDebugDataTarget2::GetSymbolProviderForImage
Retorna o provedor de símbolo para um módulo do endereço base do módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `imageBaseAddress`  
 [in] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base de um módulo.  
  
 `ppSymProvider`  
 [out] Um ponteiro para o endereço de um [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) objeto.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
