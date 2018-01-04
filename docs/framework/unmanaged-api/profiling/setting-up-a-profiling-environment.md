---
title: "Configurando um ambiente de criação de perfil"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc3d490284e371aefb2de712cb5721b0246caa6a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="setting-up-a-profiling-environment"></a>Configurando um ambiente de criação de perfil
> [!NOTE]
>  Houve alterações significativas para criação de perfil no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Quando um processo gerenciado (aplicativo ou serviço) é iniciado, ele carrega o common language runtime (CLR). Quando o CLR é inicializado, ele avalia as duas variáveis ambientais para decidir se o processo deve se conectar a um criador de perfil a seguir:  
  
-   COR_ENABLE_PROFILING: O CLR se conecta a um criador de perfil somente se essa variável de ambiente existe e está definida como 1.  
  
-   COR_PROFILER: Se a verificação COR_ENABLE_PROFILING passa, o CLR conecta-se para o criador de perfil que possui este CLSID ou ProgID, que deve ter sido armazenado anteriormente no registro. A variável de ambiente COR_PROFILER é definida como uma cadeia de caracteres, conforme mostrado nos dois exemplos a seguir.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Para criar o perfil de um aplicativo de CLR, você deve definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER antes de executar o aplicativo. Você também deve garantir que o criador de perfil DLL é registrado.  
  
> [!NOTE]
>  Começando com o [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], criadores de perfil não precisam ser registrado.  
  
> [!NOTE]
>  Para usar perfis de versões 2.0, 3.0 e 3.5 do .NET Framework no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] e versões posteriores, você deve definir a variável de ambiente COMPLUS_ProfAPI_ProfilerCompatibilitySetting.  
  
## <a name="environment-variable-scope"></a>Escopo de variáveis de ambiente  
 Como você pode definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER determinará o escopo de influência. Você pode definir essas variáveis em uma das seguintes maneiras:  
  
-   Se você definir as variáveis em um [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) chamada, elas serão aplicadas apenas para o aplicativo que você está executando no momento. (Eles também serão aplicadas a outros aplicativos iniciados pelo aplicativo que herdam o ambiente.)  
  
-   Se você definir as variáveis em uma janela de Prompt de comando, elas serão aplicadas a todos os aplicativos que são iniciados do que a janela.  
  
-   Se você definir as variáveis no nível do usuário, elas serão aplicadas a todos os aplicativos que você iniciar com o Explorador de arquivos. Uma janela de Prompt de comando que você abrir depois de definir as variáveis tenham essas configurações de ambiente, e também qualquer aplicativo que você iniciar a partir dessa janela. Para definir variáveis de ambiente no nível do usuário, clique com botão direito **meu computador**, clique em **propriedades**, clique no **avançado** , clique em **ambiente Variáveis**e adicionar as variáveis para o **variáveis** lista.  
  
