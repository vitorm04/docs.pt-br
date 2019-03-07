---
title: Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c069cb375e9cb6011e7e91041d13736f5ef88dfd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482438"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
Obtém o `FunctionID` de uma função usando o token de metadados especificado, que contém a classe, e `ClassID` valores de qualquer tipo de argumentos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleID`  
 [in] A ID do módulo no qual a função reside.  
  
 `funcDef`  
 [in] Um `mdMethodDef` token de metadados que faz referência à função.  
  
 `classId`  
 [in] A ID de classe da função.  
  
 `cTypeArgs`  
 [in] O número de parâmetros de tipo para a função determinada. Esse valor deve ser zero para funções não genéricos.  
  
 `typeArgs`  
 [in] Uma matriz de `ClassID` valores, cada um deles é um argumento da função. O valor de `typeArgs` pode ser NULL se `cTypeArgs` é definido como zero.  
  
 `pFunctionID`  
 [out] Um ponteiro para o `FunctionID` da função especificada.  
  
## <a name="remarks"></a>Comentários  
 Chamar o `GetFunctionFromTokenAndTypeArgs` método com um `mdMethodRef` metadados, em vez de um `mdMethodDef` token de metadados pode ter resultados imprevisíveis. Os chamadores devem resolver o `mdMethodRef` para um `mdMethodDef` ao passá-la.  
  
 Se a função ainda não foi carregada, chamando `GetFunctionFromTokenAndTypeArgs` fará com que o carregamento ocorra, o que é uma operação perigosa em vários contextos. Por exemplo, chamar esse método durante o carregamento de módulos ou tipos de poderia levar a um loop infinito como o tempo de execução tenta carregar circularmente as coisas.  
  
 Em geral, use de `GetFunctionFromTokenAndTypeArgs` não é recomendado. Se os criadores de perfis estiver interessados em eventos para uma função específica, eles devem armazenar o `ModuleID` e `mdMethodDef` dessa função, e use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) para verificar se um determinado `FunctionID` é o que a função desejada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
