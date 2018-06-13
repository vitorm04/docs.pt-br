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
ms.openlocfilehash: deaeb4e244a4f9c1e8582d9bea26c2ae5cfde818
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421344"
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
 [in] Uma máscara de bits que especifica quais valores devem ser recuperadas de registro. Cada bit corresponde a um registro. Se um bit é definido como um, o valor do registro é recuperado. Caso contrário, o valor do registro não será recuperado.  
  
 `regCount`  
 [in] O número de valores do registro a ser recuperado.  
  
 `regBuffer`  
 [out] Uma matriz de `CORDB_REGISTER` objetos, cada um deles receberá um valor de um registro.  
  
## <a name="remarks"></a>Comentários  
 O tamanho da matriz deve ser igual ao número de bits definido como um na máscara de bits. O `regCount` parâmetro especifica o número de elementos no buffer que receberá os valores do registro. Se o `regCount` valor é muito pequeno para o número de registros indicado pela máscara, registros numerados mais altos serão truncados do conjunto. Se o `regCount` valor é muito grande, não usada `regBuffer` elementos serão modificados.  
  
 Se a máscara de bits especifica um registro que não está disponível, `GetRegisters` retorna um valor indeterminado para esse registro.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [Interface ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
