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
ms.openlocfilehash: fd362beb9f8fd7a1f2076eb6490a96c0358520e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432141"
---
# <a name="imaptokenmap-method"></a>Método IMapToken::Map
Mapeia uma relação entre os assemblies usando assinaturas de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tkImp`  
 no O token de metadados que representa o objeto de código importado.  
  
 `tkEmit`  
 no O token de metadados que representa o objeto de código emitido.  
  
## <a name="remarks"></a>Comentários  
 Quando o novo mapeamento de token ocorre durante uma mesclagem, o token original é definido no escopo de metadados importado (origem) e o novo token é definido no escopo de metadados emitido (destino).  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
