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
ms.openlocfilehash: 0d4d5ec9119cdcf89e507f133288f569e6fb37ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072513"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
Obtém o `ClassID` de um tipo usando o token de metadados especificado e o `ClassID` valores de qualquer tipo de argumentos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleID`  
 [in] A ID do módulo no qual reside o tipo.  
  
 `typeDef`  
 [in] Um `mdTypeDef` token de metadados que faz referência ao tipo.  
  
 `cTypeArgs`  
 [in] O número de parâmetros de tipo para o tipo fornecido. Esse valor deve ser zero para tipos não genéricos.  
  
 `typeArgs`  
 [in] Uma matriz de `ClassID` valores, cada um deles é um argumento do tipo. O valor de `typeArgs` pode ser NULL se `cTypeArgs` é definido como zero.  
  
 `pClassID`  
 [out] Um ponteiro para o `ClassID` do tipo especificado.  
  
## <a name="remarks"></a>Comentários  
 Chamar o `GetClassFromTokenAndTypeArgs` método com um `mdTypeRef` em vez de uma `mdTypeDef` token de metadados pode ter resultados imprevisíveis; os chamadores devem resolver o `mdTypeRef` para um `mdTypeDef` ao passá-la.  
  
 Se o tipo já não estiver carregado, chamando `GetClassFromTokenAndTypeArgs` irá disparar o carregamento, o que é uma operação perigosa em vários contextos. Por exemplo, chamar esse método durante o carregamento dos módulos ou outros tipos poderia levar a um loop infinito como o tempo de execução tenta carregar circularmente as coisas.  
  
 Em geral, use de `GetClassFromTokenAndTypeArgs` não é recomendado. Se os criadores de perfis estiver interessados em eventos para um determinado tipo, deve armazenar o `ModuleID` e `mdTypeDef` do tipo e use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) para verificar se um determinado `ClassID` é o da tipo desejado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
