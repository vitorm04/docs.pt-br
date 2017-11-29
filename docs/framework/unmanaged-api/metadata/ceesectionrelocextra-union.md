---
title: "CeeSectionRelocExtra União"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionRelocExtra Union
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionRelocExtra
helpviewer_keywords: CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5b584ced996b31be6656082af3f64a19b1f223c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ceesectionrelocextra-union"></a>CeeSectionRelocExtra União
Representa um deslocamento de endereço que é usado pelo [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface para realocar uma seção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`highAdj`|O ajuste de endereço superior da seção.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Uniões de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
