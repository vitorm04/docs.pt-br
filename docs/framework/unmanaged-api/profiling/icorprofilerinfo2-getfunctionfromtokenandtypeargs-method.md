---
title: "Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b225b87eab6e65055618c8b6659459637e8a01be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>Método ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
Obtém o `FunctionID` de uma função usando o token de metadados especificado, que contém a classe, e `ClassID` valores de quaisquer argumentos de tipo.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `moduleID`  
 [in] A ID do módulo no qual a função reside.  
  
 `funcDef`  
 [in] Um `mdMethodDef` token de metadados que faz referência à função.  
  
 `classId`  
 [in] A ID de classe da função.  
  
 `cTypeArgs`  
 [in] O número de parâmetros de tipo para a função determinada. Esse valor deve ser zero para funções não genérico.  
  
 `typeArgs`  
 [in] Uma matriz de `ClassID` valores, cada um deles é um argumento da função. O valor de `typeArgs` pode ser NULL se `cTypeArgs` está definido como zero.  
  
 `pFunctionID`  
 [out] Um ponteiro para o `FunctionID` da função especificada.  
  
## <a name="remarks"></a>Comentários  
 Chamando o `GetFunctionFromTokenAndTypeArgs` método com um `mdMethodRef` metadados em vez de um `mdMethodDef` token de metadados pode ter resultados imprevisíveis. Os chamadores devem resolver o `mdMethodRef` para um `mdMethodDef` ao transmiti-lo.  
  
 Se a função ainda não foi carregada, chamando `GetFunctionFromTokenAndTypeArgs` fará com que o carregamento ocorra, que é uma operação perigosa em vários contextos. Por exemplo, chamar esse método durante o carregamento dos módulos ou tipos pode causar um loop infinito que o tempo de execução tenta carregar circularmente as coisas.  
  
 Em geral, uso de `GetFunctionFromTokenAndTypeArgs` não é recomendado. Se os criadores de perfil estiver interessados em eventos para uma função específica, deve armazenar o `ModuleID` e `mdMethodDef` dessa função e use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) para verificar se um determinado `FunctionID` é o que a função desejada.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
