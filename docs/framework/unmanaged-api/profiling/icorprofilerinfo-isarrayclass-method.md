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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f34fee19c796f65d315fcbd26d55e1d5322303a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453022"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>Método ICorProfilerInfo::IsArrayClass
Determina se a classe especificada é uma classe de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID da classe a ser examinado.  
  
 `pBaseElemType`  
 [out] Um ponteiro para um valor da enumeração CorElementType que indica o tipo dos elementos da matriz.  
  
 `pBaseClassId`  
 [out] Um ponteiro para a ID da classe dos elementos da matriz, quando disponível.  
  
 `pcRank`  
 [out] Um ponteiro para um inteiro que indica a classificação (ou seja, o número de dimensões) da matriz.  
  
## <a name="remarks"></a>Comentários  
 Se a classe especificada é uma classe de matriz, o `IsArrayClass` método retorna um HRESULT S_OK e valores para os parâmetros de saída não nulo. Caso contrário, ela retornará S_FALSE.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
