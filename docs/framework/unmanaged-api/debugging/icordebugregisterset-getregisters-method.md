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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56a7f343de999d68a71d9eac04eed6e06b444e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568888"
---
# <a name="icordebugregistersetgetregisters-method"></a>Método ICorDebugRegisterSet::GetRegisters
Obtém o valor de cada registro (no computador que está executando código) que é especificado pela máscara de bits.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mask`  
 [in] Uma máscara de bits que especifica quais valores devem ser recuperadas de registro. Cada bit corresponde a um registro. Se um bit é definido como um, o valor do registro é recuperado; Caso contrário, o valor do registro não será recuperado.  
  
 `regCount`  
 [in] O número de valores do registro a ser recuperado.  
  
 `regBuffer`  
 [out] Uma matriz de `CORDB_REGISTER` objetos, cada um dos quais recebe um valor de um registro.  
  
## <a name="remarks"></a>Comentários  
 O tamanho da matriz deve ser igual ao número de bits definidos para um em que a máscara de bits. O `regCount` parâmetro especifica o número de elementos no buffer que receberá os valores do registro. Se o `regCount` valor for muito pequeno para o número de registros indicados pela máscara, os registros de numerada mais alta serão truncados do conjunto. Se o `regCount` valor é muito grande, não usada `regBuffer` elementos serão não modificados.  
  
 Se a máscara de bits especifica um registro que não está disponível, `GetRegisters` retorna um valor indeterminado para que se registram.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [Interface ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
