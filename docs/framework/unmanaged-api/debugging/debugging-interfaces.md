---
title: Depurando interfaces
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179163"
---
# <a name="debugging-interfaces"></a>Depurando interfaces
Esta seção descreve as interfaces não gerenciadas que lidam com a depuração de um programa que está sendo executado no CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>Nesta seção  
 [ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)\
 Fornece um método para enumerar as regiões da memória que são especificadas por chamadores.  
  
 [Interface de retorno de callback do ICLRDataEnumMemoryRegions](iclrdataenummemoryregionscallback-interface.md)\
 Fornece um método de retorno de chamada para `EnumMemoryRegions` relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada da memória.  
  
 [ICLRDataTarget Interface](iclrdatatarget-interface.md)\
 Fornece métodos para interação com um processo de CLR de destino.  
  
 [ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)\
 Uma subclasse de `ICLRDataTarget` que é usada pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.  
  
 [ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)\
 Uma subclasse de [ICLRDataTarget2](iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.  
  
 [Interface de depuração do ICLR](iclrdebugging-interface.md)\
 Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.  
  
 [Interface de provedor de biblioteca do ICLRDebugging](iclrdebugginglibraryprovider-interface.md)\
 Inclui o método [ProvideLibrary Method,](iclrdebugginglibraryprovider-providelibrary-method.md) que obtém uma interface de retorno de chamada do provedor de biblioteca que permite que bibliotecas de depuração específicas de versão em tempo de execução de idiomas comuns sejam localizadas e carregadas demanda.  
  
 [ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)\
 A interface usada pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.  
  
 [ICorDebug Interface](icordebug-interface.md)\
 Fornece métodos que permitem que os desenvolvedores depurem aplicativos no ambiente do CLR.  
  
 [Interface de domínio do ICorDebugApp](icordebugappdomain-interface.md)\
 Fornece métodos para depurar domínios de aplicativo.  
  
 [ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)\
 Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos ByRef. Essa interface é uma extensão da interface `ICorDebugAppDomain`.  
  
 [ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)\
 Fornece métodos para trabalhar com os tipos de tempo de execução do Windows em um domínio de aplicativo. Essa interface é uma extensão das interfaces `ICorDebugAppDomain` e `ICorDebugAppDomain2`.  
  
 [ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)\
 Logicamente, estende a interface [ICorDebugAppDomain](icordebugappdomain-interface.md) para obter um objeto gerenciado a partir de um invólucro callable COM.  
  
 [ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)\
 Fornece um método que retorna um número especificado de valores `ICorDebugAppDomain` iniciando no próximo local na enumeração.  
  
 [Interface de valor do ICorDebugArray](icordebugarrayvalue-interface.md)\
 Uma subclasse de `ICorDebugHeapValue` que representa uma matriz unidimensional ou multidimensional.  
  
 [ICorDebugAssembly Interface](icordebugassembly-interface.md)\
 Representa um assembly.  
  
 [ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)\
 Representa um assembly. Essa interface é uma extensão da interface `ICorDebugAssembly`.  
  
 [ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)\
 Logicamente, estende a interface [ICorDebugAssembly](icordebugassembly-interface.md) para fornecer suporte para conjuntos de contêineres e seus conjuntos contidos. **Disponível apenas no .NET Native.**  
  
 [ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugAssembly`.  
  
 [ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)\
 Fornece um enumerador para uma lista de estruturas [CorDebugBlockingObject.](cordebugblockingobject-structure.md)  
  
 [ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)\
 Uma subclasse de `ICorDebugHeapValue` que representa um objeto de classe com valor boxed.  
  
 [ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)\
 Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.  
  
 [ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugBreakpoint`.  
  
 [ICorDebugChain Interface](icordebugchain-interface.md)\
 Representa um segmento de uma pilha de chamadas física ou lógica.  
  
 [ICorDebugChainEnum Interface](icordebugchainenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugChain`.  
  
 [ICorDebugClass Interface](icordebugclass-interface.md)\
 Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.  
  
 [ICorDebugClass2 Interface](icordebugclass2-interface.md)\
 Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>. Essa interface estende `ICorDebugClass`.  
  
 [ICorDebugCode Interface](icordebugcode-interface1.md)\
 Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.  
  
 [ICorDebugCode2 Interface](icordebugcode2-interface.md)\
 Fornece métodos que estendem os recursos de `ICorDebugCode`.  
  
 [ICorDebugCode3 Interface](icordebugcode3-interface.md)\
 Fornece um método que estende [o ICorDebugCode](icordebugcode-interface1.md) e [o ICorDebugCode2](icordebugcode2-interface.md) para fornecer informações sobre um valor de retorno gerenciado.  
  
 [ICorDebugCode4 Interface](icordebugcode4-interface.md)\
 Fornece um método que permite que um depurador enumerar as variáveis e argumentos locais em uma função.  
  
 [ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugCode`.  
  
 [ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)\
 Fornece métodos para recuperar objetos da interface armazenados em cache.  
  
 [Interface de contexto de iCorDebug](icordebugcontext-interface.md)\
 Representa um objeto de contexto. Essa interface ainda não foi implementada.  
  
 [Interface ICorDecontrollerController](icordebugcontroller-interface.md)\
 Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.  
  
 [Interface de destino iCorDebugData](icordebugdatatarget-interface.md)\
 Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.  
  
 [ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)\
 Logicamente, estende a interface [ICorDebugDataTarget.](icordebugdatatarget-interface.md) **Disponível apenas no .NET Native.**  
  
 [ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)\
 Logicamente, estende a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para fornecer informações sobre módulos carregados. **Disponível apenas no .NET Native.**  
  
 [ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)\
 Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`. **Disponível apenas no .NET Native.**  
  
 [ICorDebugEditAndContinuErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)\
 Obsoleto. Não use essa interface.  
  
 [Interface iCorDebugEditAndContinusnapshot](icordebugeditandcontinuesnapshot-interface.md)\
 Obsoleto. Não use essa interface.  
  
 [ICorDebugEnum Interface](icordebugenum-interface1.md)\
 Serve como a interface da base abstrata para depurar enumeradores.  
  
 [ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)\
 Obsoleto. Não use essa interface.  
  
 [ICorDebugEval Interface](icordebugeval-interface.md)\
 Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.  
  
 [ICorDebugEval2 Interface](icordebugeval2-interface.md)\
 Estende `ICorDebugEval` para fornecer suporte a tipos genéricos.  
  
 [Interface de evento iCorDebugDebug](icordebugexceptiondebugevent-interface.md)\
 Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para suportar eventos de exceção. **Disponível apenas no .NET Native.**  
  
 [ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)\
 Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.  
  
 [ICorDebugExceptionObjectInterface de valor](icordebugexceptionobjectvalue-interface.md)\
 Estende a interface [ICorDebugObjectValue](icordebugobjectvalue-interface.md) para fornecer informações de rastreamento de pilha a partir de um objeto de exceção gerenciado.  
  
 [ICorDebugFrame Interface](icordebugframe-interface.md)\
 Representa um quadro na pilha atual.  
  
 [ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugFrame`.  
  
 [Interface de função iCorDebug](icordebugfunction-interface1.md)\
 Representa uma função ou um método gerenciado.  
  
 [ICorDebugFunction2 Interface](icordebugfunction2-interface.md)\
 Estende `ICorDebugFunction` logicamente para fornecer suporte à depuração passo a passo Apenas Meu Código.  
  
 [ICorDebugFunction3 Interface](icordebugfunction3-interface.md)\
 Logicamente, estende a interface [ICorDebugFunction](icordebugfunction-interface1.md) para fornecer acesso ao código a partir de uma solicitação ReJIT.  
  
 [ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)\
 Estende `ICorDebugBreakpoint` para fornecer suporte a pontos de interrupção dentro de funções.  
  
 [ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)\
 Fornece um enumerador para objetos que serão coletados do lixo.  
  
 [ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)\
 Uma subclasse de `ICorDebugValue` que se aplica a todos os valores. Essa interface fornece métodos Get e Set para o valor.  
  
 [ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)\
 Fornece um enumerador para um objeto que mapeia GUIDs e seus objetos `ICorDebugType` correspondentes.  
  
 [ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)\
 Uma subclasse de `ICorDebugReferenceValue` que representa um valor de referência para o qual o depurador criou um identificador para coleta de lixo.  
  
 [ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)\
 Fornece um enumerador para objetos no heap gerenciado.  
  
 [ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)\
 Fornece um enumerador para regiões de memória do heap gerenciado.  
  
 [ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)\
 Uma subclasse de `ICorDebugValue` que representa um objeto coletado pelo coletor de lixo do CLR.  
  
 [ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)\
 Uma extensão de `ICorDebugHeapValue` que fornece suporte aos identificadores de runtime.  
  
 [ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)\
 Expõe as propriedades de bloqueio de monitoramento de objetos.  
  
 [ICorDebugILCode Interface](icordebugilcode-interface.md)\
 Representa um segmento de código IL (Intermediate Language).  
  
 [ICorDebugILCode2 Interface](icordebugilcode2-interface.md)\
 Logicamente, estende a interface [ICorDebugILCode](icordebugilcode-interface.md) para fornecer métodos que retornam o token para a assinatura variável local de uma função, e que mapeiam as compensações de linguagem intermediária (IL) instrumentadas de um profiler para deslocamentos il do método original.  
  
 [ICorDebugILFrame Interface](icordebugilframe-interface.md)\
 Representa um registro de ativação do código MSIL.  
  
 [ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)\
 Uma extensão lógica de `ICorDebugILFrame`.  
  
 [ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)\
 Fornece um método que encapsula o valor de retorno de uma função.  
  
 [ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)\
 Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL. Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.  
  
 [ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)\
 Representa a informação do símbolo de depuração para um campo de instância. **Disponível apenas no .NET Native.**  
  
 [Interface de imagem interna do ICorDebug](icordebuginternalframe-interface.md)\
 Identifica os tipos de quadro para o depurador.  
  
 [ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)\
 Fornece informações sobre quadros internos, incluindo endereço de pilha e posição em relação a objetos [ICorDebugFrame.](icordebugframe-interface.md)  
  
 [ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)\
 Fornece informações sobre um módulo carregado. **Disponível apenas no .NET Native.**  
  
 [Interface de retorno de chamada gerenciada do ICorDebug](icordebugmanagedcallback-interface.md)\
 Fornece métodos para processar retornos de chamada do depurador.  
  
 [ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)\
 Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs). `ICorDebugManagedCallback2` é uma extensão lógica de `ICorDebugManagedCallback`.  
  
 [ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)\
 Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.  
  
 [ICorDebugMDA Interface](icordebugmda-interface.md)\
 Representa uma mensagem do assistente de depuração gerenciado (MDA).  
  
 [ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)\
 Representa um buffer na memória. **Disponível apenas no .NET Native.**  
  
 [Interface de registro de gravação de ICorDebugMergedAssembly](icordebugmergedassemblyrecord-interface.md)\
 Fornece informações sobre uma montagem mesclada. **Disponível apenas no .NET Native.**  
  
 [ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)\
 Fornece informações de metadados ao depurador.  
  
 [ICorDebugModule Interface](icordebugmodule-interface.md)\
 Representa um módulo de CLR, que é um executável ou uma biblioteca de vínculo dinâmico (DLL).  
  
 [ICorDebugModule2 Interface](icordebugmodule2-interface.md)\
 Serve como extensão lógica para `ICorDebugModule`.  
  
 [ICorDebugModule3 Interface](icordebugmodule3-interface.md)\
 Cria um leitor de símbolos para um módulo dinâmico.  
  
 [ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)\
 Estende `ICorDebugBreakpoint` para fornecer acesso aos módulos específicos.  
  
 [Interface de evento iCorDebugDebug](icordebugmoduledebugevent-interface.md)\
 Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para suportar eventos em nível de módulo. **Disponível apenas no .NET Native.**  
  
 [ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugModule`.  
  
 [ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)\
 Estende a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para suportar metas de dados mutáveis.  
  
 [Interface de frame nativo do ICorDebug](icordebugnativeframe-interface.md)\
 Uma implementação especializada de `ICorDebugFrame` usada para quadros nativos.  
  
 [ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)\
 Fornece métodos que testam relações de quadros pai e filho.  
  
 [ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de objetos pelos endereços virtuais relacionados (RVAs).  
  
 [Interface de valor do ICorDebugObject](icordebugobjectvalue-interface.md)\
 Uma subclasse de `ICorDebugValue` que representa um valor que contém um objeto.  
  
 [ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)\
 Estende `ICorDebugObjectValue` para oferecer suporte a herança e substituição.  
  
 [Interface de processo de iCorDebug](icordebugprocess-interface.md)\
 Representa um processo que está executando o código gerenciado.  
  
 [ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)\
 Uma extensão lógica de `ICorDebugProcess`.  
  
 [ICorDebugProcess3 Interface](icordebugprocess3-interface.md)\
 Controla as notificações personalizadas do depurador.

 [ICorDebugProcess4 Interface](icordebugprocess4-interface.md)\
 Fornece suporte para controle de execução fora do processo.
  
 [ICorDebugProcess5 Interface](icordebugprocess5-interface.md)\
 Estende a interface [ICorDebugProcess](icordebugprocess-interface.md) para oferecer suporte ao acesso ao heap gerenciado, para fornecer informações sobre coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do cache de imagem nativo local do aplicativo.  
  
 [ICorDebugProcess6 Interface](icordebugprocess6-interface.md)\
 Logicamente, estende a interface [ICorDebugProcess](icordebugprocess-interface.md) para habilitar recursos como decodificação de eventos de depuração gerenciados que são codificados em eventos de depuração de exceção nativa e divisão de módulos virtuais. **Disponível apenas no .NET Native.**  
  
 [ICorDebugProcess7 Interface](icordebugprocess7-interface.md)\
 Fornece um método que configura o depurador para manipular atualizações de metadados na memória no processo de destino.  
  
 [ICorDebugProcess8 Interface](icordebugprocess8-interface.md)\
 Logicamente, estende a interface [ICorDebugProcess](icordebugprocess-interface.md) para ativar ou desativar certos tipos de retornos de exceção [de ICorDebugManagedCallback2.](icordebugmanagedcallback2-interface.md)  
  
 [ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugProcess`.  
  
 [Interface de valor de iCorDebugReference](icordebugreferencevalue-interface.md)\
 Uma subclasse de `ICorDebugValue` que oferece suporte a tipos de referência.  
  
 [ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)\
 Representa o conjunto de registros disponíveis no computador que está executando o código no momento.  
  
 [ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)\
 Estende os recursos de `ICorDebugRegisterSet` para as plataformas de hardware que possuem mais de 64 registros.  
  
 [Interface remota do ICorDebug](icordebugremote-interface.md)\
 Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.  
  
 [Interface de destino remoto do ICorDebug](icordebugremotetarget-interface.md)\
 Fornece métodos que permitem a você depurar aplicativos baseados no Silverlight no ambiente do CLR.  
  
 [Interface de quadro unwindable unwindable ICorDebugExecução](icordebugruntimeunwindableframe-interface.md)\
 Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.  
  
 [ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)\
 Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.  
  
 [ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)\
 Representa a informação do símbolo de depuração para um campo estático. **Disponível apenas no .NET Native.**  
  
 [ICorDebugStepper Interface](icordebugstepper-interface.md)\
 Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.  
  
 [ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)\
 Fornece suporte para a depuração JMC (Apenas Meu Código).  
  
 [ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugStepper`.  
  
 [Interface de valor do ICorDebugString](icordebugstringvalue-interface.md)\
 Uma subclasse de `ICorDebugHeapValue` que se aplica a valores de cadeia de caracteres.  
  
 [ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)\
 Fornece métodos que podem ser usados para recuperar informações de símbolos de depuração. **Disponível apenas no .NET Native.**  
  
 [ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)\
 Logicamente, estende a interface [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) para recuperar informações adicionais de símbolo de depuração. **Disponível apenas no .NET Native.**  
  
 [ICorDebugThread Interface](icordebugthread-interface.md)\
 Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
 [ICorDebugThread2 Interface](icordebugthread2-interface.md)\
 Serve como extensão lógica para `ICorDebugThread`.  
  
 [ICorDebugThread3 Interface](icordebugthread3-interface.md)\
 Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e interfaces correspondentes.  
  
 [ICorDebugThread4 Interface](icordebugthread4-interface.md)\
 Fornece informações de bloqueio de thread.  
  
 [ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugThread`.  
  
 [ICorDebugType Interface](icordebugtype-interface.md)\
 Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.  
  
 [ICorDebugType2 Interface](icordebugtype2-interface.md)\
 Estende a interface [ICorDebugType](icordebugtype-interface.md) para recuperar o identificador de tipo de um tipo base ou tipo complexo (definido pelo usuário).  
  
 [ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugType`.  
  
 [Interface de retorno de chamada de iCorDebugUngerenciado](icordebugunmanagedcallback-interface.md)\
 Fornece notificação de eventos nativos que não estão diretamente relacionados ao CLR.  
  
 [Icordebugvalue](icordebugvalue-interface.md)\
 Representa um valor de leitura ou gravação no processo que está sendo depurado.  
  
 [ICorDebugValue2](icordebugvalue2-interface.md)\
 Estende `ICorDebugValue` para oferecer suporte a `ICorDebugType`.  
  
 [ICorDebugValue3 Interface](icordebugvalue3-interface.md)\
 Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte para arrays maiores que 2 GB.  
  
 [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)\
 Estende `ICorDebugBreakpoint` para fornecer acesso a valores específicos.  
  
 [ICorDebugValueEnum](icordebugvalueenum-interface.md)\
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugValue`.  
  
 [ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)\
 Representa uma variável local ou argumento de uma função.  
  
 [ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)\
 Fornece um enumerador para as variáveis e argumentos locais em uma função.  
  
 [ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)\
 Recupera a informação do símbolo de depuração para uma variável. **Disponível apenas no .NET Native.**  
  
 [ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)\
 Fornece métodos para ajudar no desenrolar da pilha. **Disponível apenas no .NET Native.**  
  
 [ICorPublish Interface](icorpublish-interface.md)\
 Serve como a interface geral para os processos de publicação.  
  
 [Interface de domínio do ICorPublishApp](icorpublishappdomain-interface.md)\
 Representa e fornece informações sobre um domínio de aplicativo.  
  
 [ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)\
 Fornece métodos que percorrem uma coleção de objetos `ICorPublishAppDomain` existentes em um processo.  
  
 [ICorPublishEnum Interface](icorpublishenum-interface.md)\
 Serve como a base abstrata para a publicação de enumeradores.  
  
 [ICorPublishProcess Interface](icorpublishprocess-interface.md)\
 Fornece métodos que acessam informações sobre um processo.  
  
 [ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)\
 Fornece métodos que percorrem uma coleção de objetos `ICorPublishProcess`.  

 [ISOSDacInterface Interface](isosdacinterface-interface.md)\
 Fornece métodos auxiliares para `SOS`acessar dados de .

 [Interface DEdefinição de método IXCLRData](ixclrdatamethoddefinition-interface.md)\
 Fornece métodos para consultar informações sobre uma definição de método.

 [IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)\
 Fornece métodos para consultar informações sobre uma instância do método.

 [IXCLRDataModule Interface](ixclrdatamodule-interface.md)\
 Fornece métodos para consultar informações sobre um módulo carregado.

 [IXCLRDataProcess Interface](ixclrdataprocess-interface.md)\
 Fornece métodos para consultar informações sobre um processo.
  
## <a name="related-sections"></a>Seções relacionadas  
 [Co-classes de depuração](debugging-coclasses.md)\
 [Depuração de funções estáticas globais](debugging-global-static-functions.md)\
 [Depuração de enumerações](debugging-enumerations.md)\
 [Estruturas de depuração](debugging-structures.md)\