-   Se você definir as variáveis no nível do computador, elas serão aplicadas a todos os aplicativos que são iniciados no computador. Uma janela de Prompt de comando que você abrir no computador terá essas configurações de ambiente e também qualquer aplicativo que você iniciar a partir dessa janela. Isso significa que todos os processos gerenciados no computador serão iniciado com o criador de perfil. Para definir variáveis de ambiente no nível do computador, clique com botão direito **meu computador**, clique em **propriedades**, clique no **avançado** , clique em **ambiente Variáveis**, adicione as variáveis para o **variáveis de sistema** lista e, em seguida, reinicie o computador. Depois de reiniciar, as variáveis será disponível em todo o sistema.  
  
 Se você estiver criando um perfil para um serviço do Windows, você deve reiniciar seu computador depois de definir as variáveis de ambiente e registrar a DLL do criador de perfil. Para obter mais informações sobre essas considerações, consulte a seção [criação de perfil de um serviço do Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Considerações adicionais  
  
-   A criador de perfil a classe implementa o [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfaces. O .NET Framework versão 2.0, um criador de perfil deve implementar `ICorProfilerCallback2`. Se não estiver, `ICorProfilerCallback2` não será carregado.  
  
-   Somente um criador de perfil pode analisar um processo de uma vez em um determinado ambiente. Você pode registrar os dois perfis diferentes em ambientes diferentes, mas cada uma deve criar o perfil de processos separados. O criador de perfil deve ser implementado como um DLL, que é mapeado no espaço de endereço do processo que está sendo criado o perfil do servidor em processo COM. Isso significa que o criador de perfil é executado em processo. O .NET Framework não dá suporte a qualquer outro tipo de servidor COM. Por exemplo, se quiser um criador de perfil monitorar os aplicativos de um computador remoto, ele deve implementar agentes coletores em cada computador. Esses agentes serão resultados de lote e comunicar-se ao computador de coleta de dados central.  
  
-   Como o criador de perfil é um objeto COM que é instanciado no processo, cada aplicativo perfilado terá sua própria cópia do criador de perfil. Portanto, uma instância única do criador de perfil não precisa lidar com dados de vários aplicativos. No entanto, você precisará adicionar a lógica para o código de log do criador de perfil para impedir que o arquivo de log substitui de outros aplicativos de perfil.  
  
## <a name="initializing-the-profiler"></a>Inicializando o criador de perfil  
 Ao passarem as verificações de variável de ambiente, o CLR cria uma instância do criador de perfil de maneira semelhante para o COM `CoCreateInstance` função. O criador de perfil não foi carregado por meio de uma chamada direta para `CoCreateInstance`. Portanto, uma chamada para `CoInitialize`, que requer a definição do modelo de threading é evitada. O CLR, em seguida, chama o [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) método no criador de perfil. A assinatura do método é o seguinte.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 O criador de perfil deve consultar `pICorProfilerInfoUnk` para um [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) ponteiro de interface e salvá-lo para que ele possa solicitar mais informações posteriormente, durante a criação de perfil.  
  
## <a name="setting-event-notifications"></a>Notificações de eventos de configuração  
 O criador de perfil, em seguida, chama o [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para especificar quais categorias de notificações está interessada em. Por exemplo, se o criador de perfil está interessado apenas em função entram e saem notificações e notificações de coleta de lixo, especifica o seguinte.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Definindo a máscara de notificações dessa maneira, o criador de perfil pode limitar quais notificações recebidas. Essa abordagem ajuda o usuário a criar um criador de perfil simple ou especial. Isso também reduz o tempo de CPU que poderia ser perdido enviar notificações que o criador de perfil deve ignorar.  
  
 Determinados eventos do criador de perfil são imutáveis. Isso significa que, assim que esses eventos são definidos `ICorProfilerCallback::Initialize` retorno de chamada, não pode ser desativadas e novos eventos não podem ser ativados. Tentativas de alterar um evento imutável resultará em `ICorProfilerInfo::SetEventMask` retornar uma falha de HRESULT.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Criação de perfil de um serviço do Windows  
 Criação de perfil de um serviço do Windows é como um aplicativo de tempo de execução de linguagem comum de criação de perfil. As duas operações de criação de perfil são habilitadas por meio de variáveis de ambiente. Como um serviço do Windows é iniciado quando o sistema operacional é iniciado, as variáveis de ambiente discutidos anteriormente neste tópico já deve estar presente e definida como os valores necessários antes que o sistema é iniciado. Além disso, a DLL de criação de perfil já deve estar registrada no sistema.  
  
 Depois de definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER e registrar a DLL do criador de perfil, você deverá reiniciar o computador de destino para que o serviço do Windows pode detectar essas alterações.  
  
 Observe que essas alterações permitirá a criação de perfil em uma base de todo o sistema. Para impedir que todos os aplicativos gerenciados subsequentemente executado a partir com criação de perfil, você deve excluir as variáveis de ambiente do sistema depois que você reiniciar o computador de destino.  
  
 Essa técnica também leva a cada processo CLR obtendo atribuído. O criador de perfil deve adicionar a lógica para sua [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada para detectar se o processo atual é de interesse. Se não for, o criador de perfil pode falhar o retorno de chamada sem executar a inicialização.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
