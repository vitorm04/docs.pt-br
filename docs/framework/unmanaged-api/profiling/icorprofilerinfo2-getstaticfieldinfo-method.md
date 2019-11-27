---
title: Método ICorProfilerInfo2::GetStaticFieldInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: e74bab058adda759db1fb549022608eedfef5d80
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432979"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>Método ICorProfilerInfo2::GetStaticFieldInfo
Obtém um valor que indica o tipo de estático que se aplica ao campo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no A ID da classe na qual o campo estático é definido.  
  
 `fieldToken`  
 no O token de metadados para o campo estático.  
  
 `pFieldInfo`  
 fora Um ponteiro para um valor da enumeração [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) que indica se o campo especificado é estático e, nesse caso, o tipo de estático que se aplica ao campo.  
  
## <a name="remarks"></a>Comentários  
 Essas informações podem ser usadas para determinar qual função chamar para obter o endereço do campo estático.  
  
 O código do criador de perfil ainda deve verificar os metadados de um campo estático para garantir que ele realmente tenha um endereço. Literais estáticos (ou seja, constantes) existem somente nos metadados e não têm um endereço.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
