---
title: Método EnumCustomAttributes
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d8827f46a12bd090fa27e71072d833607d34677
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777354"
---
# <a name="enumcustomattributes-method"></a>Método EnumCustomAttributes
Recupera atributos personalizados no nível do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a>Parâmetros  
 `hEnum`  
 Identificador do enumerador.  
  
 `tkType`  
 Tipo de atributos a serem enumerados. Use `mdTokenNill` para todos os atributos.  
  
 `rCustomValues`  
 Recebe tokens de atributos personalizados.  
  
 `cMax`  
 Especifica o tamanho `rCustomValues` da matriz.  
  
 `pcCustomValues`  
 Opcionalmente, recebe a contagem de valores de token.  
  
## <a name="return-value"></a>Valor de retorno  
 Retornará S_OK se o método tiver sucesso.  
  
## <a name="requirements"></a>Requisitos  
 Requer ALink. h  
  
## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)
