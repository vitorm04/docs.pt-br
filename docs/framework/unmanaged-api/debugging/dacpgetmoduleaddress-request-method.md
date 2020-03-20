---
title: DacpGetModuleAddress::Método de solicitação
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179210"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Método de solicitação

Realiza uma solicitação para preencher a estrutura a partir da estrutura de tempo de execução dada.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>parâmetros

`pDataModule`\
[em] Um ponteiro para o módulo de dados de sementes.

## <a name="remarks"></a>Comentários

Esta estrutura vive dentro do tempo de execução e não é exposta através de nenhum cabeçalho ou arquivos de biblioteca. Para usá-lo, a maneira mais fácil é imitar a implementação:

- Devolva o valor `Request` obtido ao `IXCLRDataModule*` ligar para o método no parâmetro com os seguintes parâmetros:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>Requisitos

**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhuma **Biblioteca:** Nenhuma  
**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Confira também

- [Depuração](index.md)
- [DacpGetModuleInterface de endereço](dacpgetmoduleaddress-structure.md)
