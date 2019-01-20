---
title: Declarando enumerações
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5edd6dfb3dac05ce4614c43949f2ec4c19b5f742
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415943"
---
# <a name="debugging-enumerations"></a>Declarando enumerações
Esta seção descreve as enumerações não gerenciadas que a API de depuração utiliza.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Enumeração CLR_DEBUGGING_PROCESS_FLAGS](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 Fornece valores que são usados pela [iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) método.  
  
 [Enumeração CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 Indica quais regiões de memória uma chamada para o [iclrdataenummemoryregions:: Enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) método deve incluir.  
  
 [Enumeração COR_PUB_ENUMPROCESS](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 Identifica o tipo de processo que será enumerado.  
  
 [Enumeração CorDebugBlockingReason](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 Especifica os motivos pelos quais um thread pode ficar bloqueado em um determinado objeto.  
  
 CorDebugChainReason  
 Indica o motivo ou os motivos para o início de uma cadeia de chamadas.  
  
 [Enumeração CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 Descreve como uma função exportada invocará o código gerenciado.  
  
 [Enumeração CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 Descreve por que uma função exportada chama o código gerenciado.  
  
 CorDebugCreateProcessFlags  
 Fornece opções de depuração adicionais que podem ser usadas em uma chamada para o [icordebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) método.  
  
 [Enumeração CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 Indica o tipo de evento cujas informações são decodificadas pelo [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) método.  
  
 [Enumeração CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Fornece informações adicionais sobre eventos de depuração na plataforma Windows.  
  
 CorDebugExceptionCallbackType  
 Indica o tipo de retorno de chamada é feito de um [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) eventos.  
  
 [Enumeração CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 Fornece informações adicionais sobre uma exceção.  
  
 CorDebugExceptionUnwindCallbackType  
 Indica o evento que está sendo sinalizado pelo retorno de chamada durante a fase de desenrolamento.  
  
 [Enumeração CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 Indica se o coletor de lixo está sendo executado em uma estação de trabalho ou em um servidor.  
  
 [Enumeração CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 Especifica a geração de uma região de memória no heap gerenciado.  
  
 CorDebugHandleType  
 Indica o tipo de manipulação.  
  
 [Enumeração CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 Indica se uma faixa específica de instruções nativas corresponde a uma região de código especial.  
  
 CorDebugIntercept  
 Indica os tipos de código que podem ser entrados.  
  
 [Enumeração CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 Especifica uma versão do .NET Framework ou a versão do .NET Framework na qual uma interface foi introduzida.  
  
 CorDebugInternalFrameType  
 Identifica o tipo de quadro de pilha.  
  
 [Enumeração CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 Contém valores que influenciam o comportamento do compilador just-in-time (JIT) gerenciado.  
  
 [Enumeração CorDebugJITCompilerFlagsDeprecated](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 Obsoleto. Use o `CORDEBUG_JIT_DEFAULT` membro a [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeração em vez disso.  
  
 CorDebugMappingResult  
 Fornece os detalhes sobre como o valor do ponteiro de instrução (IP) foi obtido.  
  
 [Enumeração CorDebugMDAFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 Especifica o status do thread no qual o assistente de depuração gerenciada (MDA) é disparado.  
  
 [Enumeração CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 Fornece um valor que determina se um depurador carrega imagens nativas (NGen) do cache de imagens nativas.  
  
 [Enumeração CorDebugPlatform](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 Fornece valores de plataforma de destino que são usados pela [icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método.  
  
 [Enumeração CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 Descreve o formato dos dados em uma matriz de bytes que contém informações sobre um evento de depuração de exceção nativo.  
  
 CorDebugRegister  
 Especifica os registros associados a uma determinada arquitetura de processador.  
  
 [Enumeração CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 Indica se o contexto é do quadro ativo (ou folha) na pilha ou se foi computado pelo desenrolamento de outro quadro.  
  
 [Enumeração CorDebugStateChange](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.  
  
 CorDebugStepReason  
 Indica o resultado de uma etapa individual.  
  
 CorDebugThreadState  
 Especifica o estado de um thread para depuração.  
  
 \>CorDebugUnmappedStop  
 Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.  
  
 CorDebugUserState  
 Indica o estado do usuário de um thread.  
  
 [Enumeração CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 Identifica a fonte de um objeto para ser coletado do lixo.  
  
 [Enumeração ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 Fornece valores que especificam se o depurador é capaz de acessar variáveis locais ou o código incluído na instrumentação ReJIT do criador de perfis.  
  
 [Enumeração LoggingLevelEnum](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 Indica o nível de severidade de uma mensagem descritiva que é escrita no log de eventos quando um thread gerenciado registrar um evento.  
  
 [Enumeração LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 Indica a operação que foi realizada em uma alternação entre depuração/rastreamento.  
  
 [Enumeração VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 Indica o tipo de local nativo de uma variável.  
  
 [Enumeração WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 Fornece valores que especificam se as atualizações na memória para metadados estão visíveis para um depurador. 

 [Enumeração ClrDataSourceType](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) fornece valores que são usados pela estrutura CLRDATA_IL_ADDRESS_MAP.

## <a name="related-sections"></a>Seções relacionadas  
 [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
