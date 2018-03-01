---
title: "Método ICorProfilerInfo7::GetInMemorySymbolsLength"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8c1299429e9173069c5a39fe4a2b82d1db5938f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>Método ICorProfilerInfo7::GetInMemorySymbolsLength
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
 Retorna o comprimento de um fluxo de símbolo na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] O identificador do módulo que contém o fluxo de memória.  
  
 pCountSymbolBytes  
 [out] Um ponteiro para um `DWORD` valor que, quando o método retorna, contém o comprimento do fluxo em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna `S_OK` se o comprimento do fluxo de memória pode ser determinado, mesmo se ele for zero (0).  
  
 O método retorna `CORPROF_E_MODULE_IS_DYNAMIC` se o método foi criado usando <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="remarks"></a>Comentários  
 Se o módulo tem símbolos na memória, o comprimento do fluxo será colocado em `pCountSymbolBytes`. Se o módulo não tem símbolos na memória, `*pCountSymbolBytes = 0`.  
  
> [!NOTE]
>  A implementação atual não oferece suporte a Reflection. Emit. Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
