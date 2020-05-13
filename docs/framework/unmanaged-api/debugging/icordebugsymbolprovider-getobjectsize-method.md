---
title: 'Método ICorDebugSymbolProvider:: getobjectize'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 64324df49ad0b5dfa3c25455950bddc3d687b178
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379550"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a>Método ICorDebugSymbolProvider:: getobjectize
Retorna o tamanho do objeto de um objeto com base em sua assinatura de TypeSpec.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cbSignature`  
 no O número de bytes na assinatura TypeSpec.  
  
 typeSig  
 no A assinatura TypeSpec.  
  
 `pObjectSize`  
 fora Um ponteiro para o tamanho do objeto.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
