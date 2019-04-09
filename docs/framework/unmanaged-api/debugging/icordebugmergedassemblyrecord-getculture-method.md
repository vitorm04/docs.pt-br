---
title: Método ICorDebugMergedAssemblyRecord::GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 093b21a439b96c9fe2f971300f314d1b75527f1f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207195"
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
  
## <a name="parameters"></a>Parâmetros  
 `cchCulture`  
 [in] O número de caracteres no `szCulture` buffer.  
  
 `pcchCulture`  
 [out] O número de caracteres gravados, na verdade, o `szCulture` buffer.  
  
 `szCulture`  
 [out] Uma matriz de caracteres que contém o nome da cultura.  
  
## <a name="remarks"></a>Comentários  
 O nome de cultura é uma cadeia de caracteres exclusiva que identifica uma cultura, como "en-US" (para a cultura do inglês (Estados Unidos)) ou "neutral" (para uma cultura neutra).  
  
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
