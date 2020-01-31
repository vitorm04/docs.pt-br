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
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862757"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>Método ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
Obtém a `ClassID` de um tipo usando o token de metadados especificado e os valores de `ClassID` de qualquer argumento de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleID`  
 no A ID do módulo no qual o tipo reside.  
  
 `typeDef`  
 no Um `mdTypeDef` token de metadados que faz referência ao tipo.  
  
 `cTypeArgs`  
 no O número de parâmetros de tipo para o tipo fornecido. Esse valor deve ser zero para tipos não genéricos.  
  
 `typeArgs`  
 no Uma matriz de valores de `ClassID`, cada um dos quais é um argumento do tipo. O valor de `typeArgs` pode ser nulo se `cTypeArgs` for definido como zero.  
  
 `pClassID`  
 fora Um ponteiro para a `ClassID` do tipo especificado.  
  
## <a name="remarks"></a>Comentários  
 Chamar o método `GetClassFromTokenAndTypeArgs` com um `mdTypeRef` em vez de um token de metadados `mdTypeDef` pode ter resultados imprevisíveis; os chamadores devem resolver o `mdTypeRef` a um `mdTypeDef` ao passá-lo.  
  
 Se o tipo ainda não estiver carregado, chamar `GetClassFromTokenAndTypeArgs` irá disparar o carregamento, que é uma operação perigosa em muitos contextos. Por exemplo, chamar esse método durante o carregamento de módulos ou outros tipos pode levar a um loop infinito, pois o tempo de execução tenta carregar as coisas de forma circular.  
  
 Em geral, o uso de `GetClassFromTokenAndTypeArgs` não é recomendado. Se os profileres estiverem interessados em eventos para um tipo específico, eles deverão armazenar o `ModuleID` e `mdTypeDef` desse tipo e usar [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) para verificar se um determinado `ClassID` é do tipo desejado.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
