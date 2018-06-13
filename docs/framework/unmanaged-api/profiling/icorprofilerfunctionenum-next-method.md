---
title: Método ICorProfilerFunctionEnum::Next
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 30e0dbb6b22c7278c0bc207ae60214a582d35e9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454912"
---
# <a name="icorprofilerfunctionenumnext-method"></a>Método ICorProfilerFunctionEnum::Next
Obtém o número especificado de funções de contíguas de uma coleção sequencial de funções, começando na posição atual do enumerador na sequência.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de funções para recuperar.  
  
 `ids`  
 [out] Uma matriz de `COR_PRF_FUNCTION` valores, cada um deles representa uma função recuperada.  
  
 `pceltFetched`  
 [out] Um ponteiro para o número de funções de fato retornadas no `ids` matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|`celt` elementos foram retornados.|  
|S_FALSE|Menos de `celt` elementos foram retornados, que indica que a enumeração foi concluída.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
