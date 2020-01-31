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
ms.openlocfilehash: cc54664ea8ad61005de3f3fae7407946d1c861b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793839"
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

| {1&gt;Membro&lt;1}                       | Descrição                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | Indica se o tempo de execução tem código nativo disponível para a instanciação fornecida do método. |
| `bIsDynamic`                 | Indica se o método é gerado dinamicamente por meio da geração de código leve.           |
| `wSlotNumber`                | O número do slot do método na tabela de métodos.                                                   |
| `NativeCodeAddr`             | O endereço nativo inicial do método.                                                            |
| `data`                       | Ponteiro para um buffer usado internamente pelo tempo de execução.                                             |
| `MethodDescPtr`              | Ponteiro para a `MethodDesc` no tempo de execução.                                                     |
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

## <a name="requirements"></a>Requisitos do
**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** None  
**Biblioteca:** None  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Veja também

- [Depuração](index.md)
- [Estruturas de depuração](debugging-structures.md)
- [Tipos de dados comuns](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
