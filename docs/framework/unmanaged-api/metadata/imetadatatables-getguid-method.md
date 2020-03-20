---
title: Método IMetaDataTables::GetGuid
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175272"
---
# <a name="imetadatatablesgetguid-method"></a>Método IMetaDataTables::GetGuid
Obtém um GUID da linha no índice especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ixGuid`  
 [em] O índice da linha a partir do qual obter o GUID.  
  
 `ppGuid`  
 [fora] Um ponteiro para um ponteiro para o GUID.  
  
## <a name="remarks"></a>Comentários  

  Não recomendamos o uso deste método, pois ele não retorna resultados consistentes. Para obter informações sobre a tabela GUID, consulte a documentação da Infra-estrutura de linguagem comum (CLI), especialmente "Partição II: Definição de Metadados e Semântica". A documentação está disponível online; consulte [ECMA C# e Padrões de infra-estrutura de linguagem comum](../../../standard/components.md#applicable-standards) e [Padrão ECMA-335 - Infra-estrutura de linguagem comum (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
