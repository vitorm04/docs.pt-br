---
title: ICorDebugMergedAssemblyRecord::GetSimpleName Method
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3df84fa7c316d3cd0c97b79478159a5a97ad1e64
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762367"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergedAssemblyRecord::GetSimpleName Method
Obtém o nome simples do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchName`  
 [in] O número de caracteres no `szName` buffer.  
  
 `pcchName`  
 [out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.  
  
 `szName`  
 Um ponteiro para uma matriz de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera o nome simples de um assembly (por exemplo, "System. Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública. Ele corresponde a <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> propriedade no código gerenciado.  
  
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
