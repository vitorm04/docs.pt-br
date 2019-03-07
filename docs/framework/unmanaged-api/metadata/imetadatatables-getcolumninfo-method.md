---
title: Método IMetaDataTables::GetColumnInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcab5adf30648f6b5a614a407478977bc37c7062
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480696"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>Método IMetaDataTables::GetColumnInfo
Obtém dados sobre a coluna especificada na tabela especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetColumnInfo (   
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `ixTbl`  
 [in] O índice da tabela desejada.  
  
 `ixCol`  
 [in] O índice da coluna desejada.  
  
 `poCol`  
 [out] Um ponteiro para o deslocamento da coluna na linha.  
  
 `pcbCol`  
 [out] Um ponteiro para o tamanho, em bytes, da coluna.  
  
 `pType`  
 [out] Um ponteiro para o tipo dos valores na coluna.  
  
 `ppName`  
 [out] Um ponteiro para um ponteiro para o nome da coluna.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
