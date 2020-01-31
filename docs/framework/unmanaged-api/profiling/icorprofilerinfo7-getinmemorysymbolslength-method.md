---
title: 'Método ICorProfilerInfo7:: GetInMemorySymbolsLength'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: a675cc301d2dd32f87e3864a3123e2044761ef91
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868350"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>Método ICorProfilerInfo7:: GetInMemorySymbolsLength
[Com suporte no .NET Framework 4.6.1 e versões posteriores]  
  
 Retorna o comprimento de um fluxo de símbolo na memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `moduleId`  
 no O identificador do módulo que contém o fluxo na memória.  
  
 pCountSymbolBytes  
 fora Um ponteiro para um valor `DWORD` que, quando o método retorna, contém o comprimento do fluxo em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retornará `S_OK` se o comprimento do fluxo de memória puder ser determinado, mesmo se for zero (0).  
  
 O método retornará `CORPROF_E_MODULE_IS_DYNAMIC` se o método tiver sido criado usando <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="remarks"></a>Comentários  
 Se o módulo tiver símbolos na memória, o comprimento do fluxo será colocado em `pCountSymbolBytes`. Se o módulo não tiver símbolos na memória, `*pCountSymbolBytes = 0`.  
  
> [!NOTE]
> A implementação atual não oferece suporte a Reflection. Emit. Se o módulo foi criado usando Reflection. Emit, o método retornará `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo7](icorprofilerinfo7-interface.md)
