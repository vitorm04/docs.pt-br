---
title: Interface IMetaDataTables
ms.date: 03/30/2017
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1a11c0b697a32b184a2c4a60c2f2c88a4b47aaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatables-interface"></a>Interface IMetaDataTables
Fornece métodos para o armazenamento e recuperação de informações de metadados nas tabelas.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetBlob](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|Obtém um ponteiro para o objeto binário grande (BLOB) ao índice da coluna especificada.|  
|[Método GetBlobHeapSize](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|Obtém o tamanho, em bytes, do heap de BLOB.|  
|[Método GetCodedTokenInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|Obtém um ponteiro para uma matriz de tokens associada ao índice de linha especificado.|  
|[Método GetColumn](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|Obtém um ponteiro para os valores contidos na coluna no índice de coluna especificada na tabela do índice da tabela especificada.|  
|[Método GetColumnInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|Obtém dados sobre a coluna especificada na tabela especificada.|  
|[Método GetGuid](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|Obtém um GUID da linha no índice especificado.|  
|[Método GetGuidHeapSize](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|Obtém o tamanho, em bytes, do heap GUID.|  
|[Método GetNextBlob](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|Obtém o índice do próximo BLOB na tabela.|  
|[Método GetNextGuid](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|Obtém o índice do próximo valor GUID na coluna da tabela atual.|  
|[Método GetNextString](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|Obtém o índice da seguinte cadeia de caracteres na coluna da tabela atual.|  
|[Método GetNextUserString](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|Obtém o índice da linha que contém a cadeia de caracteres codificada Avançar na coluna da tabela atual.|  
|[Método GetNumTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|Obtém o número de tabelas no escopo atual `IMetaDataTables` instância.|  
|[Método GetRow](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|Obtém a linha no índice de linha especificada na tabela do índice da tabela especificada.|  
|[Método GetString](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|Obtém a cadeia de caracteres no índice especificado da coluna de tabela no escopo de referência atual.|  
|[Método GetStringHeapSize](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|Obtém o tamanho, em bytes, do heap de cadeia de caracteres.|  
|[Método GetTableIndex](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|Obtém o índice para a tabela referenciada pelo token especificado.|  
|[Método GetTableInfo](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|Obtém o nome, o tamanho de linha, o número de linhas, o número de colunas e o índice da coluna de chave da tabela do índice da tabela especificada.|  
|[Método GetUserString](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|Obtém a cadeia de caracteres codificada no índice especificado na coluna de cadeia de caracteres no escopo atual.|  
|[Método GetUserStringHeapSize](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|Obtém o tamanho, em bytes, do heap de cadeia de caracteres do usuário.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de metadados](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
