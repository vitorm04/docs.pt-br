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
ms.openlocfilehash: 8eca550130a22532cb781e09ec59c60c11a5ba33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416030"
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
  
#### <a name="parameters"></a>Parâmetros  
 `cClauses`  
 [in] A capacidade de armazenamento da matriz de `clauses`. Consulte a seção Comentários para obter mais informações.  
  
 `pcClauses`  
 [out] O número de cláusulas sobre quais informações são gravadas na matriz `clauses`.  
  
 cláusulas  
 [out] Uma matriz de [CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) objetos que contêm informações sobre cláusulas definidas para esse nível de integridade de tratamento de exceção.  
  
## <a name="remarks"></a>Comentários  
 Se `cClauses` é 0 e `pcClauses` é não -**nulo**, `pcClauses` é definido como o número de cláusulas de tratamento de exceção disponível. Se `cClauses` for não zero, representará a capacidade de armazenamento da matriz do `clauses`. Quando o método retorna, `clauses` contém o máximo de itens `cClauses` e `pcClauses` estará definido como o número de cláusulas realmente gravadas na matriz `clauses`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [Estrutura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
