---
title: Método ICorProfilerInfo2::GetClassIDInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2af0eacbff8220be7f2286f7f345f14126972261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458517"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>Método ICorProfilerInfo2::GetClassIDInfo2
Obtém o módulo de pai e os metadados de token para a definição genérica aberta da classe especificada, o `ClassID` de sua classe pai e o `ClassID` para cada argumento de tipo, se houver, da classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID da classe para a qual as informações serão recuperadas.  
  
 `pModuleId`  
 [out] Ponteiro para a ID do módulo principal para a definição genérica aberta da classe especificada.  
  
 `pTypeDefToken`  
 [out] Ponteiro para o token de metadados para a definição genérica aberta da classe especificada.  
  
 `pParentClassId`  
 [out] Ponteiro para a ID da classe pai.  
  
 `cNumTypeArgs`  
 [in] O tamanho do `typeArgs` matriz.  
  
 `pcNumTypeArgs`  
 [out] Ponteiro para o número total de elementos disponíveis.  
  
 `typeArgs`  
 [out] Uma matriz de `ClassID` valores, cada um deles representa a ID de um argumento de tipo da classe. Quando o método retorna, `typeArgs` conterá alguns ou todos os disponíveis `ClassID` valores.  
  
## <a name="remarks"></a>Comentários  
 O `GetClassIDInfo2` método é semelhante do [: Getclassidinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) método, mas `GetClassIDInfo2` obtém informações adicionais sobre um tipo genérico.  
  
 O criador de perfil código pode chamar [Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter um [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) interface para um determinado módulo. O token de metadados que é retornado para o local referenciado pelo `pTypeDefToken` , em seguida, pode ser usado para acessar os metadados para a classe.  
  
 Depois de `GetClassIDInfo2` retorna, você deve verificar se o `typeArgs` buffer era grande o suficiente para conter todos o `ClassID` valores. Para fazer isso, o valor de comparação que `pcNumTypeArgs` aponta para com o valor de `cNumTypeArgs` parâmetro. Se `pcNumTypeArgs` aponta para um valor que é maior do que `cNumTypeArgs`, alocar uma maior `typeArgs` buffer, atualize `cNumTypeArgs` com o novo tamanho maior e chame `GetClassIDInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetClassIDInfo2` com um comprimento zero `typeArgs` buffer para obter o tamanho do buffer correto. Você pode definir o `typeArgs` de buffer de tamanho para o valor retornado em `pcNumTypeArgs` e chame `GetClassIDInfo2` novamente.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
