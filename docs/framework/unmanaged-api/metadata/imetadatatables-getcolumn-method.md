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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 853f137d91e1b3eb4f3f65a06522618f8441dcb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053670"
---
# <a name="imetadatatablesgetcolumn-method"></a>Método IMetaDataTables::GetColumn
Obtém um ponteiro para o valor contido na célula da coluna e linha especificadas na tabela especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>Parâmetros

 `ixTbl`  
 no O índice da tabela.  
  
 `ixCol`  
 no O índice da coluna na tabela.  
  
 `rid`  
 no O índice da linha na tabela.  
  
 `pVal`  
 fora Um ponteiro para o valor na célula.  
 
## <a name="remarks"></a>Comentários

A interpretação do valor retornado `pVal` depende do tipo da coluna. O tipo de coluna pode ser determinado chamando [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md).

- O método **GetColumn** converte automaticamente colunas do tipo **RID** ou **CodedToken** em valores completos de 32 `mdToken` bits.
- Ele também converte automaticamente valores de 8 ou 16 bits em valores completos de 32 bits. 
- Para colunas do tipo *heap* , o *PVal* retornado será um índice no heap correspondente.

| Tipo de coluna              | pVal contém | Comentário                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)  | mdToken     | *PVal* conterá um token completo. A função converte automaticamente o RID em um token completo. |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | mdToken | Após o retorno, o *PVal* conterá um token completo. A função descompacta automaticamente o CodedToken em um token completo. |
| `iSHORT`(96)            | Int16         | Faça automaticamente a extensão estendida para 32 bits.  |
| `iUSHORT`(97)           | UInt16        | Faça automaticamente a extensão estendida para 32 bits.  |
| `iLONG`(98)             | Int32         |                                        | 
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Byte          | Faça automaticamente a extensão estendida para 32 bits.  |
| `iSTRING`(101)          | Índice de heap de cadeia de caracteres | *PVal* é um índice no heap de cadeia de caracteres. Use [IMetadataTables:: GetString](imetadatatables-getstring-method.md) para obter o valor real da cadeia de caracteres da coluna. |
| `iGUID`(102)            | Índice de heap de GUID | *PVal* é um índice no heap de GUID. Use [IMetadataTables:: GetGUID](imetadatatables-getguid-method.md) para obter o valor de GUID de coluna real. |
| `iBLOB`(103)            | Índice de heap de BLOB | *PVal* é um índice no heap de BLOB. Use [IMetadataTables:: getBlob](imetadatatables-getblob-method.md) para obter o valor de blob de coluna real. |
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor. h  
  
 **Biblioteca** Usado como um recurso em MsCorEE. dll  
  
 **Versões do .NET Framework**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
