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
ms.openlocfilehash: 2f8337f96239948189ffd58923d87fd05c79b0c3
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204856"
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
|`DISABLE_LOCAL_NIC`|Em um aplicativo da loja do Windows 8. x, o uso de imagens do cache de imagem nativa local está desabilitado. Em um aplicativo de área de trabalho, essa configuração não tem efeito.|  
  
## <a name="remarks"></a>Comentários  
 A enumeração de `CorDebugNGENPolicy` é usada pelo método [ICorDebugProcess5:: EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) . A desabilitação do uso de imagens do cache de imagem nativa local fornece uma experiência de depuração consistente, garantindo que o depurador Carregue imagens depurável compiladas por JIT em vez de imagens nativas otimizadas.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
