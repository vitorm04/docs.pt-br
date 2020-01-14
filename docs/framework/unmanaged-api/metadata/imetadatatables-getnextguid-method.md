---
title: Método IMetaDataTables::GetNextGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: d4055975287267d08d2c2224ff6ddaa39fca548d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937792"
---
# <a name="imetadatatablesgetnextguid-method"></a>Método IMetaDataTables::GetNextGuid
Obtém o índice do próximo valor de GUID na coluna da tabela atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ixGuid`  
 no O valor de índice de uma coluna de tabela de GUID.  
  
 `pNext`  
 fora Um ponteiro para o índice do próximo valor de GUID.  
  
## <a name="remarks"></a>Comentários  

  Não recomendamos o uso desse método, pois ele não retorna resultados consistentes. Para obter informações sobre a tabela de GUID, consulte a documentação de Common Language Infrastructure (CLI), especialmente "partição II: definição de metadados e semântica". A documentação está disponível online; consulte [padrões C# ECMA e Common Language Infrastructure](../../../standard/components.md#applicable-standards) e [a CLI (Standard ECMA-335-Common Language Infrastructure)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca:** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
