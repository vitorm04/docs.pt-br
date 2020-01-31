---
title: Estrutura DacpGetModuleAddress
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1e3a62de3259c012438c64ece26e696682ec96e6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789204"
---
# <a name="dacpgetmoduleaddress-structure"></a>Estrutura DacpGetModuleAddress

Define o contêiner para uma solicitação de endereço de módulo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>Membros

| {1&gt;Membro&lt;1}      | Descrição                |
| ----------- | -------------------------- |
| `ModulePtr` | O ponteiro para o módulo. |

## <a name="methods"></a>{1&gt;Métodos&lt;1}

| Método                                                                                               | Descrição                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Solicitação](dacpgetmoduleaddress-request-method.md) | Executa uma solicitação para popular a estrutura da estrutura de tempo de execução fornecida. |

## <a name="remarks"></a>Comentários

Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca. Para usá-lo, defina a estrutura conforme especificado acima, em que `CLRDATA_ADDRESS` é um inteiro sem sinal de 64 bits.

## <a name="requirements"></a>Requisitos do
**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Estruturas de depuração](debugging-structures.md)
