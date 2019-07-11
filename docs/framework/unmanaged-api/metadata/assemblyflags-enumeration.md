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
ms.openlocfilehash: 502e7841f8c413aa48732bcea0b6c2178d70c061
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776448"
---
# <a name="assemblyflags-enumeration"></a>Enumeração AssemblyFlags
Contém valores que descrevem os recursos de tempo de execução de um assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`afImplicitExportedTypes`|Especifica que as definições de tipo exportado implícitas dentro dos arquivos que compõem o assembly. Nas versões do .NET Framework 1.0 e 1.1, esse valor sempre deve ser definido.|  
|`afImplicitResources`|Especifica que as definições de recurso são implícitas dentro dos arquivos que compõem o assembly. No .NET Framework 1.0 e 1.1, esse valor é sempre deve ser definido.|  
|`afNonSideBySideAppDomain`|Especifica que o assembly não seja executado com outras versões se estiverem sendo executados no mesmo domínio do aplicativo.|  
|`afNonSideBySideProcess`|Especifica que o assembly não seja executado com outras versões se estiverem sendo executados no mesmo processo.|  
|`afNonSideBySideMachine`|Especifica que o assembly não seja executado com outras versões se elas estão em execução no mesmo computador.|  
  
## <a name="remarks"></a>Comentários  
 Os valores entre 0x0010 e 0x0070, inclusive, são usados para descrever os recursos de compatibilidade lado a lado do assembly referenciado. Se nenhum desses valores estiverem definidas, o assembly deve para ser compatível com o lado a lado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MsCorEE.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
