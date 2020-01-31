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
ms.openlocfilehash: d30d0bc262d76cf8980f90d8384173d89baf92d5
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862667"
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
 fora Um ponteiro para um valor da enumeração [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) que indica se o campo especificado é estático e, nesse caso, o tipo de estático que se aplica ao campo.  
  
## <a name="remarks"></a>Comentários  
 Essas informações podem ser usadas para determinar qual função chamar para obter o endereço do campo estático.  
  
 O código do criador de perfil ainda deve verificar os metadados de um campo estático para garantir que ele realmente tenha um endereço. Literais estáticos (ou seja, constantes) existem somente nos metadados e não têm um endereço.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](icorprofilerinfo2-interface.md)
