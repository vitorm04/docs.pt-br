---
title: Método IMapToken::Map
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176065"
---
# <a name="imaptokenmap-method"></a>Método IMapToken::Map
Mapeia uma relação entre as assembléias usando assinaturas de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `tkImp`  
 [em] O token de metadados que representa o objeto de código importado.  
  
 `tkEmit`  
 [em] O token de metadados que representa o objeto de código emitido.  
  
## <a name="remarks"></a>Comentários  
 Quando o remapa do token ocorre durante uma fusão, o token original é escopo no escopo de metadados importado (fonte) e o novo token é escopo no escopo de metadados emitidos (destino).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
