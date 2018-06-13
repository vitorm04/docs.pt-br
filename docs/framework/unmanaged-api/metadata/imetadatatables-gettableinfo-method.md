---
title: Método IMetaDataTables::GetTableInfo
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea617668a72413f3387a35fe009b37fa15d03354
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449602"
---
# <a name="imetadatatablesgettableinfo-method"></a>Método IMetaDataTables::GetTableInfo
Obtém o nome, o tamanho de linha, o número de linhas, o número de colunas e o índice da coluna de chave da tabela especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ixTbl`  
 [in] O identificador da tabela cujas propriedades para retornar.  
  
 `pcbRow`  
 [out] Um ponteiro para o tamanho, em bytes, de uma linha da tabela.  
  
 `pcRows`  
 [out] Um ponteiro para o número de linhas na tabela.  
  
 `pcCols`  
 [out] Um ponteiro para o número de colunas na tabela.  
  
 `piKey`  
 [out] Um ponteiro para o índice da coluna de chave, ou -1 se a tabela não tiver nenhuma coluna de chave.  
  
 `ppName`  
 [out] Um ponteiro para um ponteiro para o nome da tabela.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
