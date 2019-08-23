---
title: Interface ICorDebugArrayValue
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99bd3e9ae1faec1b71933681fadf4816b4789c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952216"
---
# <a name="icordebugarrayvalue-interface"></a>Interface ICorDebugArrayValue

Uma subclasse de ICorDebugHeapValue que representa uma matriz unidimensional ou multidimensional.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetBaseIndicies](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Obtém o índice base de cada dimensão na matriz.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Obtém o número total de elementos na matriz.|  
|[Método GetDimensions](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Obtém as dimensões da matriz.|  
|[Método GetElement](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Obtém um valor que representa o elemento fornecido na matriz.|  
|[Método GetElementAtPosition](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Obtém o elemento na posição fornecida, tratando a matriz como uma matriz unidimensional com base em zero.|  
|[Método GetElementType](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Obtém o tipo simples dos elementos na matriz.|  
|[Método GetRank](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Obtém o número de dimensões na matriz.|  
|[Método HasBaseIndicies](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Determina se a matriz tem índices base.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugArrayValue`dá suporte a matrizes unidimensionais e multidimensionais.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
