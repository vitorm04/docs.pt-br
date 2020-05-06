---
title: Estrutura DacpMethodDescData
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: d623fe862eaf5902fd89d0e512dd07f73a03246f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860809"
---
# <a name="dacpmethoddescdata-structure"></a>Estrutura DacpMethodDescData

Define um buffer de transporte para as informações de tempo de execução de um método.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a>Membros

| Membro                       | Descrição                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | Indica se o tempo de execução tem código nativo disponível para a instanciação fornecida do método. |
| `bIsDynamic`                 | Indica se o método é gerado dinamicamente por meio da geração de código leve.           |
| `wSlotNumber`                | O número do slot do método na tabela de métodos.                                                   |
| `NativeCodeAddr`             | O endereço nativo inicial do método.                                                            |
| `data`                       | Ponteiro para um buffer usado internamente pelo tempo de execução.                                             |
| `MethodDescPtr`              | Ponteiro para o `MethodDesc` no tempo de execução.                                                     |
| `nativeCodeInfo`             | Ponteiro para um buffer usado internamente pelo tempo de execução para controlar métodos.                            |
| `moduleInfo`                 | Ponteiro para um buffer usado internamente pelo tempo de execução para obter informações sobre o módulo.                      |
| `MDToken`                    | Token associado ao método fornecido.                                                         |
| `payloadGC`                  | Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.                          |
| `payloadGC2`                 | Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.                          |
| `managedDynamicMethodObject` | Se o método for dinâmico, o tempo de execução usará esse buffer internamente para o controle de informações.     |
| `requestedIP`                | Usado para popular a estrutura por solicitação quando um endereço de código nativo é fornecido.                    |
| `rejitDataCurrent`           | Informações sobre a versão instrumentada mais recente do método.                                   |
| `rejitDataRequested`         | Informações de ReJIT para o endereço nativo solicitado.                                             |
| `cJittedRejitVersions`       | Número de vezes que o método foi rejitted por meio de instrumentação.                           |

## <a name="remarks"></a>Comentários

Essa estrutura reside dentro do tempo de execução e não é exposta por nenhum cabeçalho ou arquivo de biblioteca. Para usá-lo, defina a estrutura conforme especificado acima.

## <a name="requirements"></a>Requisitos
**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**.NET Framework versões:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Confira também

- [Depuração](index.md)
- [Estruturas de depuração](debugging-structures.md)
- [Tipos de dados comuns](../common-data-types-unmanaged-api-reference.md)
