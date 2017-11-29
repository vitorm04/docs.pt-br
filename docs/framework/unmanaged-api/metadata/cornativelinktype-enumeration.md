---
title: "Enumeração CorNativeLinkType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkType
helpviewer_keywords: CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b8da034590bc5e0b2cbd9456d9d5b4ef4970f259
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cornativelinktype-enumeration"></a>Enumeração CorNativeLinkType
Fornece valores que indicam o tipo vinculado em código nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum   
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`nltNone`|Indica que nenhuma das palavras-chave são especificadas.|  
|`nltAnsi`|Indica que uma palavra-chave ANSI é especificada.|  
|`nltUnicode`|Indica que uma palavra-chave Unicode foi especificada|  
|`nltAuto`|Indica que uma palavra-chave auto é especificada.|  
|`nltOle`|Indica que uma palavra-chave OLE é especificada.|  
|`nltMaxValue`|Não usado.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
