---
title: Estrutura ASSEMBLYMETADATA
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83f6190872ecf4435688f3b7c82a61f5f15d9f62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="assemblymetadata-structure"></a>Estrutura ASSEMBLYMETADATA
Contém informações sobre o assembly referenciado, inclusive sua versão e seu nível de suporte para localidades, processadores e sistemas operacionais.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`usMajorVersion`|O número de versão principal do assembly referenciado. Esse valor não pode ser zero. Se todos os bits de `usMajorVersion` estão configurados, a versão principal não for especificada.|  
|`usMinorVersion`|O número de versão secundária do assembly referenciado. Esse valor não pode ser zero. Se todos os bits de `usMinorVersion` estão configurados, a versão secundária não está especificada.|  
|`usBuildNumber`|O número de compilação do assembly referenciado. Esse valor não pode ser zero. Se todos os bits de `usBuildNumber` estão configurados, o número de compilação não é especificado.|  
|`usRevisionNumber`|O número de revisão do assembly referenciado. Esse valor não pode ser zero. Se todos os bits de `usRevisionNumber` estão configurados, o número de revisão não for especificado.|  
|`szLocale`|Uma lista de nomes de localidades em conformidade com a especificação RFC1766, separada por ponto e vírgula, especificando as localidades com suporte pelo assembly referenciado. Um valor nulo indica independência de localidade. **Observação:** no .NET Framework versão 1.0 não é possível especificar mais de uma localidade.|  
|`cbLocale`|O tamanho em caracteres largos de `szLocale`.|  
|`rdwProcessor`|Uma matriz de identificadores, conforme definido em Winnt. h, para os tipos de processador que são suportados pelo assembly referenciado. Um valor NULL indica independência de processador.|  
|`ulProcessor`|O comprimento do `rdwProcessor` matriz.|  
|`rOS`|Uma matriz de [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instâncias especificando os sistemas operacionais que têm suporte para o assembly referenciado. Um valor NULL indica independência de sistema operacional.|  
|`ulOS`|O comprimento do `rOS` matriz.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [Interface IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [Estrutura OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
