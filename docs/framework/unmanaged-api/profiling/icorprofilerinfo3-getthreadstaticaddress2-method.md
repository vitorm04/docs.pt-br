---
title: Método ICorProfilerInfo3::GetThreadStaticAddress2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a51d88af20b3abbbe2f80134473ec1ba1b7a4b17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a>Método ICorProfilerInfo3::GetThreadStaticAddress2
Obtém o endereço do campo de thread estático especificado está no escopo do thread especificado e do domínio de aplicativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID da classe que contém o campo de thread estático solicitado.  
  
 `fieldToken`  
 [in] O token de metadados para o campo de thread estático solicitado.  
  
 `appDomainId`  
 [in] A ID do domínio do aplicativo.  
  
 `threadId`  
 [in] A ID do thread é o escopo para o campo estático solicitado.  
  
 `ppAddress`  
 [out] Um ponteiro para o endereço do campo estático que está dentro do thread especificado.  
  
## <a name="remarks"></a>Comentários  
 O `GetThreadStaticAddress2` método pode retornar um dos seguintes:  
  
-   Um HRESULT de CORPROF_E_DATAINCOMPLETE se determinado campo estático não tiver sido atribuído um endereço no contexto especificado.  
  
-   Os endereços dos objetos que podem ser no heap de coleta de lixo. Esses endereços podem se tornar inválidos após a coleta de lixo, portanto após a coleta de lixo, criadores de perfil não devem presumir que são válidas.  
  
 Antes da conclusão, o construtor de classe da classe `GetThreadStaticAddress2` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.  
  
 O [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) método é semelhante de `GetThreadStaticAddress2` método, mas não aceita um argumento de domínio de aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
