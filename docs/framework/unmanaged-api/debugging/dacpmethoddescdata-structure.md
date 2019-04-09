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
ms.openlocfilehash: 567dc3942f79b6bfd29338b9103083aa64e66451
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203191"
---
# <a name="dacpmethoddescdata-structure"></a>Estrutura DacpMethodDescData

Define um buffer de transporte para obter informações de tempo de execução do método.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Sintaxe

```
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
| `bHasNativeCode`             | Indica se o tempo de execução tem disponível para a determinada instanciação do método de código nativo. |
| `bIsDynamic`                 | Indica se o método é gerado dinamicamente por meio da geração de código leve.           |
| `wSlotNumber`                | Número de slot do método na tabela de método.                                                   |
| `NativeCodeAddr`             | Endereço de nativo inicial do método.                                                            |
| `data`                       | Ponteiro para um buffer usado internamente pelo tempo de execução.                                             |
| `MethodDescPtr`              | Ponteiro para o `MethodDesc` no tempo de execução.                                                     |
| `nativeCodeInfo`             | Ponteiro para um buffer usado internamente pelo tempo de execução para acompanhar os métodos.                            |
| `moduleInfo`                 | Ponteiro para um buffer usado internamente pelo tempo de execução para obter informações de módulo.                      |
| `MDToken`                    | Token associado com o método em questão.                                                         |
| `payloadGC`                  | Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.                          |
| `payloadGC2`                 | Ponteiro para um buffer de coleta de lixo usado internamente pelo tempo de execução.                          |
| `managedDynamicMethodObject` | Se o método for dinâmico, o tempo de execução usa esse buffer internamente para obter informações de acompanhamento.     |
| `requestedIP`                | Usado para preencher a estrutura por solicitação quando é fornecido um endereço de código nativo.                    |
| `rejitDataCurrent`           | Informações sobre a versão mais recente do método instrumentada.                                   |
| `rejitDataRequested`         | Informações do Rejit para o endereço nativo solicitado.                                             |
| `cJittedRejitVersions`       | Número de vezes que o método foi rejitted por meio da instrumentação.                           |

## <a name="remarks"></a>Comentários

Essa estrutura reside dentro do tempo de execução e não é exposta por meio de todos os cabeçalhos ou arquivos de biblioteca. Para usá-lo, defina a estrutura conforme especificado acima.

## <a name="requirements"></a>Requisitos
**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
**Cabeçalho:** Nenhum  
**Biblioteca:** Nenhum  
**Versões do .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Consulte também

- [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Tipos de dados comuns](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
