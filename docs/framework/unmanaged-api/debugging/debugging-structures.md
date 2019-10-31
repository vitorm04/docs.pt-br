---
title: Estruturas de depuração
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 05a321d5025f03d6a0378b462178bf06c0291f48
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123028"
---
# <a name="debugging-structures"></a>Estruturas de depuração

Esta seção descreve as estruturas não gerenciadas que a API de depuração usa.

## <a name="in-this-section"></a>Nesta seção
 [Estrutura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Define um intervalo de endereços.

 [Estrutura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Define um IL para o mapeamento de endereços

 [Estrutura CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Define a versão do produto do Common Language Runtime (CLR) para fins de depuração.

 [Estrutura CodeChunkInfo](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Representa uma única parte do código na memória.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contém informações sobre as funções que estão atualmente ativas em quadros de um thread.

 [Estrutura COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Fornece informações sobre o layout de um objeto de matriz na memória.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contém os deslocamentos que são usados para mapear o código MSIL (Microsoft Intermediate Language) para o código nativo.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contém as informações de deslocamento de um intervalo de código.

 [Estrutura COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Fornece informações sobre um campo em um objeto.

 [Estrutura COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contém informações sobre um objeto que deve ser coletado pelo lixo.

 [Estrutura COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele é enumerável.

 [Estrutura COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Fornece informações sobre um objeto no heap gerenciado.

 [COR_IL_MAP](cor-il-map-structure.md) Especifica alterações no deslocamento relativo de uma função.

 [Estrutura COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contém informações sobre uma região de memória no heap gerenciado.

 [Estrutura COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contém um identificador de tipo.

 [Estrutura COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Fornece informações sobre o layout de um objeto na memória.

 [COR_VERSION](cor-version-structure.md) Armazena o número de versão padrão de quatro partes do Common Language Runtime.

 [Estrutura CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Define um objeto que está bloqueando um thread e o motivo pelo qual o thread é bloqueado.

 [Estrutura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Representa uma cláusula de tratamento de exceção (EH) para uma determinada linguagem intermediária (IL).

 [Estrutura CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Representa informações de quadros de pilha de um objeto de exceção.

 [Estrutura CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Mapeia um GUID de Windows Runtime para seu objeto [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) correspondente.

 [Estrutura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Define o contêiner para uma solicitação de endereço de módulo.

 [Estrutura DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Define um buffer de transporte para as informações de tempo de execução de um método.

 [Estrutura DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Define um buffer de transporte para as informações de tempo de execução de um módulo.

 [Estrutura DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Define as informações básicas sobre um determinado método de instrumento do criador de perfil.

 [Estrutura StackTrace_SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Fornece um contexto simples que pode ser usado no lugar de uma estrutura de `CONTEXT` completa.

## <a name="related-sections"></a>Seções relacionadas

 [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
