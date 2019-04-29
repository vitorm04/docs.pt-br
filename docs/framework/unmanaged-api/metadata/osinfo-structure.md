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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aba49fb4a60b2e471c541a8d8531a1cbc8627f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775194"
---
# <a name="osinfo-structure"></a>Estrutura OSINFO
Contém detalhes sobre o sistema operacional para um assembly ou módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`dwOSPlatformId`|Um dos valores de identificador definidos pela função de plataforma do Microsoft Windows `GetVersionEx`. Há suporte para os seguintes valores:<br /><br /> -VER_PLATFORM_WIN32s, ou 0x0000, para especificar o Microsoft Windows 3.1.<br />-VER_PLATFORM_WIN32_WINDOWS, ou 0x0001, para especificar o Windows 95, Windows 98 ou sistemas operacionais descendente de-los.<br />-VER_PLATFORM_WIN32_NT, ou 0x0010, para especificar o Windows NT ou sistemas operacionais descendentes dele.|  
|`dwOSMajorVersion`|A versão principal do sistema operacional ou um valor nulo para indicar qualquer versão.|  
|`dwOSMinorVersion`|A versão secundária do sistema operacional ou um valor nulo para indicar qualquer versão.|  
  
## <a name="remarks"></a>Comentários  
 `OSINFO` se baseia a `OSVERSIONINFOEX` estrutura que é usado em chamadas para a função de plataforma do Microsoft Windows `GetVersionEx`. Essa estrutura é usada pela estrutura ASSEMBLYMETADATA para indicar o suporte do sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
