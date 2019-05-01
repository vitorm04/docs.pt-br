---
title: Enumeração CorMethodSemanticsAttr
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e36cb91c3ef741badb04b54e2b62158ecf6ced1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045624"
---
# <a name="cormethodsemanticsattr-enumeration"></a>Enumeração CorMethodSemanticsAttr
Contém valores que descrevem a relação entre um método e um evento ou propriedade associada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`msSetter`|Especifica que o método é um `set` acessador para uma propriedade.|  
|`msGetter`|Especifica que o método é um `get` acessador para uma propriedade.|  
|`msOther`|Especifica que o método tem uma relação com uma propriedade ou um evento diferente daqueles definidos aqui.|  
|`msAddOn`|Especifica que o método adiciona métodos do manipulador para um evento.|  
|`msRemoveOn`|Especifica que o método Remove métodos do manipulador para um evento.|  
|`msFire`|Especifica que o método gera um evento.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
