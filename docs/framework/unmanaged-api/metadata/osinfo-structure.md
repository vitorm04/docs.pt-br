---
title: Estrutura OSINFO
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175220"
---
# <a name="osinfo-structure"></a>Estrutura OSINFO
Contém detalhes sobre o sistema operacional para um conjunto ou módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dwOSPlatformId`|Um dos valores identificadores definidos `GetVersionEx`pela função da plataforma Microsoft Windows . Os valores a seguir têm suporte:<br /><br /> - VER_PLATFORM_WIN32s, ou 0x0000, para especificar o Microsoft Windows 3.1.<br />- VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, para especificar o Windows 95, Windows 98 ou sistemas operacionais descendentes deles.<br />- VER_PLATFORM_WIN32_NT, ou 0x0002, para especificar o Windows NT ou sistemas operacionais descendentes dele.|  
|`dwOSMajorVersion`|A versão principal do sistema operacional ou um valor NULL para indicar qualquer versão.|  
|`dwOSMinorVersion`|A versão menor do sistema operacional ou um valor NULL para indicar qualquer versão.|  
  
## <a name="remarks"></a>Comentários  
 `OSINFO`baseia-se `OSVERSIONINFOEX` na estrutura usada em chamadas para `GetVersionEx`a função da plataforma Microsoft Windows . Esta estrutura é usada pela estrutura ASSEMBLYMETADATA para indicar o suporte ao sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Estruturas de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
