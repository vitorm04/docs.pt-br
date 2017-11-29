---
title: "Método ICorDebugVariableSymbol::GetSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ea4a77b08b12c3f067d51f9dfe2c961192c3354
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetsize-method"></a>Método ICorDebugVariableSymbol::GetSize
Obtém o tamanho de uma variável em bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcbValue`  
 Um ponteiro para um inteiro não assinado de 32 bits que contém o tamanho da variável.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
