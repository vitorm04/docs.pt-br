---
title: ICorDebugArrayValue Interface1
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
ms.openlocfilehash: 7b8e9e9c9f43b45bf4f5d65bf80394c0fcd71325
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559262"
---
# <a name="icordebugarrayvalue-interface1"></a>ICorDebugArrayValue Interface1
Uma subclasse de ICorDebugHeapValue que representa uma matriz unidimensional ou multidimensional.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetBaseIndicies](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Obtém o índice de base de cada dimensão da matriz.|  
|[Método GetCount](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Obtém o número total de elementos na matriz.|  
|[Método GetDimensions](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Obtém as dimensões da matriz.|  
|[Método GetElement](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Obtém um valor que representa o elemento especificado na matriz.|  
|[Método GetElementAtPosition](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Obtém o elemento na posição determinada, tratando da matriz como uma matriz unidimensional de base zero.|  
|[Método GetElementType](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Obtém o tipo simples dos elementos na matriz.|  
|[Método GetRank](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Obtém o número de dimensões na matriz.|  
|[Método HasBaseIndicies](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Determina se a matriz tem índices de base.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugArrayValue` dá suporte a matrizes unidimensionais e multidimensionais.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
