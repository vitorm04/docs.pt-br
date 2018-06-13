---
title: Método ICorDebugDataTarget::ReadVirtual
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d9e619e4176633074242521133d42f191f140ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412185"
---
# <a name="icordebugdatatargetreadvirtual-method"></a>Método ICorDebugDataTarget::ReadVirtual
Obtém um bloco de memória contígua, iniciando no endereço especificado e o retorna no buffer fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] O endereço inicial de memória solicitada.  
  
 `pbuffer`  
 [out] O buffer em que a memória será armazenada.  
  
 `bytesRequested`  
 [in] O número de bytes a ser obtido o endereço de destino.  
  
 `pBytesRead`  
 [out] O número de bytes realmente lidos do endereço de destino. Isso pode ser menos de `bytesRequested`.  
  
## <a name="remarks"></a>Comentários  
 Se o primeiro byte (no endereço inicial especificada) pode ser lidos, a chamada deve retornar êxito (para dar suporte a leitura eficiente de estruturas de dados com autodescritivos comprimento, como cadeias de caracteres terminada em nulo).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
