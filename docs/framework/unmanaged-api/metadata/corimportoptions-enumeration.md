---
title: Enumeração CorImportOptions
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2f71a277484adbbfe3628222c635528cdab03e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045741"
---
# <a name="corimportoptions-enumeration"></a>Enumeração CorImportOptions
Contém valores de sinalizadores que controlam o comportamento durante a importação de um assembly fora do escopo atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`MDImportOptionDefault`|Indica o comportamento padrão, que é ignorar registros excluídos.|  
|`MDImportOptionAll`|Indica que todos os metadados devem ser enumerados.|  
|`MDImportOptionAllTypeDefs`|Indica que todas as definições de tipo, incluindo o que foi excluído, devem ser enumeradas.|  
|`MDImportOptionAllMethodDefs`|Indica que todos os MethodDefs, incluindo o que foi excluído, deve ser enumerados.|  
|`MDImportOptionAllFieldDefs`|Indica que todos os FieldDefs, incluindo o que foi excluído, deve ser enumerados.|  
|`MDImportOptionAllProperties`|Indica que todos os PropertyDefs, incluindo o que foi excluído, deve ser enumerados.|  
|`MDImportOptionAllEvents`|Indica que todos os EventDefs, incluindo o que foi excluído, deve ser enumerados.|  
|`MDImportOptionAllCustomAttributes`|Indica que todos os atributos personalizados, incluindo o que foi excluído, devem ser enumerados.|  
|`MDImportOptionAllExportedTypes`|Indica que todos os tipos exportados, incluindo o que foi excluído, devem ser enumerados.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
