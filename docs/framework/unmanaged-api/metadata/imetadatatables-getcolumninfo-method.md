---
title: Método IMetaDataTables::GetColumnInfo
ms.date: 10/10/2019
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
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177128"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>Método IMetaDataTables::GetColumnInfo
Obtém dados sobre a coluna especificada na tabela especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>parâmetros
=======

 `ixTbl`  
 [em] O índice da tabela desejada.  
  
 `ixCol`  
 [em] O índice da coluna desejada.  
  
 `poCol`  
 [fora] Um ponteiro para o deslocamento da coluna na linha.  
  
 `pcbCol`  
 [fora] Um ponteiro para o tamanho, em bytes, da coluna.  
  
 `pType`  
 [fora] Um ponteiro para o tipo de valores na coluna.  
  
 `ppName`  
 [fora] Um ponteiro para um ponteiro para o nome da coluna.  

## <a name="remarks"></a>Comentários

O tipo de coluna retornada está dentro de uma variedade de valores:

| Ptype                    | Descrição   | Função auxiliar                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)   | Livrar           | **IsridType**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | Token codificado | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT`(96)            | Int16         | **isFixedType**                   |
| `iUSHORT`(97)           | UInt16        | **isFixedType**                   |
| `iLONG`(98)             | Int32         | **isFixedType**                   |
| `iULONG`(99)            | UInt32        | **isFixedType**                   |
| `iBYTE`(100)            | Byte          | **isFixedType**                   |
| `iSTRING`(101)          | String        | **IsHeapType**                    |
| `iGUID`(102)            | Guid          | **IsHeapType**                    |
| `iBLOB`(103)            | Blob          | **IsHeapType**                    |

Os valores armazenados no *heap* (isto é, `IsHeapType == true`) podem ser lidos usando:

- `iSTRING`: **IMetadataTables.GetString**
- `iGUID`: **IMetadataTables.GetGUID**
- `iBLOB`: **IMetadataTables.GetBlob**

> [!IMPORTANT]
> Para usar as constantes definidas na `#define _DEFINE_META_DATA_META_CONSTANTS` tabela acima, inclua a diretiva fornecida pelo arquivo de cabeçalho *cor.h.*

## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Cor.h  
  
 **Biblioteca:** Usado como recurso em MsCorEE.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface IMetaDataTables](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [Interface IMetaDataTables2](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
