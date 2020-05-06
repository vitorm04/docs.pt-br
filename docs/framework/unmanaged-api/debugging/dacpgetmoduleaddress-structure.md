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
ms.openlocfilehash: e460264e2393858c028ba51aec4a4f2c01649994
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860831"
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

| Membro      | Descrição                |
| ----------- | -------------------------- |
| `ModulePtr` | O ponteiro para o módulo. |

## <a name="methods"></a>Métodos

| Método                                                                                               | Descrição                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Solicitação](dacpgetmoduleaddress-request-method.md) | Executa uma solicitação para popular a estrutura da estrutura de tempo de execução fornecida. |

## <a name="remarks"></a>Comentários

Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca. Para usá-lo, defina a estrutura conforme especificado acima, `CLRDATA_ADDRESS` em que é um inteiro sem sinal de 64 bits.

## <a name="requirements"></a>Requisitos
**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Confira também

- [Depuração](index.md)
- [Estruturas de depuração](debugging-structures.md)
