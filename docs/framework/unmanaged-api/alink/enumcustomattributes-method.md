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
ms.openlocfilehash: 5a3d7d3bb05a878f4d9832cf39a8e8863929c4e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="enumcustomattributes-method"></a>Método EnumCustomAttributes
Recupera atributos personalizados de nível de assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hEnum`  
 Identificador do enumerador.  
  
 `tkType`  
 Tipo de atributos a serem enumerados. Use `mdTokenNill` para todos os atributos.  
  
 `rCustomValues`  
 Recebe os tokens de atributos personalizados.  
  
 `cMax`  
 Especifica o tamanho de `rCustomValues` matriz.  
  
 `pcCustomValues`  
 Opcionalmente, recebe a contagem de valores do token.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna S_OK se o método for bem-sucedido.  
  
## <a name="requirements"></a>Requisitos  
 Requer alink.h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Interface IALink2](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API do ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
