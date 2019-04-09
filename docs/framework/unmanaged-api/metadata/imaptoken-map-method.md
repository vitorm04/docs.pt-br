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
ms.openlocfilehash: a85dc586b0c08fabdd34c018e82314c9003eeded
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170992"
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
