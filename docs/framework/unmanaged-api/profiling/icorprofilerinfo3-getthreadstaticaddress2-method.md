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
ms.openlocfilehash: ee44c89ec30edcb6233081f0757fa0f7b7191178
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449650"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a>Método ICorProfilerInfo3::GetThreadStaticAddress2
Obtém o endereço do campo de thread estático especificado que está no escopo do thread e do domínio do aplicativo especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 no A ID da classe que contém o campo de thread estático solicitado.  
  
 `fieldToken`  
 no O token de metadados para o campo de thread estático solicitado.  
  
 `appDomainId`  
 no A ID do domínio do aplicativo.  
  
 `threadId`  
 no A ID do thread que é o escopo do campo estático solicitado.  
  
 `ppAddress`  
 fora Um ponteiro para o endereço do campo estático que está dentro do thread especificado.  
  
## <a name="remarks"></a>Comentários  
 O método `GetThreadStaticAddress2` pode retornar um dos seguintes:  
  
- Um CORPROF_E_DATAINCOMPLETE HRESULT se o campo estático fornecido não tiver sido atribuído um endereço no contexto especificado.  
  
- Os endereços de objetos que podem estar no heap de coleta de lixo. Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, os profileres não devem presumir que eles são válidos.  
  
 Antes de o construtor de classe de uma classe ser concluído, `GetThreadStaticAddress2` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos possam já estar inicializados e a raiz dos objetos de coleta de lixo.  
  
 O método [ICorProfilerInfo2:: GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) é semelhante ao método `GetThreadStaticAddress2`, mas não aceita um argumento de domínio de aplicativo.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
