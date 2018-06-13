---
title: Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04be252092732296354cfec102cf8fe648ed2dd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456632"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
Obtém o `ClassID` de um tipo usando o token de metadados especificado e o `ClassID` valores de quaisquer argumentos de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleID`  
 [in] A ID do módulo no qual reside o tipo.  
  
 `typeDef`  
 [in] Um `mdTypeDef` token de metadados que faz referência ao tipo.  
  
 `cTypeArgs`  
 [in] O número de parâmetros de tipo para o tipo especificado. Esse valor deve ser zero para tipos não genérico.  
  
 `typeArgs`  
 [in] Uma matriz de `ClassID` valores, cada um deles é um argumento do tipo. O valor de `typeArgs` pode ser NULL se `cTypeArgs` está definido como zero.  
  
 `pClassID`  
 [out] Um ponteiro para o `ClassID` do tipo especificado.  
  
## <a name="remarks"></a>Comentários  
 Chamando o `GetClassFromTokenAndTypeArgs` método com um `mdTypeRef` em vez de um `mdTypeDef` token de metadados pode ter resultados imprevisíveis; chamadores devem resolver o `mdTypeRef` para um `mdTypeDef` ao transmiti-lo.  
  
 Se o tipo já não estiver carregado, chamando `GetClassFromTokenAndTypeArgs` irá disparar o carregamento, o que é uma operação perigosa em vários contextos. Por exemplo, chamar esse método durante o carregamento dos módulos ou outros tipos pode causar um loop infinito que o tempo de execução tenta carregar circularmente as coisas.  
  
 Em geral, uso de `GetClassFromTokenAndTypeArgs` não é recomendado. Se os criadores de perfil estiver interessados em eventos para um tipo específico, deve armazenar o `ModuleID` e `mdTypeDef` do tipo e use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) para verificar se um determinado `ClassID` é do tipo desejado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
