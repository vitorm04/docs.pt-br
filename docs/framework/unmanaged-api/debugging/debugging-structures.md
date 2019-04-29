---
title: Estruturas de depuração
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50db519410b9513725c3dc10637421ba8bb37ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698351"
---
# <a name="debugging-structures"></a>Estruturas de depuração

Esta seção descreve as estruturas não gerenciadas que a API de depuração usa.

## <a name="in-this-section"></a>Nesta seção
 [Estrutura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) define um intervalo de endereços.

 [Estrutura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) define um IL para o mapeamento de endereço

 [Estrutura CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) define a versão do produto do common language runtime (CLR) para fins de depuração.

 [Estrutura CodeChunkInfo](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) representa um único bloco de código na memória.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) contém informações sobre as funções que estão atualmente ativas nos quadros de um thread.

 [Estrutura COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) fornece informações sobre o layout de um objeto de matriz na memória.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) contém os deslocamentos que são usados para mapear o Microsoft intermediate language (MSIL) de código para código nativo.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) contém as informações de deslocamento para um intervalo de código.

 [Estrutura COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) fornece informações sobre um campo em um objeto.

 [Estrutura COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) contém informações sobre um objeto que deve ser coletado como lixo.

 [Estrutura COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele é enumerável.

 [Estrutura COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) fornece informações sobre um objeto no heap gerenciado.

 [COR_IL_MAP](cor-il-map-structure.md) especifica mudanças no deslocamento relativo de uma função.

 [Estrutura COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) contém informações sobre uma região de memória no heap gerenciado.

 [Estrutura COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) contém um identificador de tipo.

 [Estrutura COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) fornece informações sobre o layout de um objeto na memória.

 [COR_VERSION](cor-version-structure.md) armazena o número de versão de quatro partes padrão de common language runtime.

 [Estrutura CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) define um objeto que está bloqueando um thread e o motivo por que o thread está bloqueado.

 [Estrutura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) representa uma cláusula de tratamento (EH) de exceção para um determinado pedaço de IL (linguagem intermediária).

 [Estrutura CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) representa informações de um objeto de exceção de quadro de pilha.

 [Estrutura CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) mapas uma [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID para seus respectivos [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objeto.

 [Estrutura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) define o contêiner para uma solicitação de endereço do módulo.

 [Estrutura DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) define um buffer de transporte para obter informações de tempo de execução do método.

 [Estrutura DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) define um buffer de transporte para obter informações de tempo de execução de um módulo.

 [Estrutura DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) define as informações básicas sobre um determinado método instrumentados pelo criador de perfil.

 [Estrutura StackTrace_SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) fornece um contexto simple que pode ser usado no lugar de uma completa `CONTEXT` estrutura.

## <a name="related-sections"></a>Seções relacionadas

 [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
