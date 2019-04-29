---
title: Enumeração CorDebugNGenPolicy
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca922d8b582c0608073d4fd0ba986167ae470e34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599489"
---
# <a name="cordebugngenpolicy-enumeration"></a>Enumeração CorDebugNGenPolicy
Fornece um valor que determina se um depurador carrega imagens nativas (NGen) do cache de imagens nativas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>Membros  
  
|Nome do membro|Descrição|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|Em um [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] aplicativo, o uso de imagens do cache de imagem nativo local está desabilitado. Em um aplicativo da área de trabalho, essa configuração não tem nenhum efeito.|  
  
## <a name="remarks"></a>Comentários  
 O `CorDebugNGENPolicy` enumeração é usada pelo [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) método. Desabilitando o uso de imagens do cache de imagem nativo local fornece uma experiência de depuração consistente, garantindo que o depurador carrega imagens depuráveis compilado por JIT, em vez de imagens nativas otimizadas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
