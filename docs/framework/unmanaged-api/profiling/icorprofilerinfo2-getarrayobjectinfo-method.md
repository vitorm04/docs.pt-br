---
title: Método ICorProfilerInfo2::GetArrayObjectInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: 839cd574e5352b74b47cd6242d5706bc6405d439
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862900"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>Método ICorProfilerInfo2::GetArrayObjectInfo
Obtém informações detalhadas sobre um objeto de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectId`  
 no A ID de um objeto de matriz válido.  
  
 `cDimensions`  
 no A classificação (número de dimensões) da matriz.  
  
 `pDimensionSizes`  
 fora Uma matriz que contém inteiros, cada um representando o tamanho de uma dimensão da matriz.  
  
 `pDimensionLowerBounds`  
 fora Uma matriz que contém inteiros, cada um representando o limite inferior de uma dimensão da matriz.  
  
 `ppData`  
 fora Um ponteiro para o endereço do buffer bruto para a matriz, que é disposta de acordo com a C++ Convenção.  
  
## <a name="remarks"></a>Comentários  
 Os `pDimensionSizes` e `pDimensionLowerBounds` são matrizes paralelas, portanto, os elementos localizados no mesmo índice em cada matriz são características da mesma entidade.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
