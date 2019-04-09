---
title: Método ICorDebugMutableDataTarget::WriteVirtual
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fba970de6e5882d3cbe9be17b5b49be5a3e81aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171646"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>Método ICorDebugMutableDataTarget::WriteVirtual
Grava a memória no espaço de endereço do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 [in] O endereço no qual gravar o conteúdo de `pBuffer`.  
  
 `pBuffer`  
 [in] Um ponteiro para uma matriz de bytes que contém os bytes a serem gravados.  
  
 `address`  
 [in] O número de bytes em `pBuffer`.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` no êxito ou qualquer outro `HRESULT` em caso de falha.  
  
## <a name="remarks"></a>Comentários  
 Se qualquer não podem ser gravados, a chamada de método falhará sem alterar quaisquer bytes no espaço de endereço de destino. (Caso contrário, o destino seria em um estado inconsistente que torna mais depurações não confiável.)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
