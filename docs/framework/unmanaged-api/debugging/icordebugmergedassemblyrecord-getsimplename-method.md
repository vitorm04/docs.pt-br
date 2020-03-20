---
title: ICorDebugMergeDRecord::GetSimpleName Method
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178713"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergeDRecord::GetSimpleName Method
Fica com o nome simples da assembléia.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `cchName`  
 [em] O número de `szName` caracteres no buffer.  
  
 `pcchName`  
 [fora] Um ponteiro para o número de `szName` caracteres realmente escrito no buffer.  
  
 `szName`  
 Um ponteiro para uma matriz de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Este método recupera o nome simples de um conjunto (como "System.Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública. Corresponde à <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> propriedade em código gerenciado.  
  
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
