---
title: Método ICorProfilerInfo2::GetBoxClassLayout
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
ms.openlocfilehash: 500cf74c320438fc1b78f0aac737b418716e1a11
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862822"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a>Método ICorProfilerInfo2::GetBoxClassLayout
Obtém informações sobre onde o tipo de valor especificado está localizado quando ele está em caixa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no A ID da classe que descreve o tipo de valor que está em caixa.  
  
 `pBufferOffset`  
 fora Um inteiro que é o deslocamento, relativo ao ponteiro da ID do objeto em caixa, do tipo de valor.  
  
## <a name="remarks"></a>Comentários  
 O valor de `pBufferOffset` é o local do tipo de valor dentro de uma caixa. Depois que `pBufferOffset` é aplicado a um objeto em caixa, o layout de classe do tipo de valor pode ser usado para interpretar o valor do objeto.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
