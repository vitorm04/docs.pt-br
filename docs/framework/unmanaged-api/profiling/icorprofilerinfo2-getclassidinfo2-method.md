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
ms.openlocfilehash: 64d2cd76dafb1a51814b916b5ce73fb08cdcaef9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868854"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>Método ICorProfilerInfo2::GetClassIDInfo2
Obtém o módulo pai e o token de metadados para a definição genérica aberta da classe especificada, a `ClassID` de sua classe pai e a `ClassID` para cada argumento de tipo, se presente, da classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no A ID da classe para a qual as informações serão recuperadas.  
  
 `pModuleId`  
 fora Aponta para a ID do módulo pai para a definição genérica aberta da classe especificada.  
  
 `pTypeDefToken`  
 fora Ponteiro para o token de metadados para a definição genérica aberta da classe especificada.  
  
 `pParentClassId`  
 fora Ponteiro para a ID da classe pai.  
  
 `cNumTypeArgs`  
 no O tamanho da matriz de `typeArgs`.  
  
 `pcNumTypeArgs`  
 fora Aponta para o número total de elementos disponíveis.  
  
 `typeArgs`  
 fora Uma matriz de valores de `ClassID`, cada um representando a ID de um argumento de tipo da classe. Quando o método retornar, `typeArgs` conterá alguns ou todos os valores de `ClassID` disponíveis.  
  
## <a name="remarks"></a>Comentários  
 O método `GetClassIDInfo2` é semelhante ao método [ICorProfilerInfo:: GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) , mas `GetClassIDInfo2` Obtém informações adicionais sobre um tipo genérico.  
  
 O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de [metadados](../../../../docs/framework/unmanaged-api/metadata/index.md) para um determinado módulo. O token de metadados que é retornado para o local referenciado por `pTypeDefToken` pode ser usado para acessar os metadados da classe.  
  
 Depois que `GetClassIDInfo2` retorna, você deve verificar se o buffer de `typeArgs` era grande o suficiente para conter todos os valores de `ClassID`. Para fazer isso, compare o valor que `pcNumTypeArgs` aponta com o valor do parâmetro `cNumTypeArgs`. Se `pcNumTypeArgs` apontar para um valor maior que `cNumTypeArgs`, aloque um buffer de `typeArgs` maior, atualize `cNumTypeArgs` com o tamanho novo, maior e chame `GetClassIDInfo2` novamente.  
  
 Como alternativa, você pode primeiro chamar `GetClassIDInfo2` com um buffer de `typeArgs` de comprimento zero para obter o tamanho de buffer correto. Em seguida, você pode definir o tamanho do buffer de `typeArgs` para o valor retornado em `pcNumTypeArgs` e chamar `GetClassIDInfo2` novamente.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
