---
title: Método IMetaDataTables::GetColumn
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177137"
---
# <a name="imetadatatablesgetcolumn-method"></a>Método IMetaDataTables::GetColumn
Obtém um ponteiro para o valor contido na célula da coluna especificada e linha na tabela dada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>parâmetros

 `ixTbl`  
 [em] O índice da tabela.  
  
 `ixCol`  
 [em] O índice da coluna na tabela.  
  
 `rid`  
 [em] O índice da linha na tabela.  
  
 `pVal`  
 [fora] Um ponteiro para o valor na célula.  

## <a name="remarks"></a>Comentários

A interpretação do valor devolvido `pVal` depende do tipo da coluna. O tipo de coluna pode ser determinado ligando para [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- O método **GetColumn** converte automaticamente colunas do tipo **Rid** ou **CodedToken** em valores completos de 32 bits. `mdToken`
- Ele também converte automaticamente valores de 8 bits ou 16 bits em valores completos de 32 bits.
- Para colunas do tipo *heap,* o *pVal* retornado será um índice no heap correspondente.

| Tipo de coluna              | pVal contém | Comentário                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)  | Mdtoken     | *pVal* conterá um Token completo. A função converte automaticamente o Rid em um token completo. |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | Mdtoken | Após o retorno, *pVal* conterá um Token completo. A função descompacta automaticamente o CodedToken em um token completo. |
| `iSHORT`(96)            | Int16         | Sinal automaticamente estendido para 32 bits.  |
| `iUSHORT`(97)           | UInt16        | Sinal automaticamente estendido para 32 bits.  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | Sinal automaticamente estendido para 32 bits.  |
| `iSTRING`(101)          | Índice de pilha de cordas | *pVal* é um índice no heap String. Use [IMetadataTables::GetString](imetadatatables-getstring-method.md) para obter o valor real da seqüência de caracteres da coluna. |
| `iGUID`(102)            | Índice de pilha guia | *pVal* é um índice para o heap Guid. Use [IMetadataTables::GetGuid](imetadatatables-getguid-method.md) para obter o valor de Guia da coluna real. |
| `iBLOB`(103)            | Índice de pilha de blob | *pVal* é um índice para a pilha Blob. Use [IMetadataTables::GetBlob](imetadatatables-getblob-method.md) para obter o valor real da coluna Blob. |
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
