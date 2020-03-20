---
title: Método IMetaDataTables::GetRow
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177111"
---
# <a name="imetadatatablesgetrow-method"></a>Método IMetaDataTables::GetRow
Obtém a linha no índice de linha especificado, na tabela no índice de tabela especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `ixTbl`  
 [em] O índice da tabela da qual a linha será recuperada.  
  
 `rid`  
 [em] O índice da linha para obter.  
  
 `ppRow`  
 [fora] Um ponteiro para um ponteiro para a linha.  
  
## <a name="remarks"></a>Comentários  

  Não recomendamos o uso deste método, pois ele não retorna resultados consistentes. Para obter informações sobre a tabela GUID, consulte a documentação da Infra-estrutura de linguagem comum (CLI), especialmente "Partição II: Definição de Metadados e Semântica". A documentação está disponível online; consulte [ECMA C# e Padrões de infra-estrutura de linguagem comum](../../../standard/components.md#applicable-standards) e [Padrão ECMA-335 - Infra-estrutura de linguagem comum (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
