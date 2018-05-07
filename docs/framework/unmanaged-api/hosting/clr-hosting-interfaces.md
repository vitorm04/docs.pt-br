---
title: Interfaces de hospedagem CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="clr-hosting-interfaces"></a>Interfaces de hospedagem CLR
Esta seção descreve as interfaces não gerenciadas hosts podem usar para integrar o common language runtime (CLR) em seus aplicativos. As informações relativas ao .NET Framework versão 2.0 e versões posteriores. Essas interfaces habilite o host de controlar vários aspectos mais de tempo de execução que era possível nas versões 1.0 e 1.1 e fornecem muito mais integração entre o CLR e o modelo de execução do host.  
  
 No .NET Framework versão 1.0 e 1.1, o modelo de host habilitado um host não gerenciado carregar o CLR em um processo, para definir certas configurações e para receber notificações de eventos. No entanto, em geral, o host e o CLR executaram independentemente no processo. No .NET Framework versão 2.0 e versões posteriores, novas camadas de abstração permita que o host fornece muitos dos recursos fornecidos no momento, os tipos no assembly Win32 e estender o conjunto de recursos que o host pode configurar.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Fornece um método que executa um retorno de chamada para um evento registrado.  
  
 [Interface IApartmentCallback](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Fornece métodos para fazer retornos de chamada em um apartment.  
  
 [Interface IAppDomainBinding](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Fornece métodos para definição de configuração de tempo de execução.  
  
 [Interface ICatalogServices](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Fornece métodos para serviços de catalogação. (Esta interface dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.)  
  
 [Interface ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Fornece métodos que oferecem suporte a comunicação entre o host e o CLR sobre assemblies.  
  
 [Interface ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Gerencia uma lista de assemblies que são carregados do CLR e não pelo host.  
  
 [Interface ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Fornece métodos para o host para acessar e configurar vários aspectos do CLR.  
  
 [Interface ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Fornece métodos que permitem que um host associar um conjunto de tarefas com um identificador e um nome amigável.  
  
 [Interface ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Fornece métodos que permitem que o host configurar os despejos de pilha personalizado para relatório de erros.  
  
 [Interface ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Fornece métodos que permitem que um host interagir com o sistema de coleta de lixo do CLR.  
  
 [Interface ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Fornece métodos para o host avaliar e comunicar alterações nas informações de política de assemblies.  
  
 [Interface ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Permite que o host bloquear as classes gerenciadas específicos, métodos, propriedades e campos da execução de código parcialmente confiável.  
  
 [Interface ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementa um método de retorno de chamada que permite que o host notificar o CLR do status de solicitações de e/s especificados.  
  
 [Interface ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Permite que o host para condições de pressão de memória do relatório usando uma abordagem semelhante do Win32 `CreateMemoryResourceNotification` função.  
  
 [Interface ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Fornece métodos que permitem que o host registrar e cancelar o registro de retornos de chamada para eventos CLR.  
  
 [Interface ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Fornece métodos que permitem que o host especificar ações de política a ser executada no caso de falhas e tempos limite.  
  
 [Interface ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Fornece métodos que permitem que o host obter as identidades de investigação de um assembly usando as informações de identidade do assembly que é internas para o CLR, sem a necessidade de criar ou entender que a identidade.  
  
 [Interface ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Fornece métodos que permitem que o host manipular o conjunto de assemblies referenciados por um arquivo ou um fluxo usando dados de identidade do assembly que são internos para o CLR, sem a necessidade de criar ou entender essas identidades.  
  
 [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Fornece recursos semelhantes para [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), com um método adicional para definir a interface de controle de host.  
  
 [Interface ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Fornece métodos para o host para obter informações sobre tarefas solicitadas e para detectar deadlocks em sua implementação de sincronização.  
  
 [Interface ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Fornece métodos que permitem que o host para fazer solicitações do CLR, ou para fornecer notificação para o CLR sobre a tarefa associada.  
  
 [Interface ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Fornece métodos que permitem que o host solicitar explicitamente que o CLR cria uma nova tarefa, obter a tarefa em execução no momento e definir o idioma geográfico e a cultura para a tarefa.  
  
 [Interface ICLRValidator](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Fornece métodos para validar portátil imagens executáveis de (PE) e relatando erros de validação.  
  
 [Interface ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Fornece métodos para configurar o CLR.  
  
 [Interface ICorThreadpool](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Fornece métodos para acessar o pool de threads.  
  
 [Interface IDebuggerInfo](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Fornece métodos para obter informações sobre o estado dos serviços de depuração.  
  
 [Interface IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Fornece métodos para notificar o host sobre o bloqueio e desbloqueio de threads pelos serviços de depuração.  
  
 [Interface IGCHost](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Fornece métodos para obter informações sobre o sistema de coleta de lixo e para controlar alguns aspectos da coleta de lixo.  
  
 [Interface IGCHost2](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Fornece o [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) método que permite que um host definir o tamanho do segmento de coleta de lixo e o tamanho máximo da geração do sistema de coleta de lixo zero com valores maiores que `DWORD`.  
  
 [Interface IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Fornece um método que permite que o coletor de lixo solicitar o host para alterar os limites de memória virtual.  
  
 [Interface IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Fornece métodos para participação no agendamento de threads que outra forma seriam bloqueados para coleta de lixo.  
  
 [Interface IHostAssemblyManager](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Fornece métodos que permitem que um host ao especificar conjuntos de módulos (assemblies) que deve ser carregado pelo CLR ou pelo host.  
  
 [Interface IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Fornece métodos que permitem que um host ao carregar assemblies e módulos independentemente do CLR.  
  
 [Interface IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Fornece uma representação de um evento de redefinição automática implementada pelo host.  
  
 [Interface IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Fornece métodos para configurar o carregamento de assemblies e para determinar quais hospedagem interfaces com suporte no host.  
  
 [Interface IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Serve como a representação do host de uma seção crítica de threading.  
  
 [Interface IHostGCManager](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Fornece métodos que notificam o host de eventos no mecanismo de coleta de lixo implementado pelo CLR.  
  
 [Interface IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Fornece métodos que permitem interagir com portas de conclusão de e/s fornecidas pelo host do CLR.  
  
 [Interface IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Fornece métodos para o CLR solicitar refinadas alocações de heap por meio do host.  
  
 [Interface IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Fornece a implementação do host de uma representação de um evento de redefinição manual.  
  
 [Interface IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Fornece métodos para o CLR fazer solicitações de memória virtual por meio do host, em vez de usar as funções de memória virtual padrão do Win32.  
  
 [Interface IHostPolicyManager](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Fornece métodos que notificam o host das ações que o CLR executa no caso do anula, tempos limites ou falhas.  
  
 [Interface IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Habilita o CLR manter informações de contexto de segurança implementadas pelo host.  
  
 [Interface IHostSecurityManager](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Fornece métodos que permitem acesso a e o controle sobre o contexto de segurança do thread em execução no momento.  
  
 [Interface IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Fornece uma representação de um semáforo implementada pelo host.  
  
 [Interface IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Fornece métodos para o CLR criar os primitivos de sincronização chamando o host, em vez de usar as funções de sincronização do Win32.  
  
 [Interface IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Fornece métodos que permitem que o CLR para se comunicar com o host para gerenciar as tarefas.  
  
 [Interface IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Fornece métodos que permitem que o CLR trabalhar com tarefas por meio do host em vez de usar as funções de threading ou fibra do sistema operacional padrão.  
  
 [Interface IHostThreadPoolManager](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Fornece métodos para o CLR para configurar o pool de threads e para a fila de itens de trabalho para o pool de threads.  
  
 [Interface IManagedObject](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Fornece métodos para controlar um objeto gerenciado.  
  
 "IObjectHandle"  
 Fornece um método para descodificar objetos marshal-by-value de indireção.  
  
 [Interface ITypeName](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Fornece métodos para obter informações de nome de tipo. (Esta interface dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.)  
  
 [Interface ITypeNameBuilder](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Fornece métodos para criar um nome de tipo. (Esta interface dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.)  
  
 [Interface ITypeNameFactory](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Fornece métodos para deconstructing um nome de tipo. (Esta interface dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.)  
  
 "IValidator"  
 Fornece métodos para validar portátil imagens executáveis de (PE) e relatando erros de validação.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Interfaces e coclasses de hospedagem CLR preteridas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Contém tópicos que descrevem as interfaces de hospedagem fornecidas no .NET Framework versão 1.0 e 1.1.  
  
 [Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Contém tópicos que descrevem as interfaces de hospedagem fornecidas a [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].
