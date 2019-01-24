---
title: Método ICorProfilerInfo2::GetContextStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4ebf93c103b74be458ba51577a5195795029176
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520393"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>Método ICorProfilerInfo2::GetContextStaticAddress
Obtém o endereço para o campo especificado do contexto estático que está no escopo do contexto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID da classe que contém o campo de contexto estático solicitado.  
  
 `fieldToken`  
 [in] O token de metadados para o campo de contexto estático solicitado.  
  
 `contextId`  
 [in] A ID do contexto que é o escopo para o campo de contexto estático solicitado.  
  
 `ppAddress`  
 [out] Um ponteiro para o endereço do campo estático dentro do contexto especificado.  
  
## <a name="remarks"></a>Comentários  
 O `GetContextStaticAddress` método pode retornar um dos seguintes:  
  
-   Um HRESULT de CORPROF_E_DATAINCOMPLETE se o campo estático fornecido não foi atribuído um endereço no contexto especificado.  
  
-   Os endereços de objetos que podem estar no heap de coleta de lixo. Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, criadores de perfil não devem presumir que eles são válidos.  
  
 Antes de construtor de classe uma classe do for concluída, `GetContextStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
