---
title: 'Método ICorDebugMutableDataTarget:: WriteVirtual'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 6325dba99fba0ab5e2f752a0635fdd428d3065eb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206749"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>Método ICorDebugMutableDataTarget:: WriteVirtual
Grava a memória no espaço de endereço do processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 no O endereço no qual gravar o conteúdo `pBuffer` .  
  
 `pBuffer`  
 no Um ponteiro para uma matriz de bytes que contém os bytes a serem gravados.  
  
 `address`  
 no O número de bytes em `pBuffer` .  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`em caso de sucesso ou qualquer outro `HRESULT` em caso de falha.  
  
## <a name="remarks"></a>Comentários  
 Se algum byte não puder ser gravado, a chamada do método falhará sem alterar nenhum byte no espaço de endereço de destino. (Caso contrário, o destino estaria em um estado inconsistente que torna a depuração mais não confiável.)  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
