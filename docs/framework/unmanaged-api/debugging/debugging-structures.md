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
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415319"
---
# <a name="debugging-structures"></a>Estruturas de depuração
Esta seção descreve as estruturas não gerenciadas que a API de depuração usa.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estrutura CLR_DEBUGGING_VERSION](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Define a versão do produto do CLR (Common Language Runtime) para fins de depuração.  
  
 [Estrutura1 CodeChunkInfo](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Representa uma única parte de código na memória.  
  
 [Estrutura CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Define um objeto que está bloqueando um thread e o motivo pelo qual o segmento está bloqueado.  
  
 [Estrutura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Representa uma cláusula de tratamento de exceções para um determinado pedaço de IL (Intermediate Language).  
  
 [Estrutura CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Representa informações de quadro de pilha de um objeto de exceção.  
  
 [Estrutura CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Mapas de um [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID para seus respectivos [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objeto.  
  
 COR_ACTIVE_FUNCTION  
 Contém informações sobre as funções que estão atualmente ativas nos quadros de um thread.  
  
 [Estrutura COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Fornece informações sobre o layout de um objeto matriz na memória.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP  
 Contém os deslocamentos que são usados ​​para mapear o código da MSIL (Microsoft intermediate language) para o código nativo.  
  
 COR_DEBUG_STEP_RANGE  
 Contém as informações de deslocamento para um intervalo de código.  
  
 [Estrutura COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Fornece informações sobre um campo em um objeto.  
  
 [Estrutura COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Contém informações sobre um objeto que será coletado como lixo.  
  
 [Estrutura COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Fornece informações gerais sobre o heap de coleta de lixo, incluindo se é enumerável.  
  
 [Estrutura COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Fornece informações sobre um objeto no heap gerenciado.  
  
 COR_IL_MAP  
 Especifica mudanças no deslocamento relativo de uma função.  
  
 [Estrutura COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Contém informações sobre uma região da memória no heap gerenciado.  
  
 [Estrutura COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Contém um identificador de tipo.  
  
 [Estrutura COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Fornece informações sobre o layout de um objeto na memória.  
  
 COR_VERSION  
 Armazena o número da versão com quatro partes padrão do CLR.  
  
 [Estrutura StackTrace_SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Fornece um contexto simples que pode ser usado em lugar de uma estrutura `CONTEXT` completa.

 [Estrutura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) define um intervalo de endereços.
 
 [Estrutura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) define um IL para o mapeamento de endereço
 
 [Estrutura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) define o contêiner para uma solicitação de endereço do módulo.

  
## <a name="related-sections"></a>Seções relacionadas  
 [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
