---
title: Enumeração CorFileMapping
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: f85a36c810df52f871ecc75b92a3b4440455c66b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450301"
---
# <a name="corfilemapping-enumeration"></a>Enumeração CorFileMapping
Contém valores que descrevem o tipo de mapeamento de arquivo que é retornado de uma chamada para o método [IMetaDataInfo:: GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Membros  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`fmFlat`|O arquivo é mapeado como um arquivo de dados. Ou seja, o sinalizador `SEC_IMAGE` não foi passado para a função de `CreateFileMapping` do Microsoft Win32.|  
|`fmExecutableImage`|O arquivo é mapeado para execução, usando a função `LoadLibrary` ou a função `CreateFileMapping` com o sinalizador `SEC_IMAGE`.|  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorHdr. h  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [Método GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
