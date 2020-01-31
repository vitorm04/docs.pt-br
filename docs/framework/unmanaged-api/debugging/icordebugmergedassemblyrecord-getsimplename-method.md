---
title: 'Método ICorDebugMergedAssemblyRecord:: getsimplesname'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 21e8ebeabd3b082361ca3307240cfca58835b066
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793088"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>Método ICorDebugMergedAssemblyRecord:: getsimplesname
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
 no O número de caracteres no buffer de `szName`.  
  
 `pcchName`  
 fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.  
  
 `szName`  
 Um ponteiro para uma matriz de caracteres.  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera o nome simples de um assembly (como "System. Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública. Ele corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> no código gerenciado.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
