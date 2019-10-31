---
title: Método ICorDebugRegisterSet2::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 8e5583acfe338c185200c0b8e41b7d6e051fa146
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131350"
---
# <a name="icordebugregisterset2getregisters-method"></a>Método ICorDebugRegisterSet2::GetRegisters
Obtém o valor de cada registro (para a plataforma em que o código está em execução no momento) que é especificado pela máscara de bits fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `maskCount`  
 no O tamanho, em bytes, da matriz de `mask`.  
  
 `mask`  
 no Uma matriz de bytes, cada bit corresponde a um registro. Se o bit for 1, o valor do registro correspondente será recuperado.  
  
 `regCount`  
 no O número de valores de registro a serem recuperados.  
  
 `regBuffer`  
 fora Uma matriz de objetos `CORDB_REGISTER`, cada um deles recebe o valor de um registro.  
  
## <a name="remarks"></a>Comentários  
 O método `GetRegisters` retorna uma matriz de valores dos registros que são especificados pela máscara. A matriz não contém valores de registros cujo bit de máscara não esteja definido. Assim, o tamanho da matriz de `regBuffer` deve ser igual ao número de 1 na máscara. Se o valor de `regCount` for muito pequeno para o número de registros indicado pela máscara, os valores dos registros numerados mais altos serão truncados do conjunto. Se `regCount` for muito grande, os elementos de `regBuffer` não utilizados não serão modificados.  
  
 Se um registro indisponível for indicado pela máscara, um valor indeterminado será retornado para esse registro.  
  
 O método `ICorDebugRegisterSet2::GetRegisters` é necessário para plataformas que têm mais de 64 registros. Por exemplo, IA64 tem 128 registros de uso geral e 128 registros de ponto flutuante, portanto, você precisa de mais de 64 bits na máscara de bits.  
  
 Se você não tiver mais de 64 registros, como é o caso em plataformas como o x86, o método `GetRegisters`, na verdade, converte os bytes na matriz de bytes de `mask` em um `ULONG64` e, em seguida, chama o método [ICorDebugRegisterSet:: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) , que usa a máscara de `ULONG64`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [Interface ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
