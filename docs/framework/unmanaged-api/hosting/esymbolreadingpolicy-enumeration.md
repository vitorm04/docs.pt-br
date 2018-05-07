---
title: Enumeração ESymbolReadingPolicy
ms.date: 03/30/2017
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28f6bdbc3e382f82b7fdd632b9fc8c4d422629c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="esymbolreadingpolicy-enumeration"></a>Enumeração ESymbolReadingPolicy
Contém valores que defina a política para ler os arquivos do programa (PDB) de banco de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Especifica que o depurador sempre deve ler arquivos PDB.|  
|`eSymbolReadingFullTrustOnly`|Especifica que o depurador deve ler apenas os arquivos PDB que estão associados a assemblies de confiança total.|  
|`eSymbolReadingNever`|Especifica que o depurador nunca deve ler arquivos PDB.|  
  
## <a name="remarks"></a>Comentários  
 O `ESymbolReadingPolicy` enumeração é usada com a [: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
