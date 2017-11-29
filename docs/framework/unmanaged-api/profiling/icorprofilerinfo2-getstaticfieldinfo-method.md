---
title: "Método ICorProfilerInfo2::GetStaticFieldInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStaticFieldInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7cf16a0fae7f3e2afd095534b2e7f7957d44e3e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
  
#### <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID da classe no qual o campo estático é definido.  
  
 `fieldToken`  
 [in] O token de metadados para o campo estático.  
  
 `pFieldInfo`  
 [out] Um ponteiro para um valor de [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeração que indica se o campo especificado é estático, e se assim, o tipo de estático que se aplica ao campo.  
  
## <a name="remarks"></a>Comentários  
 Essas informações podem ser usadas para determinar a função ser chamada para obter o endereço do campo estático.  
  
 O código de criador de perfil ainda deve verificar os metadados para um campo estático garantir que realmente tem um endereço. Literais estáticos (ou seja, constantes) existem somente nos metadados e não tem um endereço.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
