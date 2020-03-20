---
title: Configurando um ambiente de criação de perfil
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
ms.openlocfilehash: 32ebb868ea64a24fba80133b1a0eb539f51cb411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176962"
---
# <a name="setting-up-a-profiling-environment"></a>Configurando um ambiente de criação de perfil
> [!NOTE]
> Houve mudanças substanciais na criação de perfil no Quadro .NET 4.  
  
 Quando um processo gerenciado (aplicativo ou serviço) é iniciado, ele carrega o tempo de execução do idioma comum (CLR). Quando a CLR é inicializada, avalia as duas variáveis ambientais a seguir para decidir se o processo deve se conectar a um profiler:  
  
- COR_ENABLE_PROFILING: O CLR se conecta a um profiler somente se essa variável de ambiente existir e for definida como 1.  
  
- COR_PROFILER: Se a verificação COR_ENABLE_PROFILING passar, a CLR se conecta ao profiler que possui este CLSID ou ProgID, que deve ter sido armazenado anteriormente no registro. A variável de ambiente COR_PROFILER é definida como uma string, como mostrado nos dois exemplos a seguir.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Para fazer o perfil de um aplicativo CLR, você deve definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER antes de executar o aplicativo. Você também deve certificar-se de que o profiler DLL está registrado.  
  
> [!NOTE]
> A partir do .NET Framework 4, os profilers não devem ser registrados.  
  
> [!NOTE]
> Para usar as versões .NET Framework 2.0, 3.0 e 3.5 nas versões .NET Framework 4 e posteriores, você deve definir a variável de ambiente COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Escopo variável de ambiente  
 Como você define as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER determinará seu escopo de influência. Você pode definir essas variáveis de uma das seguintes maneiras:  
  
- Se você definir as variáveis em uma chamada [ICorDebug::CreateProcess,](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) elas se aplicarão apenas ao aplicativo que você está executando no momento. (Eles também se aplicarão a outros aplicativos iniciados por esse aplicativo que herdam o ambiente.)  
  
- Se você definir as variáveis em uma janela Prompt de comando, elas se aplicarão a todos os aplicativos iniciados a partir dessa janela.  
  
- Se você definir as variáveis no nível do usuário, elas se aplicarão a todos os aplicativos que você iniciar com o File Explorer. Uma janela Prompt de comando que você abrir depois de definir as variáveis terá essas configurações de ambiente, assim como qualquer aplicativo que você iniciar a partir dessa janela. Para definir variáveis de ambiente no nível do usuário, clique com o botão direito do mouse **em Meu computador,** clique em **Propriedades,** clique na guia **Avançado,** clique em **Variáveis de ambiente**e adicione as variáveis à lista de variáveis do **Usuário.**  
  
- Se você definir as variáveis no nível do computador, elas se aplicarão a todos os aplicativos iniciados nesse computador. Uma janela Prompt de comando que você abrir nesse computador terá essas configurações de ambiente, assim como qualquer aplicativo que você iniciar a partir dessa janela. Isso significa que todos os processos gerenciados nesse computador começarão com o seu profiler. Para definir variáveis de ambiente no nível do computador, clique com o botão direito do mouse **em Meu computador,** clique em **Propriedades,** clique na guia **Avançado,** clique em **Variáveis de ambiente,** adicione as variáveis à lista **de variáveis** do sistema e, em seguida, reinicie o computador. Após a reinicialização, as variáveis estarão disponíveis em todo o sistema.  
  
 Se você estiver fazendo um perfil de um Serviço do Windows, você deve reiniciar o computador depois de definir as variáveis do ambiente e registrar o dLL do profiler. Para obter mais informações sobre essas considerações, consulte a seção [Perfilde um Serviço do Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Considerações adicionais  
  
- A classe profiler implementa as interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) e [ICorProfilerCallback2.](icorprofilercallback2-interface.md) Na versão .NET Framework 2.0, um `ICorProfilerCallback2`profiler deve implementar . Se isso não `ICorProfilerCallback2` acontecer, não será carregado.  
  
