---
title: "ICorDebugILCode2::Método GetLocalVarSigToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode2.GetLocalVarSigToken
api_location: mscordbi.dll
api_type: COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d41b60e5fb528dfba0f7fa82d7792a1f08ba915
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a>ICorDebugILCode2::Método GetLocalVarSigToken
[Com suporte no .NET Framework 4.5.2 e versões posteriores]  
  
 Obtém o token de metadados para a assinatura de variável local para a função que é representada por esta instância.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pmdSig`  
 [out] Um ponteiro para o token `mdSignature` para a assinatura de variável local desta função ou `mdSignatureNil` se não houver uma assinatura (isto é, se a função não tiver variáveis locais).  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugILCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
