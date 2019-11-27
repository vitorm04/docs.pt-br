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
ms.openlocfilehash: 89111bf7eb03d20c2010c7a20c4cd055c2a021e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430724"
---
# <a name="osinfo-structure"></a>Estrutura OSINFO
Contém detalhes sobre o sistema operacional de um assembly ou módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`dwOSPlatformId`|Um dos valores de identificador definidos pela função da plataforma Microsoft Windows `GetVersionEx`. Há suporte para os seguintes valores:<br /><br /> -VER_PLATFORM_WIN32s, ou 0x0000, para especificar o Microsoft Windows 3,1.<br />-VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, para especificar o Windows 95, o Windows 98 ou os sistemas operacionais decrescentes deles.<br />-VER_PLATFORM_WIN32_NT, ou 0x0010, para especificar o Windows NT ou os sistemas operacionais que descendem dele.|  
|`dwOSMajorVersion`|A versão principal do sistema operacional ou um valor nulo para indicar qualquer versão.|  
|`dwOSMinorVersion`|A versão secundária do sistema operacional ou um valor nulo para indicar qualquer versão.|  
  
## <a name="remarks"></a>Comentários  
 o `OSINFO` é baseado na estrutura de `OSVERSIONINFOEX` que é usada em chamadas para a função da plataforma Microsoft Windows `GetVersionEx`. Essa estrutura é usada pela estrutura ASSEMBLYMETADATA para indicar o suporte do sistema operacional.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
