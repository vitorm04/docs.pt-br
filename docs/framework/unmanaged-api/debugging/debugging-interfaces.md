---
title: Depurando interfaces
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 991e333c53101a2be2a8a19d3960c3d0879619be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409926"
---
# <a name="debugging-interfaces"></a>Depurando interfaces
Esta seção descreve as interfaces não gerenciadas que lidam com a depuração de um programa que está sendo executado no CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface ICLRDataEnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 Fornece um método para enumerar as regiões da memória que são especificadas por chamadores.  
  
 [Interface ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 Fornece um método de retorno de chamada para `EnumMemoryRegions` relatar ao depurador o resultado de uma tentativa de enumerar uma região especificada da memória.  
  
 [Interface ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 Fornece métodos para interação com um processo de CLR de destino.  
  
 [Interface ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 Uma subclasse de `ICLRDataTarget` que é usada pela camada de serviços de acesso a dados para manipular as regiões de memória virtual no processo de destino.  
  
 [Interface ICLRDataTarget3](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 Uma subclasse de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) que fornece acesso às informações de exceção.  
  
 [Interface ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 Fornece métodos que manipulam os módulos de carregamento e descarregamento para depuração.  
  
 [Interface ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 Inclui o [método ProvideLibrary](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) método, que obtém um provedor de biblioteca de interface de retorno de chamada que permite que o CLR bibliotecas de depuração específicos da versão em tempo de execução a ser localizada e carregada na demanda.  
  
 [Interface ICLRMetadataLocator](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 A interface usada pela camada de serviços de acesso a dados para localizar metadados de assemblies em um processo de destino.  
  
 [Interface ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 Fornece métodos que permitem que os desenvolvedores depurem aplicativos no ambiente do CLR.  
  
 [Interface1 ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 Fornece métodos para depurar domínios de aplicativo.  
  
 [Interface1 ICorDebugAppDomain2](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos ByRef. Essa interface é uma extensão da interface `ICorDebugAppDomain`.  
  
 [Interface ICorDebugAppDomain3](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 Fornece métodos para trabalhar com os tipos [!INCLUDE[wrt](../../../../includes/wrt-md.md)] em um domínio de aplicativo. Essa interface é uma extensão das interfaces `ICorDebugAppDomain` e `ICorDebugAppDomain2`.  
  
 [Interface ICorDebugAppDomain4](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 Logicamente estende o [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface para obter um objeto gerenciado de um COM callable wrapper.  
  
 [Interface1 ICorDebugAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 Fornece um método que retorna um número especificado de valores `ICorDebugAppDomain` iniciando no próximo local na enumeração.  
  
 [Interface1 ICorDebugArrayValue](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 Uma subclasse de `ICorDebugHeapValue` que representa uma matriz unidimensional ou multidimensional.  
  
 [Interface1 ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 Representa um assembly.  
  
 [Interface1 ICorDebugAssembly2](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 Representa um assembly. Essa interface é uma extensão da interface `ICorDebugAssembly`.  
  
 [Interface ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 Logicamente estende o [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface para oferecer suporte para assemblies de contêiner e seus assemblies independentes. **Disponível em apenas .NET nativo.**  
  
 [Interface1 ICorDebugAssemblyEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugAssembly`.  
  
 [Interface ICorDebugBlockingObjectEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 Fornece um enumerador para obter uma lista de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estruturas.  
  
 [Interface1 ICorDebugBoxValue](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 Uma subclasse de `ICorDebugHeapValue` que representa um objeto de classe com valor boxed.  
  
 [Interface1 ICorDebugBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 Representa um ponto de interrupção em uma função ou um ponto de inspeção em um valor.  
  
 [Interface1 ICorDebugBreakpointEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugBreakpoint`.  
  
 [Interface1 ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 Representa um segmento de uma pilha de chamadas física ou lógica.  
  
 [Interface1 ICorDebugChainEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugChain`.  
  
 [Interface1 ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.  
  
 [Interface1 ICorDebugClass2](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 Representa uma classe genérica ou uma classe com um parâmetro do método do tipo <xref:System.Type>. Essa interface estende `ICorDebugClass`.  
  
 [Interface1 ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Representa um segmento de código MSIL (Microsoft Intermediate Language) ou código nativo.  
  
 [Interface1 ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 Fornece métodos que estendem os recursos de `ICorDebugCode`.  
  
 [Interface ICorDebugCode3](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 Fornece um método que estende [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) e [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) para fornecer informações sobre um valor de retorno gerenciado.  
  
 [Interface ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 Fornece um método que permite que um depurador enumerar as variáveis locais e os argumentos em uma função.  
  
 [Interface1 ICorDebugCodeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugCode`.  
  
 [Interface ICorDebugComObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 Fornece métodos para recuperar objetos da interface armazenados em cache.  
  
 [Interface1 ICorDebugContext](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 Representa um objeto de contexto. Essa interface ainda não foi implementada.  
  
 [Interface1 ICorDebugController](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 Representa um escopo, um <xref:System.Diagnostics.Process> ou um <xref:System.AppDomain>, em que o contexto de execução de código pode ser controlado.  
  
 [Interface ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 Fornece uma interface de retorno de chamada que oferece acesso a um determinado processo de destino.  
  
 [Interface ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 Logicamente estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugDataTarget3](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 Logicamente estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para fornecer informações sobre os módulos carregados. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 Define a interface base da qual derivam todos os eventos de depuração `ICorDebug`. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugEditAndContinueErrorInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 Obsoleto. Não use essa interface.  
  
 [Interface1 ICorDebugEditAndContinueSnapshot](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 Obsoleto. Não use essa interface.  
  
 [Interface1 ICorDebugEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 Serve como a interface da base abstrata para depurar enumeradores.  
  
 [Interface1 ICorDebugErrorInfoEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 Obsoleto. Não use essa interface.  
  
 [Interface1 ICorDebugEval](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 Fornece métodos para permitir que o depurador execute um código no contexto do código que está sendo depurado.  
  
 [Interface1 ICorDebugEval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 Estende `ICorDebugEval` para fornecer suporte a tipos genéricos.  
  
 [Interface ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de exceção. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 Fornece um enumerador para informações de pilha de chamadas que são inseridas em um objeto de exceção.  
  
 [Interface ICorDebugExceptionObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 Estende o [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface para fornecer informações de rastreamento de pilha de um objeto de exceção gerenciada.  
  
 [Interface1 ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 Representa um quadro na pilha atual.  
  
 [Interface1 ICorDebugFrameEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugFrame`.  
  
 [Interface1 ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 Representa uma função ou um método gerenciado.  
  
 [Interface1 ICorDebugFunction2](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 Estende `ICorDebugFunction` logicamente para fornecer suporte à depuração passo a passo Apenas Meu Código.  
  
 [Interface ICorDebugFunction3](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 Logicamente estende o [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface para fornecer acesso ao código de uma solicitação ReJIT.  
  
 [Interface1 ICorDebugFunctionBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 Estende `ICorDebugBreakpoint` para fornecer suporte a pontos de interrupção dentro de funções.  
  
 [Interface ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 Fornece um enumerador para objetos que serão coletados do lixo.  
  
 [Interface1 ICorDebugGenericValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 Uma subclasse de `ICorDebugValue` que se aplica a todos os valores. Essa interface fornece métodos Get e Set para o valor.  
  
 [Interface ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 Fornece um enumerador para um objeto que mapeia GUIDs e seus objetos `ICorDebugType` correspondentes.  
  
 [Interface1 ICorDebugHandleValue](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 Uma subclasse de `ICorDebugReferenceValue` que representa um valor de referência para o qual o depurador criou um identificador para coleta de lixo.  
  
 [Interface ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 Fornece um enumerador para objetos no heap gerenciado.  
  
 [Interface ICorDebugHeapSegmentEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 Fornece um enumerador para regiões de memória do heap gerenciado.  
  
 [Interface1 ICorDebugHeapValue](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 Uma subclasse de `ICorDebugValue` que representa um objeto coletado pelo coletor de lixo do CLR.  
  
 [Interface1 ICorDebugHeapValue2](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 Uma extensão de `ICorDebugHeapValue` que fornece suporte aos identificadores de tempo de execução.  
  
 [Interface ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 Expõe as propriedades de bloqueio de monitoramento de objetos.  
  
 [Interface ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 Representa um segmento de código IL (Intermediate Language).  
  
 [Interface ICorDebugILCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 Logicamente estende o [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) deslocamentos de interface forneça métodos que retornam o token de assinatura de variável local de uma função, e que mapeiam instrumentada IL (intermediate language) do criador de perfil para o método original IL deslocamentos.  
  
 [Interface1 ICorDebugILFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 Representa um registro de ativação do código MSIL.  
  
 [Interface1 ICorDebugILFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 Uma extensão lógica de `ICorDebugILFrame`.  
  
 [Interface ICorDebugILFrame3](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 Fornece um método que encapsula o valor de retorno de uma função.  
  
 [Interface ICorDebugILFrame4](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 Fornece métodos que permitem acessar as variáveis locais e inserir o código em um registro de ativação de código IL. Um parâmetro especifica se o depurador possui acesso às variáveis e ao código adicionados na instrumentação do criador de perfil ReJIT.  
  
 [Interface ICorDebugInstanceFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 Representa as informações de símbolo de depuração para um campo de instância. **Disponível em apenas .NET nativo.**  
  
 [Interface1 ICorDebugInternalFrame](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 Identifica os tipos de quadro para o depurador.  
  
 [Interface ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 Fornece informações sobre quadros internos, incluindo o endereço de pilha e a posição em relação ao [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objetos.  
  
 [Interface ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 Fornece informações sobre um módulo carregado. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 Fornece métodos para processar retornos de chamada do depurador.  
  
 [Interface ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 Fornece métodos para oferecer suporte à manipulação de exceção do depurador e aos assistentes de depuração gerenciados (MDAs). `ICorDebugManagedCallback2` é uma extensão lógica de `ICorDebugManagedCallback`.  
  
 [Interface ICorDebugManagedCallback3](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 Fornece um método de retorno de chamada que indica que uma notificação personalizada ativada do depurador foi gerada.  
  
 [Interface ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 Representa uma mensagem do assistente de depuração gerenciado (MDA).  
  
 [Interface ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 Representa um buffer na memória. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 Fornece informações sobre um assembly mesclado. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugMetaDataLocator](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 Fornece informações de metadados ao depurador.  
  
 [Interface1 ICorDebugModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 Representa um módulo de CLR, que é um executável ou uma biblioteca de vínculo dinâmico (DLL).  
  
 [Interface1 ICorDebugModule2](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 Serve como extensão lógica para `ICorDebugModule`.  
  
 [Interface ICorDebugModule3](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 Cria um leitor de símbolos para um módulo dinâmico.  
  
 [Interface1 ICorDebugModuleBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 Estende `ICorDebugBreakpoint` para fornecer acesso aos módulos específicos.  
  
 [Interface ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 Estende o [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface para oferecer suporte a eventos de nível de módulo. **Disponível em apenas .NET nativo.**  
  
 [Interface1 ICorDebugModuleEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugModule`.  
  
 [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 Estende o [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface para oferecer suporte a destinos de dados mutável.  
  
 [Interface1 ICorDebugNativeFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 Uma implementação especializada de `ICorDebugFrame` usada para quadros nativos.  
  
 [Interface ICorDebugNativeFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 Fornece métodos que testam relações de quadros pai e filho.  
  
 [Interface1 ICorDebugObjectEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de objetos pelos endereços virtuais relacionados (RVAs).  
  
 [Interface1 ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 Uma subclasse de `ICorDebugValue` que representa um valor que contém um objeto.  
  
 [Interface1 ICorDebugObjectValue2](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 Estende `ICorDebugObjectValue` para oferecer suporte a herança e substituição.  
  
 [Interface1 ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 Representa um processo que está executando o código gerenciado.  
  
 [Interface1 ICorDebugProcess2](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 Uma extensão lógica de `ICorDebugProcess`.  
  
 [Interface ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 Controla as notificações personalizadas do depurador.  
  
 [Interface ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 Estende o [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) local da interface para acesso de suporte para o heap gerenciado, para fornecer informações sobre a coleta de lixo de objetos gerenciados e para determinar se um depurador carrega imagens do aplicativo cache de imagem nativa.  
  
 [Interface ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 Logicamente estende o [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface para habilitar recursos como decodificar os eventos de depuração gerenciados que são codificados em eventos de exceção nativo de depuração e divisão de módulo virtual. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugProcess7](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 Fornece um método que configura o depurador para manipular atualizações de metadados na memória no processo de destino.  
  
 [Interface ICorDebugProcess8](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 Logicamente estende o [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface para habilitar ou desabilitar certos tipos de [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) retornos de chamada de exceção.  
  
 [Interface1 ICorDebugProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugProcess`.  
  
 [Interface1 ICorDebugReferenceValue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 Uma subclasse de `ICorDebugValue` que oferece suporte a tipos de referência.  
  
 [Interface ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 Representa o conjunto de registros disponíveis no computador que está executando o código no momento.  
  
 [Interface ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 Estende os recursos de `ICorDebugRegisterSet` para as plataformas de hardware que possuem mais de 64 registros.  
  
 [Interface ICorDebugRemote](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 Fornece a capacidade de iniciar ou anexar um depurador gerenciado a um processo remoto de destino.  
  
 [Interface ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 Fornece métodos que permitem a você depurar aplicativos baseados no Silverlight no ambiente do CLR.  
  
 [Interface ICorDebugRuntimeUnwindableFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 Fornece suporte para os métodos não gerenciados que exigem que o CLR (Common Language Runtime) desenrole um quadro.  
  
 [Interface ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 Fornece métodos para colocar os métodos gerenciados, ou quadros, em uma pilha de thread.  
  
 [Interface ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 Representa as informações de símbolo de depuração para um campo estático. **Disponível em apenas .NET nativo.**  
  
 [Interface1 ICorDebugStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 Representa uma etapa na execução do código que é realizada por um depurador, serve como um identificador entre a emissão e a conclusão de um comando e fornece uma maneira de cancelar uma etapa.  
  
 [Interface1 ICorDebugStepper2](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 Fornece suporte para a depuração JMC (Apenas Meu Código).  
  
 [Interface1 ICorDebugStepperEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugStepper`.  
  
 [Interface1 ICorDebugStringValue](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 Uma subclasse de `ICorDebugHeapValue` que se aplica a valores de cadeia de caracteres.  
  
 [Interface ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 Fornece métodos que podem ser usados para recuperar informações de símbolo de depuração. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugSymbolProvider2](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 Logicamente estende o [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface para recuperar informações de símbolo de depuração adicionais. **Disponível em apenas .NET nativo.**  
  
 [Interface1 ICorDebugThread](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 Representa um thread em um processo. O tempo de vida de uma instância `ICorDebugThread` é igual ao tempo de vida do thread que ela representa.  
  
 [Interface1 ICorDebugThread2](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 Serve como extensão lógica para `ICorDebugThread`.  
  
 [Interface ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 Fornece o ponto de entrada para o [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) e interfaces correspondentes.  
  
 [Interface ICorDebugThread4](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 Fornece informações de bloqueio de thread.  
  
 [Interface1 ICorDebugThreadEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugThread`.  
  
 [Interface1 ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário). Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.  
  
 [Interface ICorDebugType2](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 Estende o [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface para recuperar o identificador de tipo de um tipo base ou um tipo complexo (definido pelo usuário).  
  
 [Interface1 ICorDebugTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugType`.  
  
 [Interface ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 Fornece notificação de eventos nativos que não estão diretamente relacionados ao CLR.  
  
 "ICorDebugValue"  
 Representa um valor de leitura ou gravação no processo que está sendo depurado.  
  
 "ICorDebugValue2"  
 Estende `ICorDebugValue` para oferecer suporte a `ICorDebugType`.  
  
 [Interface ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 Estende as interfaces "ICorDebugValue" e "ICorDebugValue2" para oferecer suporte para matrizes que são maiores do que 2 GB.  
  
 "ICorDebugValueBreakpoint"  
 Estende `ICorDebugBreakpoint` para fornecer acesso a valores específicos.  
  
 "ICorDebugValueEnum"  
 Implementa métodos `ICorDebugEnum` e enumera matrizes de `ICorDebugValue`.  
  
 [Interface ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 Representa um argumento de uma função ou variável local.  
  
 [Interface ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 Fornece um enumerador para a variáveis locais e os argumentos em uma função.  
  
 [Interface ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 Recupera as informações de símbolo de depuração para uma variável. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorDebugVirtualUnwinder](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 Fornece métodos para ajudar a desenrolamento de pilha. **Disponível em apenas .NET nativo.**  
  
 [Interface ICorPublish](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 Serve como a interface geral para os processos de publicação.  
  
 [Interface ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 Representa e fornece informações sobre um domínio de aplicativo.  
  
 [Interface ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 Fornece métodos que percorrem uma coleção de objetos `ICorPublishAppDomain` existentes em um processo.  
  
 [Interface ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 Serve como a base abstrata para a publicação de enumeradores.  
  
 [Interface ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 Fornece métodos que acessam informações sobre um processo.  
  
 [Interface ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 Fornece métodos que percorrem uma coleção de objetos `ICorPublishProcess`.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Depurando coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Depurando funções estáticas globais](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Declarando enumerações](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
