---
title: Método ICorProfilerInfo::IsArrayClass
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 57515ac4670b9b7e25bb496851347a62e1b246df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438717"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>Método ICorProfilerInfo::IsArrayClass
Determina se a classe especificada é uma classe de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no A ID da classe a ser examinada.  
  
 `pBaseElemType`  
 fora Um ponteiro para um valor da enumeração CorElementType que indica o tipo dos elementos da matriz.  
  
 `pBaseClassId`  
 fora Um ponteiro para a ID de classe dos elementos da matriz, quando disponível.  
  
 `pcRank`  
 fora Um ponteiro para um inteiro que indica a classificação (ou seja, o número de dimensões) da matriz.  
  
## <a name="remarks"></a>Comentários  
 Se a classe especificada for uma classe de matriz, o método `IsArrayClass` retornará um S_OK HRESULT e os valores para quaisquer parâmetros de saída não nulos. Caso contrário, ele retornará S_FALSE.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
