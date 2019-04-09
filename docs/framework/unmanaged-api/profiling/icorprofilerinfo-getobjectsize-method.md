---
title: Método ICorProfilerInfo::GetObjectSize
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d366a0093ca82d2e5b3c40729777a1b6c0766bda
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092195"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>Método ICorProfilerInfo::GetObjectSize
Obtém o tamanho de um objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `objectId`  
 [in] A ID do objeto.  
  
 `pcSize`  
 [out] Um ponteiro para o tamanho do objeto, em bytes.  
  
## <a name="remarks"></a>Comentários  
  
> [!IMPORTANT]
>  Esse método é obsoleto. Ele retorna COR_E_OVERFLOW para objetos de maior que 4GB em plataformas de 64 bits. Use o [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) método em vez disso.  
  
 Objetos diferentes dos mesmos tipos geralmente têm o mesmo tamanho. No entanto, alguns tipos, como matrizes ou cadeias de caracteres, podem ter um tamanho diferente para cada objeto.  
  
 O tamanho retornado pelo `GetObjectSize` método não inclui qualquer preenchimento de alinhamento que pode aparecer após o objeto está no heap de coleta de lixo. Se você usar o `GetObjectSize` método para Avançar para cada objeto no heap de coleta de lixo, adicionar preenchimento manualmente, conforme a necessidade de alinhamento.  
  
-   No Windows de 32 bits, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 e COR_PRF_GC_GEN_2 usam alinhamento de 4 bytes e COR_PRF_GC_LARGE_OBJECT_HEAP usa o alinhamento de 8 bytes.  
  
-   No Windows de 64 bits, o alinhamento sempre tem 8 bytes.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
