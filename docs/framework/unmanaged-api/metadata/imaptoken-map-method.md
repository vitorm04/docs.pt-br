---
title: "Método IMapToken::Map"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e3a9701bab27764803442a3cd0c24c4e412deaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
  
#### <a name="parameters"></a>Parâmetros  
 `tkImp`  
 [in] O token de metadados que representa o objeto de código importados.  
  
 `tkEmit`  
 [in] O token de metadados que representa o objeto de código emitido.  
  
## <a name="remarks"></a>Comentários  
 Quando o token remapear ocorre durante uma mesclagem, o token original é definido no escopo de metadados importados (origem) e o novo token tem seu escopo definido no escopo de metadados emitido (destino).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
