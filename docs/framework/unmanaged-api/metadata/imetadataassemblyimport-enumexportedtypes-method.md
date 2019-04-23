---
title: Método IMetaDataAssemblyImport::EnumExportedTypes
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c32dcfe5d00e1d35f7c63aa98a33d26f6b179c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152679"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a>Método IMetaDataAssemblyImport::EnumExportedTypes
Enumera os tipos exportados referenciados no manifesto do assembly no escopo atual de metadados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `phEnum`  
 [no, out] Um ponteiro para o enumerador. Isso deve ser um null valor quando o `EnumExportedTypes` método é chamado pela primeira vez.  
  
 `rExportedTypes`  
 [out] A enumeração de `mdExportedType` tokens de metadados.  
  
 `cMax`  
 [in] O número máximo de `mdExportedType` tokens que podem ser colocadas no `rExportedTypes` matriz.  
  
 `pcTokens`  
 [out] O número de `mdExportedType` tokens realmente colocados nos `rExportedTypes`.  
  
## <a name="return-value"></a>Valor de retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|`EnumExportedTypes` retornado com êxito.|  
|`S_FALSE`|Não há nenhum token para enumerar. Nesse caso, `pcTokens` é definido como zero.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
