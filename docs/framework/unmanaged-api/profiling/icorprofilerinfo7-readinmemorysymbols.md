---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9874c8e567a89fd3977be360666c86406f2cd395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455925"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Com suporte no [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] e versões posteriores]  
  
 Leituras de bytes de um fluxo de símbolo na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `moduleId`  
 [in] O identificador do módulo que contém o fluxo de memória.  
  
 `symbolsReadOffset`  
 [in] O deslocamento dentro do fluxo de memória no qual iniciar a leitura de bytes.  
  
 `pSymbolBytes`  
 [out] Um ponteiro para o buffer no qual os dados serão copiados. O buffer deve ter `countSymbolBytes` de espaço disponível.  
  
 `countSymbolBytes`  
 [in] O número de bytes a serem copiados.  
  
 `pCountSymbolBytesRead`  
 [out] Quando o método retorna, contém o número real de bytes lidos.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK`, se um número diferente de zero de bytes foram lidos.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Comentários  
 O `ReadInMemorySymbols` método tenta ler `countSymbolBytes` de dados que inicia no deslocamento `symbolsReadOffset` dentro do fluxo de memória. Os dados são copiados para `pSymbolBytes`, que deve ter `countSymbolBytes` de espaço disponível.     `pCountSymbolsBytesRead` contém o número real de bytes lidos, que pode ser menor do que `countSymbolBytes` se o fim do fluxo for atingido.  
  
> [!NOTE]
>  A implementação atual não oferece suporte a Reflection. Emit. Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
