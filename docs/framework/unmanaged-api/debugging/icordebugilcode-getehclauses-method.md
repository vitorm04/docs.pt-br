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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e890629f307e3d3cff11dabdb2db90a5e88ece5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995541"
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
 [out] Uma matriz de [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objetos que contêm informações sobre cláusulas definidas para esse IL de tratamento de exceção.  
  
## <a name="remarks"></a>Comentários  
 Se `cClauses` é 0 e `pcClauses` é não -**nulo**, `pcClauses` é definido como o número de cláusulas de tratamento de exceção disponível. Se `cClauses` for não zero, representará a capacidade de armazenamento da matriz do `clauses`. Quando o método retorna, `clauses` contém o máximo de itens `cClauses` e `pcClauses` estará definido como o número de cláusulas realmente gravadas na matriz `clauses`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [Estrutura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
