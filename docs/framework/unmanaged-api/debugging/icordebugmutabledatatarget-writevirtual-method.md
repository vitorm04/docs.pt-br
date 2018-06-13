---
title: Método ICorDebugMutableDataTarget::WriteVirtual
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184ae290b3a7d86a3c0351d4cfb072bce37337d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417408"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>Método ICorDebugMutableDataTarget::WriteVirtual
Grava a memória no espaço de endereço de processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] O endereço no qual gravar o conteúdo de `pBuffer`.  
  
 `pBuffer`  
 [in] Um ponteiro para uma matriz de bytes que contém os bytes a serem gravados.  
  
 `address`  
 [in] O número de bytes em `pBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` no caso de sucesso, ou qualquer outra `HRESULT` em caso de falha.  
  
## <a name="remarks"></a>Comentários  
 Se qualquer bytes não podem ser gravados, a chamada de método falhar sem alterar qualquer bytes no espaço de endereço de destino. (Caso contrário, o destino deve ser em um estado inconsistente que torna mais depuração confiável.)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
