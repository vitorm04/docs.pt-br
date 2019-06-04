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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc5171b135facfbbe901b38a19fef9e9d47699b5
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490724"
---
# <a name="setting-up-a-profiling-environment"></a>Configurando um ambiente de criação de perfil
> [!NOTE]
>  Houve alterações substanciais na criação de perfil no .NET Framework 4.  
  
 Quando um processo gerenciado (aplicativo ou serviço) é iniciado, ele carrega o common language runtime (CLR). Quando o CLR é inicializado, ele avalia as duas variáveis de ambiente a seguir para decidir se o processo deve se conectar a um criador de perfil:  
  
- COR_ENABLE_PROFILING: O CLR se conecta a um criador de perfil somente se essa variável de ambiente existe e estiver definida como 1.  
  
- COR_PROFILER: Se do COR_ENABLE_PROFILING verificar passa, o CLR se conecta ao criador de perfil que tem este CLSID ou ProgID, que deve ter sido armazenado anteriormente no registro. A variável de ambiente COR_PROFILER é definida como uma cadeia de caracteres, conforme mostrado nos dois exemplos a seguir.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Para criar o perfil de um aplicativo CLR, você deve definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER antes de executar o aplicativo. Você também deve verificar se que o profiler DLL está registrado.  
  
> [!NOTE]
>  Começando com o .NET Framework 4, os criadores de perfis não precisam ser registrados.  
  
> [!NOTE]
>  Para usar os criadores de perfis do .NET Framework versões 2.0, 3.0 e 3.5 no .NET Framework 4 e versões posteriores, você deve definir a variável de ambiente complus_profapi_profilercompatibilitysetting.  
  
## <a name="environment-variable-scope"></a>Escopo de variáveis de ambiente  
 Como você pode definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER determinará seu escopo de influência. Você pode definir essas variáveis em uma das seguintes maneiras:  
  
- Se você definir as variáveis em uma [icordebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) chamada, elas se aplicarão apenas para o aplicativo que você está executando no momento. (Eles também serão aplicadas a outros aplicativos iniciados por esse aplicativo que herda o ambiente.)  
  
- Se você definir as variáveis em uma janela de Prompt de comando, elas se aplicarão a todos os aplicativos que são iniciados a partir dessa janela.  
  
- Se você definir as variáveis no nível do usuário, elas se aplicarão a todos os aplicativos que você comece com o Explorador de arquivos. Uma janela de Prompt de comando que você abrir depois de definir as variáveis terão essas configurações de ambiente, e assim será qualquer aplicativo que você iniciar a partir dessa janela. Para definir variáveis de ambiente no nível do usuário, clique com botão direito **meu computador**, clique em **Properties**, clique no **avançado** , clique em **ambiente Variáveis**e adicione as variáveis para o **variáveis de usuário** lista.  
  
