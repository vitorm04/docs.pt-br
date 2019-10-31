---
title: ICorDebugILCode::Método GetEHClauses
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: df9859f33b4146486a046253cf4705cd19c66adf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131092"
---
# <a name="icordebugilcodegetehclauses-method"></a>ICorDebugILCode::Método GetEHClauses
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Retorna um ponteiro para uma lista de cláusulas de tratamento de exceção (EH) que estão definidas para esta linguagem intermediária (IL).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cClauses`  
 [in] A capacidade de armazenamento da matriz de `clauses`. Consulte a seção Comentários para obter mais informações.  
  
 `pcClauses`  
 [out] O número de cláusulas sobre quais informações são gravadas na matriz `clauses`.  
  
 cláusulas  
 fora Uma matriz de objetos [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) que contêm informações sobre cláusulas de tratamento de exceção definidas para esse Il.  
  
## <a name="remarks"></a>Comentários  
 Se `cClauses` for 0 e `pcClauses` for não**nulo**, `pcClauses` será definido como o número de cláusulas de tratamento de exceção disponíveis. Se `cClauses` for não zero, representará a capacidade de armazenamento da matriz do `clauses`. Quando o método retorna, `clauses` contém o máximo de itens `cClauses` e `pcClauses` estará definido como o número de cláusulas realmente gravadas na matriz `clauses`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [Estrutura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
