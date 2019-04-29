---
title: Método EnumImportTypes
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789944"
---
# <a name="enumimporttypes-method"></a>Método EnumImportTypes

Enumera cada tipo em cada escopo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>Parâmetros

`hEnum`\
Identificador para o enumerador.

`dwMax`\
Número máximo de tipos para recuperar.

`aTypeDefs`\
Recebe tokens do tipo, não deve exceder `dwMax`.

`pdwCount`\
Recebe o número real de tipo no `aTypeDefs`.

## <a name="return-value"></a>Valor de retorno

Se o método for bem-sucedido, retornará S_OK.

## <a name="requirements"></a>Requisitos

Requer alink.h

## <a name="see-also"></a>Consulte também

- [Interface IALink](ialink-interface.md)
- [Interface IALink2](ialink2-interface.md)
- [API do ALink](index.md)