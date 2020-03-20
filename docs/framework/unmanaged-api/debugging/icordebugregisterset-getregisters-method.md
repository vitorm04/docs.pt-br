---
title: Método ICorDebugRegisterSet::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178539"
---
# <a name="icordebugregistersetgetregisters-method"></a>Método ICorDebugRegisterSet::GetRegisters
Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bit.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `mask`  
 [em] Uma máscara de bit que especifica quais valores de registro devem ser recuperados. Cada bit corresponde a um registro. Se um bit for definido como um, o valor do registro será recuperado; caso contrário, o valor do registro não é recuperado.  
  
 `regCount`  
 [em] O número de valores cadastrais a serem recuperados.  
  
 `regBuffer`  
 [fora] Uma matriz `CORDB_REGISTER` de objetos, cada um dos quais recebe um valor de um registro.  
  
## <a name="remarks"></a>Comentários  
 O tamanho da matriz deve ser igual ao número de bits definido para um na máscara de bit. O `regCount` parâmetro especifica o número de elementos no buffer que receberão os valores do registro. Se `regCount` o valor for muito pequeno para o número de registros indicados pela máscara, os registros numerados mais altos serão truncados a partir do conjunto. Se `regCount` o valor for muito grande, os elementos não utilizados `regBuffer` não serão modificados.  
  
 Se a máscara de bit especificar `GetRegisters` um registro indisponível, retorne um valor indeterminado para esse registro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
- [Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
