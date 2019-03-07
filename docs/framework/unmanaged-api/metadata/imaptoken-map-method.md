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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ece12247e48a0a005fd542bf76a32a1c6eeaa7cb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478396"
---
# <a name="imaptokenmap-method"></a>Método IMapToken::Map
Mapeia uma relação entre os assemblies usando assinaturas de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tkImp`  
 [in] O token de metadados que representa o objeto de código importados.  
  
 `tkEmit`  
 [in] O token de metadados que representa o objeto de código emitido.  
  
## <a name="remarks"></a>Comentários  
 Quando o token remapear ocorre durante uma mesclagem, o token original é definido no escopo de metadados importados (origem) e o novo token é delimitado no escopo de metadados de emitido (destino).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
