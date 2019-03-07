---
title: Método ICorDebugRemoteTarget::GetHostName
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2861a2f0aec66832c618dda7d50dd543920102f4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468594"
---
# <a name="icordebugremotetargetgethostname-method"></a>Método ICorDebugRemoteTarget::GetHostName
Retorna o nome de domínio totalmente qualificado ou endereço IPv4 do computador de destino de depuração remota. Não há suporte para IPv6 neste momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchHostName`  
 [in] O tamanho, em caracteres, da `szHostName` buffer. Se esse parâmetro for 0 (zero), `szHostName` deve ser nulo.  
  
 `pcchHostName`  
 [out] O número de caracteres, incluindo um terminador nulo, o nome do host ou endereço IP. Este parâmetro pode ser nulo.  
  
 `szHostName`  
 [out] Buffer que contém o nome do host ou endereço IP.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK  
 O nome do host ou endereço IP foi retornado com êxito.  
  
 E_FAIL (ou outros códigos de retorno e _)  
 Não é possível retornar o nome do host ou endereço IP.  
  
## <a name="remarks"></a>Comentários  
 Esse método é implementado pelo gravador do depurador. Ele deve seguir o paradigma de várias chamadas: Na primeira chamada, o chamador passa nulo para ambos `cchHostName` e `szHostName`, e `pcchHostName` retorna o tamanho do buffer necessário. Na segunda chamada, o tamanho que foi retornado anteriormente é passado `cchHostName`, e um buffer adequadamente dimensionado é passado no `szHostName`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 3,5 SP1  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
