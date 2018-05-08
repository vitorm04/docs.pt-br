---
title: Método IMetaDataTables::GetTableIndex
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d207eae5e9ac1b3020216226442321e72840c037
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadatatablesgettableindex-method"></a>Método IMetaDataTables::GetTableIndex
Obtém o índice para a tabela referenciada pelo token especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `token`  
 [in] O token que faz referência à tabela.  
  
 `pixTbl`  
 [out] Um ponteiro para o índice retornado para a tabela referenciada.  
  
## <a name="remarks"></a>Comentários  
 Não recomendamos o uso desse método, porque ele não retorna resultados consistentes. Para obter informações sobre a tabela GUID, consulte a documentação de infra-estrutura de linguagem comum (CLI), especialmente "partição II: metadados definição e semântica". A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** usado como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
