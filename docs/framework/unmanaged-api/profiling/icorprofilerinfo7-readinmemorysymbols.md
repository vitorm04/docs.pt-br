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
ms.openlocfilehash: 53c01d2db44f4d0adf1ba5b9cc225ab49581aa5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868337"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
 Lê bytes de um fluxo de símbolo na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no O identificador do módulo que contém o fluxo na memória.  
  
 `symbolsReadOffset`  
 no O deslocamento dentro do fluxo na memória no qual começar a ler os bytes.  
  
 `pSymbolBytes`  
 fora Um ponteiro para o buffer para o qual os dados serão copiados. O buffer deve ter `countSymbolBytes` de espaço disponível.  
  
 `countSymbolBytes`  
 no O número de bytes a serem copiados.  
  
 `pCountSymbolBytesRead`  
 fora Quando o método retorna, contém o número real de bytes lidos.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK`, se um número diferente de zero de bytes tiver sido lido.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, se o módulo foi criado usando <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Comentários  
 O método `ReadInMemorySymbols` tenta ler `countSymbolBytes` de dados começando na `symbolsReadOffset` de deslocamento no fluxo na memória. Os dados são copiados para `pSymbolBytes`, que deve ter `countSymbolBytes` de espaço disponível.     `pCountSymbolsBytesRead` contém o número real de bytes lidos, que pode ser menor que `countSymbolBytes` se o final do fluxo for atingido.  
  
> [!NOTE]
> A implementação atual não oferece suporte a Reflection. Emit. Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo7](icorprofilerinfo7-interface.md)
