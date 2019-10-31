---
title: Depurando interfaces
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097190"
---
# <a name="debugging-interfaces"></a>Depurando interfaces
Esta seção descreve as interfaces não gerenciadas que lidam com a depuração de um programa que está sendo executado no CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>Nesta seção  
 \ de [interface ICLRDataEnumMemoryRegions](iclrdataenummemoryregions-interface.md)
 Fornece um método para enumerar as regiões da memória que são especificadas por chamadores.  
  
 \ de [interface ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)
 Fornece um método de retorno de chamada para `EnumMemoryRegions` relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada da memória.  
  
 \ de [interface ICLRDataTarget](iclrdatatarget-interface.md)
 Fornece métodos para interação com um processo de CLR de destino.  
  
 \ de [interface ICLRDataTarget2](iclrdatatarget2-interface.md)
 Uma subclasse de `ICLRDataTarget` que é usada pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.  
  
 \ de [interface ICLRDataTarget3](iclrdatatarget3-interface.md)
 Uma subclasse de [ICLRDataTarget2](iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.  
  
 \ de [interface ICLRDebugging](iclrdebugging-interface.md)
 Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.  
  
 \ de [interface ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md)
 Inclui o método de [método ProvideLibrary](iclrdebugginglibraryprovider-providelibrary-method.md) , que obtém uma interface de retorno de chamada do provedor de biblioteca que permite que Common Language Runtime bibliotecas de depuração específicas à versão sejam localizadas e carregadas sob demanda.  
  
 \ de [interface ICLRMetadataLocator](iclrmetadatalocator-interface.md)
 A interface usada pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.  
  
 \ de [interface ICorDebug](icordebug-interface.md)
 Fornece métodos que permitem que os desenvolvedores depurem aplicativos no ambiente do CLR.  
  
 \ de [interface ICorDebugAppDomain](icordebugappdomain-interface.md)
 Fornece métodos para depurar domínios de aplicativo.  
  
 \ de [interface ICorDebugAppDomain2](icordebugappdomain2-interface.md)
 Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos ByRef. Essa interface é uma extensão da interface `ICorDebugAppDomain`.  
  
 \ de [interface ICorDebugAppDomain3](icordebugappdomain3-interface.md)
 Fornece métodos para trabalhar com os tipos de Windows Runtime em um domínio de aplicativo. Essa interface é uma extensão das interfaces `ICorDebugAppDomain` e `ICorDebugAppDomain2`.  
  
 \ de [interface ICorDebugAppDomain4](icordebugappdomain4-interface.md)
 Estende logicamente a interface [ICorDebugAppDomain](icordebugappdomain-interface.md) para obter um objeto gerenciado de um com callable wrapper.  
  
 \ de [interface ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md)
 Fornece um método que retorna um número especificado de valores `ICorDebugAppDomain` iniciando no próximo local na enumeração.  
  
 \ de [interface ICorDebugArrayValue](icordebugarrayvalue-interface.md)
 Uma subclasse de `ICorDebugHeapValue` que representa uma matriz unidimensional ou multidimensional.  
  
 \ de [interface ICorDebugAssembly](icordebugassembly-interface.md)
 Representa um assembly.  
  
 \ de [interface ICorDebugAssembly2](icordebugassembly2-interface.md)
 Representa um assembly. Essa interface é uma extensão da interface `ICorDebugAssembly`.  
  
 \ de [interface ICorDebugAssembly3](icordebugassembly3-interface.md)
 Estende logicamente a interface [ICorDebugAssembly](icordebugassembly-interface.md) para fornecer suporte para assemblies de contêiner e seus assemblies contidos. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugAssemblyEnum](icordebugassemblyenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugAssembly`.  
  
 \ de [interface ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)
 Fornece um enumerador para uma lista de estruturas [CorDebugBlockingObject](cordebugblockingobject-structure.md) .  
  
 \ de [interface ICorDebugBoxValue](icordebugboxvalue-interface.md)
 Uma subclasse de `ICorDebugHeapValue` que representa um objeto de classe com valor boxed.  
  
 \ de [interface ICorDebugBreakpoint](icordebugbreakpoint-interface.md)
 Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.  
  
 \ de [interface ICorDebugBreakpointEnum](icordebugbreakpointenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugBreakpoint`.  
  
 \ de [interface ICorDebugChain](icordebugchain-interface.md)
 Representa um segmento de uma pilha de chamadas física ou lógica.  
  
 \ de [interface ICorDebugChainEnum](icordebugchainenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugChain`.  
  
 \ de [interface ICorDebugClass](icordebugclass-interface.md)
 Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.  
  
 \ de [interface ICorDebugClass2](icordebugclass2-interface.md)
 Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>. Essa interface estende `ICorDebugClass`.  
  
 \ de [interface ICorDebugCode](icordebugcode-interface1.md)
 Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.  
  
 \ de [interface ICorDebugCode2](icordebugcode2-interface.md)
 Fornece métodos que estendem os recursos de `ICorDebugCode`.  
  
 \ de [interface ICorDebugCode3](icordebugcode3-interface.md)
 Fornece um método que estende [ICorDebugCode](icordebugcode-interface1.md) e [ICorDebugCode2](icordebugcode2-interface.md) para fornecer informações sobre um valor de retorno gerenciado.  
  
 \ de [interface ICorDebugCode4](icordebugcode4-interface.md)
 Fornece um método que permite que um depurador Enumere as variáveis locais e os argumentos em uma função.  
  
 \ de [interface ICorDebugCodeEnum](icordebugcodeenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugCode`.  
  
 \ de [interface ICorDebugComObjectValue](icordebugcomobjectvalue-interface.md)
 Fornece métodos para recuperar objetos da interface armazenados em cache.  
  
 \ de [interface ICorDebugContext](icordebugcontext-interface.md)
 Representa um objeto de contexto. Essa interface ainda não foi implementada.  
  
 \ de [interface ICorDebugController](icordebugcontroller-interface.md)
 Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.  
  
 \ de [interface ICorDebugDataTarget](icordebugdatatarget-interface.md)
 Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.  
  
 \ de [interface ICorDebugDataTarget2](icordebugdatatarget2-interface.md)
 Estende logicamente a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) . **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugDataTarget3](icordebugdatatarget3-interface.md)
 Estende logicamente a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para fornecer informações sobre os módulos carregados. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugDebugEvent](icordebugdebugevent-interface.md)
 Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugEditAndContinueErrorInfo](icordebugeditandcontinueerrorinfo-interface.md)
 Obsoleto. Não use essa interface.  
  
 \ de [interface ICorDebugEditAndContinueSnapshot](icordebugeditandcontinuesnapshot-interface.md)
 Obsoleto. Não use essa interface.  
  
 \ de [interface ICorDebugEnum](icordebugenum-interface1.md)
 Serve como a interface da base abstrata para depurar enumeradores.  
  
 \ de [interface ICorDebugErrorInfoEnum](icordebugerrorinfoenum-interface.md)
 Obsoleto. Não use essa interface.  
  
 \ de [interface ICorDebugEval](icordebugeval-interface.md)
 Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.  
  
 \ de [interface ICorDebugEval2](icordebugeval2-interface.md)
 Estende `ICorDebugEval` para fornecer suporte a tipos genéricos.  
  
 \ de [interface ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)
 Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para dar suporte a eventos de exceção. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)
 Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.  
  
 \ de [interface ICorDebugExceptionObjectValue](icordebugexceptionobjectvalue-interface.md)
 Estende a interface [ICorDebugObjectValue](icordebugobjectvalue-interface.md) para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciado.  
  
 \ de [interface ICorDebugFrame](icordebugframe-interface.md)
 Representa um quadro na pilha atual.  
  
 \ de [interface ICorDebugFrameEnum](icordebugframeenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugFrame`.  
  
 \ de [interface ICorDebugFunction](icordebugfunction-interface1.md)
 Representa uma função ou um método gerenciado.  
  
 \ de [interface ICorDebugFunction2](icordebugfunction2-interface.md)
 Estende `ICorDebugFunction` logicamente para fornecer suporte à depuração passo a passo Apenas Meu Código.  
  
 \ de [interface ICorDebugFunction3](icordebugfunction3-interface.md)
 Estende logicamente a interface [ICorDebugFunction](icordebugfunction-interface1.md) para fornecer acesso ao código de uma solicitação ReJIT.  
  
 \ de [interface ICorDebugFunctionBreakpoint](icordebugfunctionbreakpoint-interface.md)
 Estende `ICorDebugBreakpoint` para fornecer suporte a pontos de interrupção dentro de funções.  
  
 \ de [interface ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)
 Fornece um enumerador para objetos que serão coletados do lixo.  
  
 \ de [interface ICorDebugGenericValue](icordebuggenericvalue-interface.md)
 Uma subclasse de `ICorDebugValue` que se aplica a todos os valores. Essa interface fornece métodos Get e Set para o valor.  
  
 \ de [interface ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)
 Fornece um enumerador para um objeto que mapeia GUIDs e seus objetos `ICorDebugType` correspondentes.  
  
 \ de [interface ICorDebugHandleValue](icordebughandlevalue-interface.md)
 Uma subclasse de `ICorDebugReferenceValue` que representa um valor de referência para o qual o depurador criou um identificador para coleta de lixo.  
  
 \ de [interface ICorDebugHeapEnum](icordebugheapenum-interface.md)
 Fornece um enumerador para objetos no heap gerenciado.  
  
 \ de [interface ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)
 Fornece um enumerador para regiões de memória do heap gerenciado.  
  
 \ de [interface ICorDebugHeapValue](icordebugheapvalue-interface.md)
 Uma subclasse de `ICorDebugValue` que representa um objeto coletado pelo coletor de lixo do CLR.  
  
 \ de [interface ICorDebugHeapValue2](icordebugheapvalue2-interface1.md)
 Uma extensão de `ICorDebugHeapValue` que fornece suporte aos identificadores de tempo de execução.  
  
 \ de [interface ICorDebugHeapValue3](icordebugheapvalue3-interface.md)
 Expõe as propriedades de bloqueio de monitoramento de objetos.  
  
 \ de [interface ICorDebugILCode](icordebugilcode-interface.md)
 Representa um segmento de código IL (Intermediate Language).  
  
 \ de [interface ICorDebugILCode2](icordebugilcode2-interface.md)
 Estende logicamente a interface [ICorDebugILCode](icordebugilcode-interface.md) para fornecer métodos que retornam o token para a assinatura de variável local de uma função e que mapeiam os deslocamentos de Il (linguagem intermediária instrumentada) de um criador de perfil para os deslocamentos de Il do método original.  
  
 \ de [interface ICorDebugILFrame](icordebugilframe-interface.md)
 Representa um registro de ativação do código MSIL.  
  
 \ de [interface ICorDebugILFrame2](icordebugilframe2-interface.md)
 Uma extensão lógica de `ICorDebugILFrame`.  
  
 \ de [interface ICorDebugILFrame3](icordebugilframe3-interface.md)
 Fornece um método que encapsula o valor de retorno de uma função.  
  
 \ de [interface ICorDebugILFrame4](icordebugilframe4-interface.md)
 Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL. Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.  
  
 \ de [interface ICorDebugInstanceFieldSymbol](icordebuginstancefieldsymbol-interface.md)
 Representa as informações de símbolo de depuração de um campo de instância. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugInternalFrame](icordebuginternalframe-interface.md)
 Identifica os tipos de quadro para o depurador.  
  
 \ de [interface ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)
 Fornece informações sobre quadros internos, incluindo o endereço de pilha e a posição em relação aos objetos [ICorDebugFrame](icordebugframe-interface.md) .  
  
 \ de [interface ICorDebugLoadedModule](icordebugloadedmodule-interface.md)
 Fornece informações sobre um módulo carregado. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
 Fornece métodos para processar retornos de chamada do depurador.  
  
 \ de [interface ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)
 Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs). `ICorDebugManagedCallback2` é uma extensão lógica de `ICorDebugManagedCallback`.  
  
 \ de [interface ICorDebugManagedCallback3](icordebugmanagedcallback3-interface.md)
 Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.  
  
 \ de [interface ICorDebugMDA](icordebugmda-interface.md)
 Representa uma mensagem do assistente de depuração gerenciado (MDA).  
  
 \ de [interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)
 Representa um buffer na memória. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)
 Fornece informações sobre um assembly mesclado. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugMetaDataLocator](icordebugmetadatalocator-interface.md)
 Fornece informações de metadados ao depurador.  
  
 \ de [interface ICorDebugModule](icordebugmodule-interface.md)
 Representa um módulo de CLR, que é um executável ou uma biblioteca de vínculo dinâmico (DLL).  
  
 \ de [interface ICorDebugModule2](icordebugmodule2-interface.md)
 Serve como extensão lógica para `ICorDebugModule`.  
  
 \ de [interface ICorDebugModule3](icordebugmodule3-interface.md)
 Cria um leitor de símbolos para um módulo dinâmico.  
  
 \ de [interface ICorDebugModuleBreakpoint](icordebugmodulebreakpoint-interface.md)
 Estende `ICorDebugBreakpoint` para fornecer acesso aos módulos específicos.  
  
 \ de [interface ICorDebugModuleDebugEvent](icordebugmoduledebugevent-interface.md)
 Estende a interface [ICorDebugDebugEvent](icordebugdebugevent-interface.md) para dar suporte a eventos no nível do módulo. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugModuleEnum](icordebugmoduleenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugModule`.  
  
 \ de [interface ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)
 Estende a interface [ICorDebugDataTarget](icordebugdatatarget-interface.md) para dar suporte a destinos de dados mutáveis.  
  
 \ de [interface ICorDebugNativeFrame](icordebugnativeframe-interface.md)
 Uma implementação especializada de `ICorDebugFrame` usada para quadros nativos.  
  
 \ de [interface ICorDebugNativeFrame2](icordebugnativeframe2-interface.md)
 Fornece métodos que testam relações de quadros pai e filho.  
  
 \ de [interface ICorDebugObjectEnum](icordebugobjectenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de objetos pelos endereços virtuais relacionados (RVAs).  
  
 \ de [interface ICorDebugObjectValue](icordebugobjectvalue-interface.md)
 Uma subclasse de `ICorDebugValue` que representa um valor que contém um objeto.  
  
 \ de [interface ICorDebugObjectValue2](icordebugobjectvalue2-interface.md)
 Estende `ICorDebugObjectValue` para oferecer suporte a herança e substituição.  
  
 \ de [interface ICorDebugProcess](icordebugprocess-interface.md)
 Representa um processo que está executando o código gerenciado.  
  
 \ de [interface ICorDebugProcess2](icordebugprocess2-interface1.md)
 Uma extensão lógica de `ICorDebugProcess`.  
  
 \ de [interface ICorDebugProcess3](icordebugprocess3-interface.md)
 Controla as notificações personalizadas do depurador.

 \ de [interface ICorDebugProcess4](icordebugprocess4-interface.md)
 Fornece suporte para controle de execução fora do processo.
  
 \ de [interface ICorDebugProcess5](icordebugprocess5-interface.md)
 Estende a interface [ICorDebugProcess](icordebugprocess-interface.md) para dar suporte ao acesso ao heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do cache de imagem nativa local do aplicativo.  
  
 \ de [interface ICorDebugProcess6](icordebugprocess6-interface.md)
 Estende logicamente a interface [ICorDebugProcess](icordebugprocess-interface.md) para habilitar recursos como decodificação de eventos de depuração gerenciados que são codificados em eventos de depuração de exceção nativa e divisão de módulo virtual. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugProcess7](icordebugprocess7-interface.md)
 Fornece um método que configura o depurador para manipular atualizações de metadados na memória no processo de destino.  
  
 \ de [interface ICorDebugProcess8](icordebugprocess8-interface.md)
 Estende logicamente a interface [ICorDebugProcess](icordebugprocess-interface.md) para habilitar ou desabilitar determinados tipos de retornos de chamada de exceção [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
 \ de [interface ICorDebugProcessEnum](icordebugprocessenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugProcess`.  
  
 \ de [interface ICorDebugReferenceValue](icordebugreferencevalue-interface.md)
 Uma subclasse de `ICorDebugValue` que oferece suporte a tipos de referência.  
  
 \ de [interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
 Representa o conjunto de registros disponíveis no computador que está executando o código no momento.  
  
 \ de [interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
 Estende os recursos de `ICorDebugRegisterSet` para as plataformas de hardware que possuem mais de 64 registros.  
  
 \ de [interface ICorDebugRemote](icordebugremote-interface.md)
 Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.  
  
 \ de [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md)
 Fornece métodos que permitem a você depurar aplicativos baseados no Silverlight no ambiente do CLR.  
  
 \ de [interface ICorDebugRuntimeUnwindableFrame](icordebugruntimeunwindableframe-interface.md)
 Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.  
  
 \ de [interface ICorDebugStackWalk](icordebugstackwalk-interface.md)
 Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.  
  
 \ de [interface ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md)
 Representa as informações de símbolo de depuração de um campo estático. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugStepper](icordebugstepper-interface.md)
 Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.  
  
 \ de [interface ICorDebugStepper2](icordebugstepper2-interface1.md)
 Fornece suporte para a depuração JMC (Apenas Meu Código).  
  
 \ de [interface ICorDebugStepperEnum](icordebugstepperenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugStepper`.  
  
 \ de [interface ICorDebugStringValue](icordebugstringvalue-interface.md)
 Uma subclasse de `ICorDebugHeapValue` que se aplica a valores de cadeia de caracteres.  
  
 \ de [interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
 Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugSymbolProvider2](icordebugsymbolprovider2-interface.md)
 Estende logicamente a interface [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) para recuperar informações adicionais de símbolo de depuração. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugThread](icordebugthread-interface.md)
 Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
 \ de [interface ICorDebugThread2](icordebugthread2-interface.md)
 Serve como extensão lógica para `ICorDebugThread`.  
  
 \ de [interface ICorDebugThread3](icordebugthread3-interface.md)
 Fornece o ponto de entrada para o [ICorDebugStackWalk](icordebugstackwalk-interface.md) e as interfaces correspondentes.  
  
 \ de [interface ICorDebugThread4](icordebugthread4-interface.md)
 Fornece informações de bloqueio de thread.  
  
 \ de [interface ICorDebugThreadEnum](icordebugthreadenum-interface1.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugThread`.  
  
 \ de [interface ICorDebugType](icordebugtype-interface.md)
 Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.  
  
 \ de [interface ICorDebugType2](icordebugtype2-interface.md)
 Estende a interface [ICorDebugType](icordebugtype-interface.md) para recuperar o identificador de tipo de um tipo base ou tipo complexo (definido pelo usuário).  
  
 \ de [interface ICorDebugTypeEnum](icordebugtypeenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugType`.  
  
 \ de [interface ICorDebugUnmanagedCallback](icordebugunmanagedcallback-interface.md)
 Fornece notificação de eventos nativos que não estão diretamente relacionados ao CLR.  
  
 \ [ICorDebugValue](icordebugvalue-interface.md)
 Representa um valor de leitura ou gravação no processo que está sendo depurado.  
  
 \ [ICorDebugValue2](icordebugvalue2-interface.md)
 Estende `ICorDebugValue` para oferecer suporte a `ICorDebugType`.  
  
 \ de [interface ICorDebugValue3](icordebugvalue3-interface.md)
 Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para fornecer suporte a matrizes com mais de 2 GB.  
  
 \ [ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)
 Estende `ICorDebugBreakpoint` para fornecer acesso a valores específicos.  
  
 \ [ICorDebugValueEnum](icordebugvalueenum-interface.md)
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugValue`.  
  
 \ de [interface ICorDebugVariableHome](icordebugvariablehome-interface.md)
 Representa uma variável local ou um argumento de uma função.  
  
 \ de [interface ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)
 Fornece um enumerador para as variáveis locais e argumentos em uma função.  
  
 \ de [interface ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)
 Recupera as informações de símbolo de depuração para uma variável. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorDebugVirtualUnwinder](icordebugvirtualunwinder-interface.md)
 Fornece métodos para ajudar no desenrolamento de pilha. **Disponível somente em .NET Native.**  
  
 \ de [interface ICorPublish](icorpublish-interface.md)
 Serve como a interface geral para os processos de publicação.  
  
 \ de [interface ICorPublishAppDomain](icorpublishappdomain-interface.md)
 Representa e fornece informações sobre um domínio de aplicativo.  
  
 \ de [interface ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)
 Fornece métodos que percorrem uma coleção de objetos `ICorPublishAppDomain` existentes em um processo.  
  
 \ de [interface ICorPublishEnum](icorpublishenum-interface.md)
 Serve como a base abstrata para a publicação de enumeradores.  
  
 \ de [interface ICorPublishProcess](icorpublishprocess-interface.md)
 Fornece métodos que acessam informações sobre um processo.  
  
 \ de [interface ICorPublishProcessEnum](icorpublishprocessenum-interface.md)
 Fornece métodos que percorrem uma coleção de objetos `ICorPublishProcess`.  

 \ de [interface ISOSDacInterface](isosdacinterface-interface.md)
 Fornece métodos auxiliares para acessar dados de `SOS`.

 \ de [interface IXCLRDataMethodDefinition](ixclrdatamethoddefinition-interface.md)
 Fornece métodos para consultar informações sobre uma definição de método.
 
 \ de [interface IXCLRDataMethodInstance](ixclrdatamethodinstance-interface.md)
 Fornece métodos para consultar informações sobre uma instância de método.
 
 \ de [interface IXCLRDataModule](ixclrdatamodule-interface.md)
 Fornece métodos para consultar informações sobre um módulo carregado.
 
 \ de [interface IXCLRDataProcess](ixclrdataprocess-interface.md)
 Fornece métodos para consultar informações sobre um processo.
  
## <a name="related-sections"></a>Seções relacionadas  
 [Depurando coclasses](debugging-coclasses.md)\
 [Depurando funções estáticas globais](debugging-global-static-functions.md)\
 \ de [enumerações de depuração](debugging-enumerations.md)
 [Estruturas de depuração](debugging-structures.md)\
