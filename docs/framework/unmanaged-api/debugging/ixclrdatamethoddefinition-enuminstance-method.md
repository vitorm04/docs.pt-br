---
title: 'Método IXCLRDataMethodDefinition:: EnumInstance'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790436"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a>Método IXCLRDataMethodDefinition:: EnumInstance

Enumera as instâncias desta definição de método.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a>Parâmetros

`handle`\
[entrada, saída] Um identificador para enumerar as instâncias.

`instance`\
fora A instância enumerada.

## <a name="remarks"></a>Comentários

O método fornecido faz parte da interface de `IXCLRDataMethodDefinition` e corresponde ao quarto slot da tabela de métodos virtuais.

## <a name="requirements"></a>Requisitos do

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Enumeração CLRDataSourceType](clrdatasourcetype-enumeration.md)
- [Depuração](index.md)
- [Interface IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)
- [Interface IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
