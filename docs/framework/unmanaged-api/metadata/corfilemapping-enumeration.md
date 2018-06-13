---
title: Enumeração CorFileMapping
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c8864aa604b0483130eac5aa0d7c0640abbac99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443717"
---
# <a name="corfilemapping-enumeration"></a>Enumeração CorFileMapping
Contém valores que descrevem o tipo de mapeamento de arquivo que é retornado de uma chamada para o [Imetadatainfo](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`fmFlat`|O arquivo está mapeado como um arquivo de dados. Ou seja, o `SEC_IMAGE` sinalizador não foi passado para o Microsoft Win32 `CreateFileMapping` função.|  
|`fmExecutableImage`|O arquivo é mapeado para a execução, usando o `LoadLibrary` função ou o `CreateFileMapping` funcionar com o `SEC_IMAGE` sinalizador.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [Método GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
