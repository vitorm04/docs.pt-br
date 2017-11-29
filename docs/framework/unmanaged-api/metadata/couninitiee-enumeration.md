---
title: "Enumeração COUNINITIEE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COUNINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COUNINITIEE
helpviewer_keywords: COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c849a32850b5fc9aaca7ea75fdfb30db3de5d8c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="couninitiee-enumeration"></a>Enumeração COUNINITIEE
Especifica constantes usadas pelo [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ao inicializar o common language runtime.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|Indica o modo de cancelamento inicialização padrão.|  
|`COUNINITEE_DLL`|Indica o modo de cancelamento inicialização de descarregamento de um assembly.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