- Se você definir as variáveis no nível do computador, elas se aplicarão a todos os aplicativos que são iniciados no computador. Uma janela de Prompt de comando que você abre no computador terá essas configurações de ambiente e assim será qualquer aplicativo que você iniciar a partir dessa janela. Isso significa que cada processo gerenciado no computador será iniciado com seu criador de perfil. Para definir variáveis de ambiente no nível do computador, clique com botão direito **meu computador**, clique em **Properties**, clique no **avançado** , clique em **ambiente Variáveis**, adicione as variáveis para o **variáveis de sistema** lista e, em seguida, reinicie o computador. Após a reinicialização, as variáveis ficarão disponíveis em todo o sistema.  
  
 Se você estiver criando o perfil de um serviço do Windows, você deve reiniciar seu computador depois de definir as variáveis de ambiente e registrar a DLL do criador de perfil. Para obter mais informações sobre essas considerações, consulte a seção [criação de perfil de um serviço Windows](#windows_service).  
  
## <a name="additional-considerations"></a>Considerações adicionais  
  
- A classe do criador de perfis implementa o [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfaces. No .NET Framework versão 2.0, um criador de perfis deve implementar `ICorProfilerCallback2`. Se não estiver, `ICorProfilerCallback2` não será carregado.  
  
- Somente um criador de perfis pode analisar um processo ao mesmo tempo em um determinado ambiente. Você pode registrar dois criadores de perfis diferentes em diferentes ambientes, mas cada um deve criar o perfil de processos separados. O criador de perfil deve ser implementado como um servidor em processo COM DLL, que é mapeado no espaço de endereço do processo que está sendo analisado. Isso significa que o criador de perfil é executado em processo. O .NET Framework não oferece suporte a qualquer outro tipo de servidor COM. Por exemplo, se um criador de perfis desejar monitorar aplicativos de um computador remoto, ele deve implementar agentes coletores em cada computador. Esses agentes serão os resultados em lote e comunicá-los para o computador de coleta de dados central.  
  
- Como o criador de perfil é um objeto COM que é instanciado em processo, cada aplicativo analisado terá sua própria cópia do criador de perfil. Portanto, não tem uma instância única do criador de perfil lidar com dados de vários aplicativos. No entanto, você terá que adicionar lógica ao código de registro em log do criador de perfil para impedir que o arquivo de log é substituído por outros aplicativos de criação de perfil.  
  
## <a name="initializing-the-profiler"></a>Inicializando o Profiler  
 Quando ambas as verificações da variável de ambiente passam, o CLR cria uma instância do criador de perfil de maneira semelhante para o COM `CoCreateInstance` função. O criador de perfil não foi carregado por meio de uma chamada direta para `CoCreateInstance`. Portanto, uma chamada para `CoInitialize`, que requer a definição do modelo de threading, é evitada. O CLR, em seguida, chama o [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) método no criador de perfil. A assinatura desse método é da seguinte maneira.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 O criador de perfis deve consultar `pICorProfilerInfoUnk` para um [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ou [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) ponteiro de interface e salve-o para que ele possa solicitar mais informações posteriormente durante a criação de perfil.  
  
## <a name="setting-event-notifications"></a>Definindo notificações de eventos  
 O criador de perfil, em seguida, chama o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para especificar quais categorias de notificações ele está interessado. Por exemplo, se o criador de perfil estiver interessado somente na função entrar e sair de notificações e notificações de coleta de lixo, ele especificará o seguinte.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Definindo a máscara de notificações dessa maneira, o criador de perfil pode limitar quais notificações recebidas. Essa abordagem ajuda o usuário crie um criador de perfis simple ou com finalidade especial. Isso também reduz o tempo de CPU que seria desperdiçado enviando notificações que o criador de perfis apenas ignoraria.  
  
 Determinados eventos do criador de perfil são imutáveis. Isso significa que assim que esses eventos são definidos `ICorProfilerCallback::Initialize` retorno de chamada, eles não podem ser desativados e novos eventos não podem ser ativados. Tentativas de alterar um evento imutável resultarão em `ICorProfilerInfo::SetEventMask` retornando um HRESULT com falha.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Criação de perfil de um serviço do Windows  
 Criação de perfil de um serviço do Windows é semelhante a um aplicativo do common language runtime de criação de perfil. Ambas as operações de criação de perfil são habilitadas por meio de variáveis de ambiente. Como um serviço do Windows é iniciado quando o sistema operacional é iniciado, as variáveis de ambiente discutidas anteriormente neste tópico já deve estar presente e definido com os valores necessários antes do sistema é iniciado. Além disso, a DLL de criação de perfil já deve ser registrada no sistema.  
  
 Depois de definir as variáveis de ambiente COR_ENABLE_PROFILING e COR_PROFILER e registrar a DLL do criador de perfil, você deve reiniciar o computador de destino para que o serviço do Windows pode detectar essas alterações.  
  
 Observe que essas alterações irão ativar a criação de perfil em uma base de todo o sistema. Para impedir que todos os aplicativos gerenciados que executado subsequentemente tenha o perfil está sendo criado, você deve excluir as variáveis de ambiente do sistema depois que você reiniciar o computador de destino.  
  
 Essa técnica também leva a cada perfil de processo do CLR. O criador de perfis deve adicionar lógica ao seu [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) retorno de chamada para detectar se o processo atual é de interesse. Se não for, o criador de perfil poderá falhar o retorno de chamada sem executar a inicialização.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral da criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
