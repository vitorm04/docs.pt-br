---
title: "Método ICorDebugRegisterSet2::GetRegisters"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f9deccff09c255b339a22af711906baf23d7df9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2getregisters-method"></a>Método ICorDebugRegisterSet2::GetRegisters
Obtém o valor de cada registro (para a plataforma na qual o código está sendo executado) que é especificado, a máscara de bits especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `maskCount`  
 [in] O tamanho, em bytes, do `mask` matriz.  
  
 `mask`  
 [in] Uma matriz de bytes, cada bit que corresponde a um registro. Se o bit for 1, o valor do registro correspondente será recuperada.  
  
 `regCount`  
 [in] O número de valores do registro a ser recuperado.  
  
 `regBuffer`  
 [out] Uma matriz de `CORDB_REGISTER` objetos, cada um dos quais recebe o valor de um registro.  
  
## <a name="remarks"></a>Comentários  
 O `GetRegisters` método retorna uma matriz de valores de registros que são especificados pela máscara. A matriz não contém valores de registros cujo bit da máscara não está definido. Portanto, o tamanho do `regBuffer` matriz deve ser igual ao número de 1 a máscara. Se o valor de `regCount` é muito pequeno para o número de registros indicado pela máscara, os valores dos registros numerados mais altos será truncado do conjunto. Se `regCount` é muito grande, não usada `regBuffer` elementos serão modificados.  
  
 Se um registro não disponível é indicado pela máscara, um valor indeterminado será retornado para o registrador.  
  
 O `ICorDebugRegisterSet2::GetRegisters` método é necessário para as plataformas que têm mais de 64 registros. Por exemplo, IA64 tem 128 registros de uso geral e 128 registros de ponto flutuantes, portanto, você precisa de mais de 64 bits na máscara de bits.  
  
 Se você não tem mais de 64 registros, como é o caso em plataformas, como x86, o `GetRegisters` método converte apenas os bytes no `mask` matriz de bytes em uma `ULONG64` e, em seguida, chama o [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) método, que usa o `ULONG64` máscara.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [Interface ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
