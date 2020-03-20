---
title: Estrutura DacpModuleData
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179195"
---
# <a name="dacpmoduledata-structure"></a>Estrutura DacpModuleData

Define um buffer de transporte para as informações de tempo de execução de um módulo.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>Membros

| Membro    | Descrição                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | Endereço do objeto do módulo.                                           |
| `File`    | Um ponteiro para o arquivo executável portátil (PE).                       |
| `ilBase`  | O endereço da base da imagem carregada.                                 |
| `payLoad` | Um buffer de carga para informações adicionais do módulo usadas pelo tempo de execução. |

## <a name="remarks"></a>Comentários

Esta estrutura vive dentro do tempo de execução e não é exposta através de nenhum cabeçalho ou arquivos de biblioteca. Para usá-lo, defina a estrutura conforme especificado acima.

## <a name="requirements"></a>Requisitos
**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**.NET Framework Versions:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Confira também

- [Depuração](index.md)
- [Estruturas de depuração](debugging-structures.md)
