---
title: "Método ICorDebugMergedAssemblyRecord::GetCulture"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7791491a050e31d8d6c5dfb6ef9ffe209921753d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>Método ICorDebugMergedAssemblyRecord::GetCulture
Obtém a cadeia de caracteres de nome de cultura do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cchCulture`  
 [in] O número de caracteres a `szCulture` buffer.  
  
 `pcchCulture`  
 [out] O número de caracteres gravados o `szCulture` buffer.  
  
 `szCulture`  
 [out] Uma matriz de caracteres que contém o nome de cultura.  
  
## <a name="remarks"></a>Comentários  
 O nome de cultura é uma cadeia de caracteres exclusiva que identifica uma cultura, como "en-US" (para a cultura do inglês (Estados Unidos)) ou "neutral" (para uma cultura neutra).  
  
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
