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
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795491"
---
# <a name="assembly_info-structure"></a>Estrutura ASSEMBLY_INFO
Contém informações sobre um assembly que é registrado no cache de assembly global.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`dwAssemblyFlags`|Sinalizadores que indicam os detalhes da instalação sobre o assembly. Há suporte para os seguintes valores:<br /><br /> -O valor ASSEMBLYINFO_FLAG_INSTALLED, que indica que o assembly está instalado. A versão atual do .NET Framework sempre é definida `dwAssemblyFlags` para esse valor.<br />-O valor ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, que indica que o assembly é um conteúdo residente. A versão atual do .NET Framework nunca é definida `dwAssemblyFlags` para esse valor.|  
|`uliAssemblySizeInKB`|O tamanho total, em quilobytes, dos arquivos que o assembly contém.|  
|`pszCurrentAssemblyPathBuf`|Um ponteiro para um buffer de cadeia de caracteres que contém o caminho atual para o arquivo de manifesto. O caminho deve terminar com um caractere nulo.|  
|`cchBuf`|O número de caracteres largos, incluindo o terminador nulo `pszCurrentAssemblyPathBuf` , que contém.|  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** Fusion. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Estruturas de fusão](fusion-structures.md)
- [Cache de assembly global](../../app-domains/gac.md)
