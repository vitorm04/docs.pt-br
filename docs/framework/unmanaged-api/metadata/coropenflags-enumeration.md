---
title: "Enumeração CorOpenFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c7599a4b85a166aedd7a2293b79699b3ef03d14d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
|`ofReadOnly`|Indica que o arquivo deve ser aberto para leitura e que uma chamada para `QueryInterface` para um [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) não podem ser feitas.|  
|`ofTakeOwnership`|Indica que a memória foi alocada usando uma chamada para [CoTaskMemAlloc](http://msdn.microsoft.com/en-us/c4cb588d-9482-4f90-a92e-75b604540d5c) e será liberado pelos metadados.|  
|`ofNoTypeLib`|Obsoleto. Este sinalizador é ignorado.|  
|`ofNoTransform`|Indica se as transformações automáticas de arquivos .winmd devem ser desabilitadas. Em outras palavras, a projeção de um tipo de Tempo de Execução do Windows para um tipo de .NET Framework deve ser desabilitada. Para obter mais informações, consulte [sob o escopo com o .NET e o tempo de execução do Windows](http://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|Reservado para uso interno.|  
|`ofReserved2`|Reservado para uso interno.|  
|`ofReserved`|Reservado para uso interno.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corhdr  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
