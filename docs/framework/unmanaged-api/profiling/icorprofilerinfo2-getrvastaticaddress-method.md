---
title: Método ICorProfilerInfo2::GetRVAStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c2d1aee741ac54e861f7068d883731745ca7788
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584306"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a>Método ICorProfilerInfo2::GetRVAStaticAddress
Obtém o endereço do campo estático especificado endereço virtual relativo (RVA).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `classId`  
 [in] A ID da classe que contém o campo estático RVA solicitado.  
  
 `fieldToken`  
 [in] Token de metadados para o campo estático RVA solicitado.  
  
 `ppAddress`  
 [out] Um ponteiro para o endereço do campo estático RVA.  
  
## <a name="remarks"></a>Comentários  
 O `GetRVAStaticAddress` método pode retornar um dos seguintes:  
  
- Um HRESULT de CORPROF_E_DATAINCOMPLETE se o campo estático fornecido não foi atribuído um endereço no contexto especificado.  
  
- Os endereços de objetos que podem estar no heap de coleta de lixo. Esses endereços podem se tornar inválidos após a coleta de lixo, portanto, após a coleta de lixo, criadores de perfil não devem presumir que eles são válidos.  
  
 Antes de construtor de classe uma classe do for concluída, `GetRVAStaticAddress` retornará CORPROF_E_DATAINCOMPLETE para todos os seus campos estáticos, embora alguns dos campos estáticos já podem ser inicializada e podem ser torcendo objetos de coleta de lixo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
