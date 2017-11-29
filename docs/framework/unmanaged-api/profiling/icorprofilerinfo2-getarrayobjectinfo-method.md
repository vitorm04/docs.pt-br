---
title: "Método ICorProfilerInfo2::GetArrayObjectInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetArrayObjectInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a1e0c986286483f8236de3a1c73f043691820d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>Método ICorProfilerInfo2::GetArrayObjectInfo
Obtém informações detalhadas sobre um objeto de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `objectId`  
 [in] A ID de um objeto de matriz válida.  
  
 `cDimensions`  
 [in] A classificação (número de dimensões) da matriz.  
  
 `pDimensionSizes`  
 [out] Uma matriz que contém números inteiros, cada um representando o tamanho de uma dimensão da matriz.  
  
 `pDimensionLowerBounds`  
 [out] Uma matriz que contém números inteiros, cada um representando o inferior associado de uma dimensão da matriz.  
  
 `ppData`  
 [out] Um ponteiro para o endereço do buffer bruto para a matriz, que é organizada de acordo com a convenção de C++.  
  
## <a name="remarks"></a>Comentários  
 O `pDimensionSizes` e `pDimensionLowerBounds` são paralelas matrizes, portanto os elementos localizados no mesmo índice em cada matriz são características da mesma entidade.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
