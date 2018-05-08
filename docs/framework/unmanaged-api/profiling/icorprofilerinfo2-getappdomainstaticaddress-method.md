---
title: Método ICorProfilerInfo2::GetAppDomainStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8e1886a3e33b533eb525f5b35480a8a7d326da0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a>Método ICorProfilerInfo2::GetAppDomainStaticAddress
Obtém o endereço do campo estático de domínio especificado de aplicativo que está no escopo do domínio do aplicativo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID de classe da classe que contém o campo estático de domínio de aplicativo solicitado.  
  
 `fieldToken`  
 [in] O token de metadados para o campo estático de domínio de aplicativo solicitado.  
  
 `appDomainId`  
 [in] A ID do domínio do aplicativo que é o escopo para o campo estático solicitado.  
  
 `ppAddress`  
 [out] Um ponteiro para o endereço do campo estático dentro do domínio de aplicativo especificado.  
  
## <a name="remarks"></a>Comentários  
 O `GetAppDomainStaticAddress` método pode retornar um dos seguintes:  
  
-   Um HRESULT de CORPROF_E_DATAINCOMPLETE se determinado campo estático não tiver sido atribuído um endereço no contexto especificado.  
  
-   Os endereços dos objetos que podem ser no heap de coleta de lixo. Esses endereços podem se tornar inválidos após a coleta de lixo, portanto após a coleta de lixo, criadores de perfil não devem presumir que são válidas.  
  
 Antes da conclusão, o construtor de classe da classe `GetAppDomainStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos podem já ter sido inicializado e objetos de coleta de lixo de raiz.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
