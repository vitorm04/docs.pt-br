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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c0106b2dd1151e302c0082b306d999ab5a1c4322
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791632"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>Método ICorProfilerInfo2::GetStaticFieldInfo
Obtém um valor que indica o tipo de estático que se aplica ao campo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID da classe no qual o campo estático é definido.  
  
 `fieldToken`  
 [in] O token de metadados para o campo estático.  
  
 `pFieldInfo`  
 [out] Um ponteiro para um valor igual a [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeração que indica se o campo especificado é estático e, se assim, o tipo de estático que se aplica ao campo.  
  
## <a name="remarks"></a>Comentários  
 Essas informações podem ser usadas para determinar qual função a ser chamada para obter o endereço do campo estático.  
  
 O código do criador de perfil ainda deve verificar os metadados para um campo estático para garantir que ele realmente tenha um endereço. Literais estáticas (ou seja, constantes) existem somente nos metadados e não tem um endereço.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
