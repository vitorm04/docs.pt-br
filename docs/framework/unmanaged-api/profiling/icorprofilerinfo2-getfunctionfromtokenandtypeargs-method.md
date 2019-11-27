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
ms.openlocfilehash: 41021a524142afe34727584265aee578e31a64b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433214"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
Obtém a `FunctionID` de uma função usando o token de metadados especificado, contendo a classe e valores de `ClassID` de qualquer argumento de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 no A ID do módulo no qual a função reside.  
  
 `funcDef`  
 no Um `mdMethodDef` token de metadados que faz referência à função.  
  
 `classId`  
 no A ID da classe que contém a função.  
  
 `cTypeArgs`  
 no O número de parâmetros de tipo para a função fornecida. Esse valor deve ser zero para funções não genéricas.  
  
 `typeArgs`  
 no Uma matriz de valores de `ClassID`, cada um dos quais é um argumento da função. O valor de `typeArgs` pode ser nulo se `cTypeArgs` for definido como zero.  
  
 `pFunctionID`  
 fora Um ponteiro para a `FunctionID` da função especificada.  
  
## <a name="remarks"></a>Comentários  
 Chamar o método `GetFunctionFromTokenAndTypeArgs` com um `mdMethodRef` metadados em vez de um token de metadados `mdMethodDef` pode ter resultados imprevisíveis. Os chamadores devem resolver o `mdMethodRef` a um `mdMethodDef` ao passá-lo.  
  
 Se a função ainda não estiver carregada, chamar `GetFunctionFromTokenAndTypeArgs` fará com que o carregamento ocorra, que é uma operação perigosa em muitos contextos. Por exemplo, chamar esse método durante o carregamento de módulos ou tipos pode levar a um loop infinito, pois o tempo de execução tenta carregar as coisas de forma circular.  
  
 Em geral, o uso de `GetFunctionFromTokenAndTypeArgs` não é recomendado. Se os profileres estiverem interessados em eventos para uma função específica, eles deverão armazenar o `ModuleID` e `mdMethodDef` dessa função e usar [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) para verificar se um determinado `FunctionID` é o da função desejada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
