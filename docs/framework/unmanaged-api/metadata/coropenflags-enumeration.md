---
title: Enumeração CorOpenFlags
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55934ef08b10764bb705d7c166621ec7cfcadd0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992674"
---
# <a name="coropenflags-enumeration"></a>Enumeração CorOpenFlags
Contém valores de sinalizadores que controlam o comportamento dos metadados ao abrir arquivos de manifesto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`ofRead`|Indica se o arquivo deve ser aberto como somente leitura.|  
|`ofWrite`|Indica se o arquivo deve ser aberto para gravação.<br /><br /> Se você estiver usando o sinalizador `ofWrite` ao abrir um arquivo .winmd, deverá passar também o sinalizador `ofNoTransform`.|  
|`ofReadWriteMask`|Uma máscara para leitura e gravação.|  
|`ofCopyMemory`|Indica se o arquivo deve ser lido na memória. Os metadados devem manter sua própria cópia.|  
|`ofCacheImage`|Obsoleto. Este sinalizador é ignorado.|  
|`ofManifestMetadata`|Obsoleto. Este sinalizador é ignorado.|  
|`ofReadOnly`|Indica se o arquivo deve ser aberto para leitura e se uma chamada para `QueryInterface` para um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) não pode ser feita.|  
|`ofTakeOwnership`|Indica que a memória foi alocada usando uma chamada para [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) e será liberada pelos metadados.|  
|`ofNoTypeLib`|Obsoleto. Este sinalizador é ignorado.|  
|`ofNoTransform`|Indica se as transformações automáticas de arquivos .winmd devem ser desabilitadas. Em outras palavras, a projeção de um tipo de Tempo de Execução do Windows para um tipo de .NET Framework deve ser desabilitada. Para obter mais informações, consulte [tempo de execução do Windows e o CLR - sob os bastidores com o .NET e o tempo de execução do Windows](https://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|Reservado para uso interno.|  
|`ofReserved2`|Reservado para uso interno.|  
|`ofReserved`|Reservado para uso interno.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr.h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