- Apenas um profiler pode traçar um perfil de um processo de uma só vez em um determinado ambiente. Você pode registrar dois profilers diferentes em ambientes diferentes, mas cada um deve traçar o perfil de processos separados. O profiler deve ser implementado como um DLL de servidor COM em processo, que é mapeado no mesmo espaço de endereço do processo que está sendo perfilado. Isso significa que o profiler é executado em processo. O .NET Framework não suporta nenhum outro tipo de servidor COM. Por exemplo, se um profiler quiser monitorar aplicativos de um computador remoto, ele deve implementar agentes coletores em cada computador. Esses agentes irão em lote e comunicá-los ao computador central de coleta de dados.  
  
- Como o profiler é um objeto COM que está instanciado em processo, cada aplicativo perfilado terá sua própria cópia do profiler. Portanto, uma única instância de perfil não precisa lidar com dados de vários aplicativos. No entanto, você terá que adicionar lógica ao código de registro do profiler para evitar substituições de arquivos de log de outros aplicativos perfilados.  
  
## <a name="initializing-the-profiler"></a>Inicializando o Profiler  
 Quando as verificações variáveis do ambiente passam, a CLR cria uma `CoCreateInstance` instância do profiler de forma semelhante à função COM. O profiler não é carregado através `CoCreateInstance`de uma chamada direta para . Portanto, uma chamada `CoInitialize`para , que requer a definição do modelo de rosca, é evitada. Em seguida, o CLR chama o [método ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) no profiler. A assinatura deste método é a seguinte.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 O profiler deve `pICorProfilerInfoUnk` consultar um ponteiro de interface [ICorProfilerInfo](icorprofilerinfo-interface.md) ou [ICorProfilerInfo2](icorprofilerinfo2-interface.md) e salvá-lo para que ele possa solicitar mais informações mais tarde durante a criação de perfil.  
  
## <a name="setting-event-notifications"></a>Definindo notificações de eventos  
 O profiler então chama o método [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) para especificar quais categorias de notificações ele está interessado. Por exemplo, se o profiler estiver interessado apenas em função entrar e deixar notificações e notificações de coleta de lixo, ele especifica o seguinte.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Ao definir a máscara de notificações dessa forma, o profiler pode limitar quais notificações recebe. Essa abordagem ajuda o usuário a construir um profiler simples ou de propósito especial. Ele também reduz o tempo da CPU que seria desperdiçado enviando notificações que o profiler simplesmente ignoraria.  
  
 Certos eventos de profiler são imutáveis. Isso significa que, assim que esses `ICorProfilerCallback::Initialize` eventos são definidos no retorno de chamada, eles não podem ser desligados e novos eventos não podem ser ligados. As tentativas de alterar um evento `ICorProfilerInfo::SetEventMask` imutável resultarão no retorno de um HRESULT com falha.  
  
<a name="windows_service"></a>
## <a name="profiling-a-windows-service"></a>Criação de perfil de um Serviço Windows  
 O perfil de um Serviço do Windows é como traçar um perfil de um aplicativo de tempo de execução de idioma comum. Ambas as operações de criação de perfil são habilitadas através de variáveis de ambiente. Como um Windows Service é iniciado quando o sistema operacional é iniciado, as variáveis de ambiente discutidas anteriormente neste tópico já devem estar presentes e definidas para os valores necessários antes do sistema começar. Além disso, o dLL de perfil já deve ser registrado no sistema.  
  
 Depois de definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER e registrar o DLL do profiler, você deve reiniciar o computador de destino para que o Windows Service possa detectar essas alterações.  
  
 Observe que essas alterações permitirão a criação de perfis em toda a base do sistema. Para evitar que todos os aplicativos gerenciados que posteriormente sejam executados sejam perfilados, você deve excluir as variáveis do ambiente do sistema depois de reiniciar o computador de destino.  
  
 Essa técnica também leva a todos os processos da CLR a serem perfilados. O profiler deve adicionar lógica ao seu [ICorProfilerCallback::Inicialize](icorprofilercallback-initialize-method.md) o retorno de chamada para detectar se o processo atual é de interesse. Se não for, o profiler pode falhar o retorno de chamada sem realizar a inicialização.  
  
## <a name="see-also"></a>Confira também

- [Visão geral do perfil](profiling-overview.md)
