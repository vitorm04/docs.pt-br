---
title: 'Método IXCLRDataMethodDefinition:: EndEnumInstances'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: febe6766c7a35228820421eee975c777988efd1f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396487"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a>Método IXCLRDataMethodDefinition:: EndEnumInstances

Libera os recursos usados por iteradores internos usados durante a enumeração da instância.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>Parâmetros

`handle`\
fora Um identificador para enumerar as instâncias.

## <a name="remarks"></a>Comentários

O método fornecido faz parte da `IXCLRDataMethodDefinition` interface e corresponde ao sétimo slot da tabela de métodos virtuais.

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Interface IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)
