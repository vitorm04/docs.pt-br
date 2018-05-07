---
title: Enumeração AssemblyFlags
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="assemblyflags-enumeration"></a>Enumeração AssemblyFlags
Contém valores que descrevem os recursos de tempo de execução de um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Especifica que as definições de tipo exportado implícitas dentro dos arquivos que compõem o assembly. Nas versões do .NET Framework 1.0 e 1.1, esse valor é sempre devem ser definidas.|  
|`afImplicitResources`|Especifica que as definições de recursos são implícitas dentro dos arquivos que compõem o assembly. No .NET Framework 1.0 e 1.1, esse valor é sempre devem ser definidas.|  
|`afNonSideBySideAppDomain`|Especifica que o assembly não é possível executar com outras versões se estiverem sendo executados no mesmo domínio do aplicativo.|  
|`afNonSideBySideProcess`|Especifica que o assembly não é possível executar com outras versões se estiverem sendo executados no mesmo processo.|  
|`afNonSideBySideMachine`|Especifica que o assembly não é possível executar com outras versões se estiverem sendo executados no mesmo computador.|  
  
## <a name="remarks"></a>Comentários  
 Os valores entre 0x0010 e 0x0070, inclusive, são usados para descrever os recursos de compatibilidade lado a lado do assembly referenciado. Se nenhum desses valores estiverem definidos, o assembly deve para ser compatível com o lado a lado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MsCorEE.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
