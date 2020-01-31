---
title: Método ICorDebugInternalFrame2::IsCloserToLeaf
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
ms.openlocfilehash: 5dd93dcc29ace6573e313f732c45af0dfbb900e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782222"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>Método ICorDebugInternalFrame2::IsCloserToLeaf
Verifica se o quadro interno `this` está mais próximo da folha do que o objeto ICorDebugFrame especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFrameToCompare`  
 no Um ponteiro para a comparação `ICorDebugFrame` objeto.  
  
 `pIsCloser`  
 [fora] `true` se o quadro interno `this` está mais próximo da folha do que o quadro especificado por `pFrameToCompare`; caso contrário, `false`.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A comparação foi executada com êxito.|  
|{1&gt;E_FAIL&lt;1}|Não foi possível executar a comparação.|  
|{1&gt;E_INVALIDARG&lt;1}|`pFrameToCompare` ou `pIsCloser` é nulo.|  
  
## <a name="remarks"></a>Comentários  
 `IsCloserToLeaf` pode ser usado para implementar uma política para intercalar quadros internos com outros quadros na pilha.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
- [Depuração](index.md)
