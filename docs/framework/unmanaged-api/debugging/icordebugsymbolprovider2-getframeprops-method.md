---
title: 'Método ICorDebugSymbolProvider2:: GetFrameProps'
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: dc64152938c46945978715251286ecb6c6d8983c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791517"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a>Método ICorDebugSymbolProvider2:: GetFrameProps
Retorna o método iniciando o endereço virtual relativo de um método e o quadro pai, dado um endereço virtual relativo de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `codeRva`  
 no Um endereço virtual relativo ao código.  
  
 `pCodeStartRva`  
 fora Um ponteiro para o endereço virtual relativo inicial do método.  
  
 `pParentFrameStartRva`  
 fora Um ponteiro para o endereço virtual relativo inicial do quadro.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
