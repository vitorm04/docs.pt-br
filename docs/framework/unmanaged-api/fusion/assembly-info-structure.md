---
title: Estrutura ASSEMBLY_INFO
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110871"
---
# <a name="assemblyinfo-structure"></a>Estrutura ASSEMBLY_INFO
Contém informações sobre um assembly que está registrado no cache de assembly global.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`cbAssemblyInfo`|O tamanho, em bytes, da estrutura. Este campo é reservado para extensibilidade futura.|  
|`dwAssemblyFlags`|Sinalizadores que indicam os detalhes da instalação sobre o assembly. Há suporte para os seguintes valores:<br /><br /> -O valor ASSEMBLYINFO_FLAG_INSTALLED, que indica que o assembly está instalado. A versão atual do .NET Framework sempre define `dwAssemblyFlags` para esse valor.<br />-O valor ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, que indica que o assembly é uma carga residente. A versão atual do .NET Framework define nunca `dwAssemblyFlags` para esse valor.|  
|`uliAssemblySizeInKB`|O tamanho total, em quilobytes, de arquivos que contém o assembly.|  
|`pszCurrentAssemblyPathBuf`|Um ponteiro para um buffer de cadeia de caracteres que contém o caminho atual para o arquivo de manifesto. O caminho deve terminar com um caractere nulo.|  
|`cchBuf`|O número de caracteres largos, incluindo o terminador nulo, que `pszCurrentAssemblyPathBuf` contém.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de fusão](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [Cache de assembly global](../../../../docs/framework/app-domains/gac.md)
