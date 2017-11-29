---
title: "Enumeração ECustomDumpFlavor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ECustomDumpFlavor
api_location: mscoree.dll
api_type: COM
f1_keywords: ECustomDumpFlavor
helpviewer_keywords: ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a7317a3a12acef2a16deebab9a1e1b10205ebf6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ecustomdumpflavor-enumeration"></a>Enumeração ECustomDumpFlavor
Contém valores que indicam quais itens a serem incluídos em um subconjunto personalizado de um heap de despejo quando o relatório de erros.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|Especifica que o despejo de pilha personalizado deve iniciar como um minidespejo e incluir dados extras especificados por qualquer [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instâncias passadas para o mesmo método.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Especifica que o despejo de pilha personalizado deve coletar todos os dados de estado de tempo de execução que não foi alocados dinamicamente.|  
  
## <a name="remarks"></a>Comentários  
 Um parâmetro de tipo `ECustomDumpFlavor` é passado para o [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumeração ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [Interface ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
