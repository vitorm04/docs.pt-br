---
title: Criadores de perfil CLR e aplicativos da Windows Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db1152e82edde34dc8dbaba09f20b9f769dffbca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-profilers-and-windows-store-apps"></a>Criadores de perfil CLR e aplicativos da Windows Store
Este tópico discute o que você precisa pensar sobre quando gravar ferramentas de diagnóstico que analisam gerenciado código em execução dentro de um aplicativo da Windows Store.  Ele também fornece diretrizes para modificar suas ferramentas de desenvolvimento para que eles continuem a funcionar quando você executá-los nos aplicativos da Windows Store.  Para entender essas informações, é melhor que se você estiver familiarizado com o idioma em tempo de execução de criação de perfil API comum, você já tiver usado essa API em uma ferramenta de diagnóstica que é executado corretamente em relação a aplicativos de área de trabalho do Windows e você agora está interessado em modificando a ferramenta para executar corretamente em aplicativos da Windows Store.  
  
 Este tópico é composto pelas seguintes seções:  
  
 [Introdução](#Intro)  
 [Arquitetura e terminologia](#Arch)  
 [Dispositivos Windows RT](#RT)  
[Consumindo APIs de tempo de execução do Windows](#Consuming)  
[Carregar o DLL do criador de perfil](#Loading)  
 [Considerações comuns de inicialização e anexar cargas](#Common)  
 [Carga de inicialização](#Startup)  
 [Anexar carga](#Attach)  
[Em execução dentro do aplicativo da Windows Store](#Running)  
 [Usar as APIs de aplicativo da Windows Store](#APIs)  
 [Permissões reduzidas](#Permissions)  
 [Comunicação entre processos](#Interprocess)  
 [Nenhuma notificação de desligamento](#Shutdown)  
[Arquivos de metadados de tempo de execução do Windows](#Metadata)  
 [WinMDs gerenciados e não gerenciados](#WMDs)  
 [Arquivos WinMD aparência módulos CLR](#CLRModules)  
 [Ler metadados do WinMDs](#Reading)  
 [Modificando os metadados do WinMDs](#Modifying)  
 [Resolvendo referências de assembly com WinMDs](#Resolving)  
[Criadores de perfil de memória](#Profilers)  
 [ForceGC cria um thread gerenciado](#ForceGC)  
 [ConditionalWeakTableReferences](#WeakTable)  
[Conclusão](#Conclusion)  
[Recursos](#Resources)  
  
<a name="Intro"></a>   
## <a name="introduction"></a>Introdução  
 Se feitas após o parágrafo introdutório, em seguida, você está familiarizado com a API de criação de perfil CLR.  Você já escreveu uma ferramenta de diagnóstico que funciona bem em aplicativos de área de trabalho gerenciados.  Agora você estiver curioso sobre o que fazer para que a ferramenta funciona com um aplicativo da Windows Store gerenciado.  Talvez você já tentou executar esse trabalho e descobrir que não é uma tarefa simples.  Na verdade, há várias considerações que podem não ser óbvias para todos os desenvolvedores de ferramentas.  Por exemplo:  
  
-   Executar aplicativos da Windows Store em um contexto com permissões reduzidas severos.  
  
-   Arquivos de metadados do Windows têm características exclusivas em comparação com os módulos gerenciados tradicionais.  
  
-   Aplicativos da Windows Store têm o hábito de suspender a mesmos quando interatividade cair.  
  
-   Os mecanismos de comunicação entre processos poderão não funcionar por vários motivos.  
  
 Este tópico lista as coisas que você precisa conhecer e como lidar com eles corretamente.  
  
 Se você estiver familiarizado com a API de criação de perfil CLR, vá para os recursos no final deste tópico para localizar mais informações introdutórias.  
  
 Fornece detalhes sobre as APIs específicas do Windows e como eles devem ser usados também está fora do escopo deste tópico.  Considere este ponto de partida do tópico e consulte o MSDN para saber mais sobre quaisquer APIs do Windows referenciada aqui.  
  
<a name="Arch"></a>   
## <a name="architecture-and-terminology"></a>Arquitetura e terminologia  
 Normalmente, uma ferramenta de diagnóstico tem uma arquitetura semelhante à mostrada na ilustração a seguir. Ele usa o termo "profiler", mas muitas dessas ferramentas vá além de desempenho comum ou o perfil de memória em áreas como cobertura de código, simular as estruturas de objetos, viajar depuração, o aplicativo de monitoramento e assim por diante.  Para simplificar, este tópico continuará para se referir a todas essas ferramentas como criadores de perfil.  
  
 A seguinte terminologia é usada ao longo deste tópico:  
  
 Aplicativo  
 Este é o aplicativo que está analisando o criador de perfil.  Normalmente, o desenvolvedor do aplicativo agora está usando o criador de perfil para ajudar a diagnosticar problemas com o aplicativo.  Tradicionalmente, esse aplicativo seria um aplicativo de área de trabalho do Windows, mas neste tópico, estamos examinando aplicativos da Windows Store.  
  
 DLL do criador de perfil  
 Este é o componente que é carregado no espaço de processo do aplicativo que está sendo analisado.  Esse componente, também conhecido como o criador de perfil de "agente" implementa a [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[ICorProfilerCallback Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2,3, etc.) interfaces e consome o [ ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2,3, etc.) interfaces para coletar dados sobre o aplicativo analisado e possivelmente modificar os aspectos do comportamento do aplicativo.  
  
 Criador de perfil da interface do usuário  
 Este é um aplicativo de área de trabalho que o criador de perfil usuário interage com.  Ele é responsável por exibir o status do aplicativo para o usuário e dar ao usuário os meios para controlar o comportamento do aplicativo analisado.  Este componente sempre é executado em seu próprio espaço de processo, separado do espaço de processo do aplicativo que está sendo analisado.  A interface do usuário do criador de perfil também pode atuar como o "anexar gatilho," qual é o processo que chama o [Iclrprofiling](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método para fazer com que o aplicativo analisado para carregar a DLL do criador de perfil nos casos em que o criador de perfil DLL não carregar na inicialização.  
  
> [!IMPORTANT]
>  Interface de usuário do criador de perfil deve permanecer um aplicativo de área de trabalho do Windows, mesmo quando ele é usado para controle e relatórios em um aplicativo da Windows Store.  Não espere poder empacotar e enviar sua ferramenta de diagnóstico na Windows Store.  A ferramenta precisa fazer coisas que aplicativos da Windows Store não podem fazer, e muitas dessas coisas residem dentro de sua interface do usuário do criador de perfil.  
  
 Ao longo deste documento, o exemplo de código pressupõe que:  
  
-   A DLL do criador de perfil está escrito em C++, porque ele deve ser uma DLL nativa, de acordo com os requisitos da API de criação de perfil do CLR.  
  
-   Interface de usuário do criador de perfil é gravado em c#.  Isso não é necessário, mas porque não há requisitos em um idioma para o processo do criador de perfil da interface do usuário, por que não escolher um idioma concisa e simples?  
  
<a name="RT"></a>   
### <a name="windows-rt-devices"></a>Dispositivos Windows RT  
 Dispositivos Windows RT bastante estão bloqueados.  Criadores de perfis de terceiros simplesmente não podem ser carregados em dispositivos.  Este documento se concentra em PCs com Windows 8.  
  
<a name="Consuming"></a>   
## <a name="consuming-windows-runtime-apis"></a>Consumindo APIs de tempo de execução do Windows  
 Em um número de cenários discutidos nas seções a seguir, o seu aplicativo de área de trabalho do criador de perfil da interface do usuário precisa consumir algumas novas APIs do Windows Runtime.  Convém consultar a documentação para entender quais APIs de tempo de execução do Windows pode ser usado em aplicativos de desktop e, se seu comportamento é diferente quando chamado a partir de aplicativos de área de trabalho e da Windows Store apps.  
  
 Se a interface do usuário do criador de perfil é escrito em código gerenciado, haverá algumas etapas, que você precisará fazer com que o consumo fácil essas APIs do Windows Runtime.  Consulte o [gerenciados aplicativos de desktop e Windows Runtime](http://go.microsoft.com/fwlink/?LinkID=271858) artigo para obter mais informações.  
  
<a name="Loading"></a>   
## <a name="loading-the-profiler-dll"></a>Carregar o DLL do criador de perfil  
 Esta seção descreve como a interface de usuário do criador de perfil faz com que o aplicativo da Windows Store carregar a DLL do criador de perfil.  O código discutido nesta seção pertence em seu aplicativo de área de trabalho do criador de perfil da interface do usuário e, portanto, envolve o uso de APIs do Windows que estão seguros para aplicativos de desktop, mas não necessariamente seguros para aplicativos da Windows Store.  
  
 Interface de usuário do criador de perfil pode fazer com que o DLL de criador de perfil a ser carregado no espaço de processo do aplicativo de duas maneiras:  
  
-   Na inicialização do aplicativo, pois controlada por variáveis de ambiente.  
  
-   Anexando ao aplicativo após a inicialização for concluída, chamando o [Iclrprofiling](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método.  
  
 Um dos seus obstáculos primeiro obterá carga de inicialização e carregar anexar o DLL do criador de perfil funcione corretamente com aplicativos da Windows Store.  As duas formas de carregamento compartilham algumas considerações especiais em comum, então vamos começar com eles.  
  
<a name="Common"></a>   
### <a name="common-considerations-for-startup-and-attach-loads"></a>Considerações comuns de inicialização e anexar cargas  
 **O DLL do criador de perfil de assinatura**  
 Quando o Windows tenta carregar o DLL do criador de perfil, ele verifica se a DLL do criador de perfil está assinado corretamente.  Caso contrário, o carregamento falhará por padrão. Há duas formas de fazer isso:  
  
-   Certifique-se de que a DLL do criador de perfil está assinado.  
  
-   Informe o usuário que eles devem instalar uma licença de desenvolvedor na sua máquina Windows 8 antes de usar a ferramenta.  Isso pode ser feito automaticamente pelo Visual Studio ou manualmente em um prompt de comando.  Para obter mais informações, consulte [obter uma licença de desenvolvedor](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Permissões do sistema de arquivos**  
 Aplicativo da Windows Store deve ter permissão para carregar e executar o DLL do criador de perfil do local no sistema de arquivos no qual ele reside.  Por padrão, o aplicativo da Windows Store não tem essa permissão na maioria dos diretórios e qualquer falha ao tentar carregar a DLL do criador de perfil produzirá uma entrada no log de eventos de aplicativo do Windows que tem a seguinte aparência:  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 Em geral, os aplicativos da Windows Store só têm permissão para acessar um conjunto limitado de locais no disco.  Cada aplicativo da Windows Store pode acessar suas próprias pastas de dados de aplicativo, bem como algumas outras áreas no sistema de arquivos para o qual todos os aplicativos da Windows Store com acesso concedidos.  É aconselhável instalar a DLL do criador de perfil e suas dependências em arquivos de programas ou arquivos de programa (x86), porque todos os aplicativos da Windows Store têm permissões read e execute existe por padrão.  
  
<a name="Startup"></a>   
### <a name="startup-load"></a>Carga de inicialização  
 Normalmente, em um aplicativo de área de trabalho, sua interface de usuário do criador de perfil solicita uma carga de inicialização da DLL criador de perfil com a inicialização de um bloco de ambiente que contém as variáveis de ambiente de API de criação de perfil CLR necessárias (ou seja, `COR_PROFILER`, `COR_ENABLE_PROFILING`, e `COR_PROFILER_PATH`), e em seguida, criando um novo processo com esse bloco de ambiente.  O mesmo é verdadeiro para aplicativos da Windows Store, mas os mecanismos são diferentes.  
  
 **Não são executados com privilégios elevados**  
 Se o processo tenta gerar o aplicativo da Windows Store B de processo, o processo deve ser executado em integridade média nível, não no nível de integridade alto (isto é, não elevado).  Isso significa que a interface do usuário do criador de perfil deve ser executado no nível de integridade média, ou ele deve gerar outro processo de área de trabalho em nível de integridade médias para cuidar de iniciar o aplicativo da Windows Store.  
  
 **Escolher um aplicativo da Windows Store ao perfil**  
 Primeiro, você desejará peça ao seu usuário profiler qual aplicativo da Windows Store para iniciar.  Para aplicativos de área de trabalho, talvez você mostra uma caixa de diálogo de procura de arquivo e o usuário deve localizar e selecionar um arquivo .exe.  Mas os aplicativos da Windows Store são diferentes e usar uma caixa de diálogo de procura não faz sentido.  Em vez disso, é melhor Mostrar ao usuário uma lista de aplicativos da Windows Store instalado para que o usuário selecione.  
  
 Você pode usar o [PackageManager classe](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) para gerar essa lista.  `PackageManager`é uma classe de tempo de execução do Windows que está disponível para aplicativos de desktop e, na verdade é *somente* disponível para aplicativos de desktop.  
  
 O exemplo a seguir ode de uma interface de usuário de criador de perfil hipotético gravado como um aplicativo de área de trabalho no c# yses a `PackageManager` para gerar uma lista de aplicativos do Windows:  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **Especificando o bloco de ambiente personalizado**  
 Uma nova interface de COM, [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), permite que você personalize o comportamento de execução de um aplicativo da Windows Store para facilitar a algumas formas de diagnóstico.  Um de seus métodos, [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), permite que você transmitir um bloco de ambiente para o aplicativo da Windows Store quando ele é iniciado, juntamente com outros efeitos útil como desabilitar a suspensão do processo automático.  O bloco de ambiente é importante porque é onde você precisa especificar as variáveis de ambiente (`COR_PROFILER`, `COR_ENABLE_PROFILING`, e `COR_PROFILER_PATH)`) usado pelo CLR para carregar a DLL do criador de perfil.  
  
 Considere o seguinte trecho de código:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Há dois itens que você precisará obter direita:  
  
-   `packageFullName`pode ser determinado durante a iteração sobre os pacotes e captura `package.Id.FullName`.  
  
-   `debuggerCommandLine`é um pouco mais interessante.  Para transmitir o bloco de ambiente personalizado para o aplicativo da Windows Store, você precisa gravar seu próprio simplista depurador fictício.  Cria o Windows, o aplicativo da Windows Store suspenso e, em seguida, anexa o depurador iniciando o depurador com uma linha de comando, como neste exemplo:  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     onde `-p 1336` significa que o aplicativo da Windows Store tem 1336 de ID de processo, e `-tid 1424` significa 1424 de ID do Thread for o thread que está suspenso.  O depurador fictício seria analisar ThreadID na linha de comando, retomar thread e saia.  
  
     Eis aqui alguns exemplos de código C++ para fazer isso (certifique-se de adicionar a verificação de erro!):  
  
    ```cpp  
    int wmain(int argc, wchar_t* argv[])  
    {      
        // …  
        // Parse command line here  
        // …  
  
        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,   
                                                                  FALSE /* bInheritHandle */, nThreadID);  
        ResumeThread(hThread);  
        CloseHandle(hThread);  
        return 0;  
    }  
    ```  
  
     Você precisará implantar esse depurador fictício como parte de sua instalação da ferramenta de diagnóstico e, em seguida, especifique o caminho para esse depurador o `debuggerCommandLine` parâmetro.  
  
 **Iniciando o aplicativo da Windows Store**  
 Finalmente chegou o momento de iniciar o aplicativo da Windows Store. Se você já já tentou fazer isso, você deve ter notado que [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425\(v=vs.85\).aspx) não como criar um processo de aplicativo da Windows Store.  Em vez disso, você precisará usar o [IApplicationActivationManager::ActivateApplication](https://msdn.microsoft.com/library/windows/desktop/Hh706903\(v=vs.85\).aspx) método.  Para fazer isso, você precisará obter a ID de modelo de usuário do aplicativo do aplicativo da Windows Store que você está iniciando.  E isso significa que você precisará fazer um pouco aprofundar-se por meio de manifesto.  
  
 Ao iterar em seus pacotes (consulte "Escolhendo um repositório de aplicativo ao perfil do Windows" a [carga de inicialização](#Startup) seção anterior), você talvez queira coletar o conjunto de aplicativos contidos no manifesto do pacote atual:  
  
```csharp  
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";  
  
AppxPackaging.IStream manifestStream;  
SHCreateStreamOnFileEx(  
                    manifestPath,  
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE  
                    0,              // file creation attributes  
                    false,          // fCreate  
                    null,           // reserved  
                    out manifestStream);  
  
IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);  
  
IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();  
```  
  
 Sim, um pacote pode ter vários aplicativos, e cada aplicativo tem sua própria ID de modelo de usuário do aplicativo.  Assim você vai querer peça ao seu usuário da qual aplicativo ao perfil e obter a ID de modelo de usuário do aplicativo do aplicativo específico:  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
…  
```  
  
 Finalmente, agora você tem o que você precisa iniciar o aplicativo da Windows Store:  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **Lembre-se de chamar DisableDebugging**  
 Quando você chama [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), você fez uma promessa que você seria limpeza chamando o [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) método, portanto certifique-se de fazer que quando a sessão de criação de perfil está acima.  
  
<a name="Attach"></a>   
### <a name="attach-load"></a>Anexar carga  
 Quando a interface do usuário do criador de perfil deseja anexar o DLL do criador de perfil a um aplicativo que já foi iniciada em execução, ele usa [Iclrprofiling](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  O mesmo se aplica aos aplicativos da Windows Store.  Mas, além das considerações comuns listadas anteriormente, verifique se o aplicativo da Windows Store de destino não está suspenso.  
  
 **EnableDebugging**  
 Assim como acontece com carga de inicialização, chame o [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) método.  Ele não é necessário para passar um bloco de ambiente, mas você precisa de um dos seus outros recursos: desabilitar a suspensão do processo automático.  Caso contrário, quando a interface do usuário do criador de perfil chama [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), o aplicativo da Windows Store de destino pode ser suspenso.  Na verdade, isso é provável se o usuário agora está interagindo com a interface de usuário do criador de perfil e o aplicativo da Windows Store não está ativo em qualquer uma das telas do usuário.  E se a Windows Store de aplicativo está suspenso, ele não poderá responder a qualquer sinalizam que o CLR envia a ele para anexar a DLL do criador de perfil.  
  
 Portanto, você desejará fazer algo assim:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 Essa é a mesma chamada que você faria para o caso de carga de inicialização, exceto que você não especificar uma linha de comando do depurador ou um bloco de ambiente.  
  
 **DisableDebugging**  
 Como sempre, não se esqueça de chamar [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) quando a sessão de criação de perfil é concluída.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Em execução dentro do aplicativo da Windows Store  
 Assim o aplicativo da Windows Store, por fim, carregou a DLL do criador de perfil.  Agora que a DLL do criador de perfil deve ser apresentado como reproduzir pelas regras de diferentes necessárias para aplicativos da Windows Store, incluindo qual APIs são permitidas e como executar com permissões reduzidas.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Usar as APIs de aplicativo da Windows Store  
 Quando você navega a API do Windows, você observará que todas as APIs é documentada como sendo aplicáveis a aplicativos de área de trabalho, aplicativos da Windows Store ou ambos.  Por exemplo, o **requisitos** seção da documentação para o [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) função indica que a função se aplica a apenas os aplicativos de área de trabalho. Em contraste, o [InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx) função está disponível para aplicativos de área de trabalho e aplicativos da Windows Store.  
  
 Ao desenvolver a DLL do criador de perfil, tratá-lo como se fosse um aplicativo da Windows Store e usar apenas as APIs que estão documentados como disponíveis para aplicativos da Windows Store.  Analisar as dependências (por exemplo, você pode executar `link /dump /imports` em sua DLL do criador de perfil para auditar) e procure a documentação para ver qual das suas dependências são okey e que não são.  Na maioria dos casos, seu violações podem ser corrigidas, simplesmente substituindo-os com um formulário mais recente da API que é documentado como seguro (por exemplo, substituindo [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) com [ InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx)).  
  
 Você observará que o DLL do criador de perfil chama algumas APIs que se aplicam a apenas os aplicativos de área de trabalho e ainda parecem funcionar mesmo quando a DLL do criador de perfil é carregado dentro de um aplicativo da Windows Store.  Lembre-se de que ele é arriscado para usar a API não documentado para uso com aplicativos da Windows Store em sua DLL do criador de perfil quando carregado em um processo de aplicativo da Windows Store:  
  
-   Não há garantia de que essas APIs funcionem quando chamado no contexto exclusivo que executam aplicativos da Windows Store no.  
  
-   Essas APIs podem não funcionar consistentemente quando chamado de diferentes processos de aplicativo da Windows Store.  
  
-   Essas APIs podem parecer funcionar bem em aplicativos da Windows Store na versão atual do Windows, mas pode quebrar ou desabilitado em versões futuras do Windows.  
  
 O melhor conselho é corrigir todas as suas violações e evitar o risco.  
  
 Você pode achar que é absolutamente não pode fazer sem uma API específica e não é possível localizar um substituto adequado para aplicativos da Windows Store.  Nesse caso, no mínimo:  
  
-   Testar, testar, teste os daylights vida sem o uso dessa API.  
  
-   Entender a API de repente pode quebrar ou desaparecer se chamado de dentro da Windows Store apps em versões futuras do Windows.  Isso não considerado um problema de compatibilidade pela Microsoft e suporte de seu uso não será uma prioridade.  
  
<a name="Permissions"></a>   
### <a name="reduced-permissions"></a>Permissões reduzidas  
 Ele está fora do escopo deste tópico para listar todas as maneiras diferentes de permissões de aplicativo da Windows Store de aplicativos de área de trabalho.  Mas certamente o comportamento será diferente toda vez que a DLL do criador de perfil (quando carregado em um aplicativo da Windows Store em comparação com um aplicativo de área de trabalho) tenta acessar recursos.  O sistema de arquivos é o exemplo mais comum.  Existem, mas alguns coloca no disco que um determinado aplicativo da Windows Store é permitido acessar (consulte [acesso e permissões de arquivo (aplicativos do Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), e a DLL do criador de perfil estará sob as mesmas restrições.  Teste minuciosamente seu código.  
  
<a name="Interprocess"></a>   
### <a name="inter-process-communication"></a>Comunicação entre processos  
 Conforme mostrado no diagrama no início deste documento, a DLL do criador de perfil (carregado no espaço de processo do aplicativo da Windows Store) provavelmente, será necessário para se comunicar com o criador de perfil da interface do usuário (em execução em um espaço de processo do aplicativo de área de trabalho separado) por meio de seu próprio processo entre personalizado canal de comunicação entre processos (IPC).  A interface do usuário do criador de perfil envia sinais para a DLL do criador de perfil para modificar seu comportamento e a DLL do criador de perfil envia dados de aplicativo da Windows Store analisado para a interface do usuário do criador de perfil de pós-processamento e exibir para o criador de perfil usuário.  
  
 A maioria dos criadores de perfil precisam trabalhar dessa forma, mas suas opções para mecanismos IPC são mais limitadas, quando a DLL do criador de perfil é carregado em um aplicativo da Windows Store.  Por exemplo, pipes nomeados não fazem parte do aplicativo da Windows Store SDK, portanto você não pode usá-los.  
  
 Mas, naturalmente, os arquivos estão no, embora de maneira mais limitada.  Eventos também estão disponíveis.  
  
 **Comunicando-se através de arquivos**  
 A maioria dos seus dados provavelmente passarão entre o DLL do criador de perfil e o criador de perfil da interface do usuário por meio de arquivos.  A chave é escolher um local de arquivo que leu o DLL do criador de perfil (no contexto de um aplicativo da Windows Store) e a interface do usuário do criador de perfil e o acesso de gravação.  Por exemplo, o caminho da pasta temporária é um local que podem acessar o DLL do criador de perfil e o criador de perfil de interface do usuário, mas nenhum outro pacote de aplicativo da Windows Store pode acessar (Protegendo informações ao que log de outros pacotes de aplicativos da Windows Store).  
  
 O criador de perfil de interface do usuário e a DLL do criador de perfil podem determinar o caminho independentemente.  A interface do usuário do criador de perfil, quando ele é iterado por todos os pacotes instalados para o usuário atual (consulte o código de exemplo anterior), obtém acesso para o `PackageId` classe, da qual o caminho da pasta temporária pode ser derivado com o código semelhante a este trecho de código.  (Como sempre, verificação de erros é omitida para fins de brevidade).  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 Enquanto isso, a DLL do criador de perfil pode fazer basicamente a mesma coisa, se pudesse mais facilmente obtém o [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) classe usando o [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) propriedade.  
  
 **Comunicação por meio de eventos**  
 Se desejar que a semântica de sinalização simple entre o criador de perfil da interface do usuário e a DLL do criador de perfil, você pode usar os eventos dentro de aplicativos da Windows Store, bem como aplicativos de desktop.  
  
 O DLL do criador de perfil, você pode simplesmente chamar o [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx) função para criar um evento nomeado com qualquer nome que desejar.  Por exemplo:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Interface de usuário do criador de perfil, em seguida, precisa localizar esse evento nomeado no namespace do aplicativo da Windows Store.  Por exemplo, a interface do usuário do criador de perfil poderia chamar [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx), especificando o nome do evento como  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>`é o SID do AppContainer do aplicativo da Windows Store.  Uma seção anterior deste tópico mostrou como iterar sobre os pacotes instalados para o usuário atual.  Esse código de exemplo, você pode obter a packageId.  E o packageId, você pode obter o `<acSid>` com o código semelhante ao seguinte:  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
<a name="Shutdown"></a>   
### <a name="no-shutdown-notifications"></a>Nenhuma notificação de desligamento  
 Quando em execução dentro de um aplicativo da Windows Store, a DLL do criador de perfil não deve confiar na [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) ou até mesmo [DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583\(v=vs.85\).aspx) (com `DLL_PROCESS_DETACH`) que está sendo chamado para notificar o DLL do criador de perfil Se o aplicativo da Windows Store está sendo encerrado.  Na verdade, você deve esperar que eles nunca serão chamados.  Historicamente, muitos DLLs do criador de perfil usaram essas notificações como locais práticos liberar caches para disco, fechar arquivos, enviar notificações de volta para a interface do usuário do criador de perfil, etc.  Mas o DLL do criador de perfil deve ser organizado de forma diferente.  
  
 A DLL do criador de perfil deve ser informações de log conforme ele passa.  Por motivos de desempenho, você talvez queira lote informações na memória e disco à medida que cresce o lote de tamanho além do limite de liberação.  Mas suponha que todas as informações ainda não foram liberadas para disco podem ser perdidas.  Isso significa que você vai querer selecionar seu limite de maneira inteligente e que a interface do usuário do criador de perfil deve ser protegido para lidar com informações incompletas gravadas pela DLL do criador de perfil.  
  
<a name="Metadata"></a>   
## <a name="windows-runtime-metadata-files"></a>Arquivos de metadados de tempo de execução do Windows  
 Está fora do escopo deste documento para entrar em detalhes sobre quais metadados de tempo de execução do Windows (WinMD) são arquivos.    Esta seção é limitada a como a API de criação de perfil CLR reage quando arquivos WinMD são carregados pelo aplicativo da Windows Store que está analisando o DLL do criador de perfil.  
  
<a name="WMDs"></a>   
### <a name="managed-and-non-managed-winmds"></a>WinMDs gerenciados e não gerenciados  
 Se um desenvolvedor usa o Visual Studio para criar um novo projeto de componente de tempo de execução do Windows, uma compilação desse projeto produz um arquivo de WinMD que descreve os metadados (as descrições do tipo de classes, interfaces, etc.) criados pelo desenvolvedor.  Se este projeto é um projeto de idioma gerenciado escrito em c# ou VB, esse mesmo arquivo de WinMD também contém a implementação desses tipos (o que significa que ele contém IL compilado a partir de código-fonte do desenvolvedor).  Esses arquivos são conhecidos como arquivos de WinMD gerenciados.  Eles são interessantes em que eles contêm metadados de tempo de execução do Windows e a implementação subjacente.  
  
 Por outro lado, se um desenvolvedor cria um projeto de componente de tempo de execução do Windows para C++, uma compilação desse projeto produz um arquivo de WinMD que contém apenas metadados e a implementação é compilada em uma DLL nativa separada.  Da mesma forma, os arquivos WinMD incluídos no SDK do Windows contêm apenas os metadados, com a implementação compilada em DLLs nativas separadas que é fornecido como parte do Windows.  
  
 As informações a seguir se aplica a ambos os WinMDs gerenciados, que contêm metadados e a implementação, e WinMDs não gerenciado, que contêm apenas os metadados.  
  
<a name="CLRModules"></a>   
### <a name="winmd-files-look-like-clr-modules"></a>Arquivos WinMD aparência módulos CLR  
 Diz respeito o CLR, todos os arquivos WinMD são módulos.  Assim, a API de criação de perfil CLR informa a DLL do criador de perfil ao carregar arquivos WinMD e quais são seus ModuleIDs, da mesma maneira que para outros módulos gerenciados.  
  
 A DLL do criador de perfil pode distinguir arquivos WinMD de outros módulos, chamando o [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) método e inspecionando o `pdwModuleFlags` parâmetro de saída a [COR_PRF_MODULE_WINDOWS_ Tempo de execução](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) sinalizador.  (Ele é definido somente se o ModuleID representa um WinMD.)  
  
<a name="Reading"></a>   
### <a name="reading-metadata-from-winmds"></a>Ler metadados do WinMDs  
 Arquivos WinMD, semelhante aos módulos regulares, contêm metadados que podem ser lidos por meio de [Metadata APIs](../../../../docs/framework/unmanaged-api/metadata/index.md).  No entanto, o CLR mapeia tipos de tempo de execução do Windows para tipos do .NET Framework, quando ele lê que winmd arquivos para que os desenvolvedores que programa no código gerenciado e consumam o arquivo WinMD podem ter uma experiência de programação mais natural.  Para obter alguns exemplos desses mapeamentos, consulte [.NET Framework suporte para aplicativos da Windows Store e tempo de execução do Windows](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Assim o modo que o criador de perfil obterá quando ele usa os APIs de metadados: o modo de exibição bruto do tempo de execução do Windows ou o modo de exibição do .NET Framework mapeado?  A resposta: cabe a você.  
  
 Quando você chama o [Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) método em um WinMD para obter uma interface de metadados, como [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), você pode optar por definir [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)no `dwOpenFlags` parâmetro para desativar esse mapeamento.  Caso contrário, por padrão, o mapeamento será habilitado.  Normalmente, um criador de perfil manterá o mapeamento habilitado, para que as cadeias de caracteres que a DLL do criador de perfil obtém dos metadados de WinMD (por exemplo, nomes de tipos) parecerá familiar e natural para o usuário do criador de perfil.  
  
<a name="Modifying"></a>   
### <a name="modifying-metadata-from-winmds"></a>Modificando os metadados do WinMDs  
 Não há suporte para a modificação de metadados em WinMDs.  Se você chamar o [Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) método para um WinMD de arquivo e especifique [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) no `dwOpenFlags` parâmetro ou solicitar uma interface de metadados graváveis, como [ IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) falhará.  Isso é de particular importância a regravação de IL criadores de perfil, que precisam modificar metadados para dar suporte a instrumentação (por exemplo, para adicionar AssemblyRefs ou novos métodos).  Portanto, você deve verificar [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) primeiro (como discutido na seção anterior) e não pedir para interfaces de metadados gravável esses módulos.  
  
<a name="Resolving"></a>   
### <a name="resolving-assembly-references-with-winmds"></a>Resolvendo referências de assembly com WinMDs  
 Muitos criadores de perfil precisam resolver referências de metadados manualmente para auxiliar na instrumentação ou tipo inspeção.  Esses perfis precisam estar ciente de como o CLR resolve referências de assembly que apontam para WinMDs, porque essas referências são resolvidas na forma completamente diferente que as referências de assembly padrão.  
  
<a name="Profilers"></a>   
## <a name="memory-profilers"></a>Criadores de perfil de memória  
 O coletor de lixo e o heap gerenciado não são significativamente diferentes em um aplicativo da Windows Store e um aplicativo de área de trabalho.  No entanto, há algumas diferenças sutis que autores do criador de perfil precisam estar ciente.  
  
<a name="ForceGC"></a>   
### <a name="forcegc-creates-a-managed-thread"></a>ForceGC cria um thread gerenciado  
 Durante a criação de perfil de memória, a DLL do criador de perfil geralmente cria um thread separado do que chamar o [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) método.  Isso não é nada novo.  Mas o que podem ser surpreendente é que o ato de fazer uma coleta de lixo dentro de um aplicativo da Windows Store pode transformar o thread em um thread gerenciado (por exemplo, um ThreadID de API de criação de perfil será criado para esse thread).  
  
 Para entender as consequências disso, é importante entender as diferenças entre as chamadas síncronas e assíncronas, conforme definido pela API de criação de perfil do CLR. Observe que isso é muito diferente do conceito de chamadas assíncronas em aplicativos da Windows Store.  Consulte a postagem do blog [por que temos CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) para obter mais informações.  
  
 O ponto de relevante é que as chamadas feitas em threads criados pelo criador de perfil sempre são consideradas síncronas, mesmo se as chamadas são feitas de fora de uma implementação de sua DLL de criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) métodos.  Pelo menos, que é usado para ser o caso.  Agora que o CLR foram desligados thread do profiler em um thread gerenciado por causa de sua chamada para [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), que o thread não é considerado thread do profiler.  Como tal, o CLR impõe uma definição mais rígida do que qualifica como síncrona para esse thread — ou seja, que deve originar-se uma chamada de dentro de um a DLL de criador de perfil [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) métodos para se qualificar como síncrona.  
  
 O que isso significa na prática?  A maioria dos [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) métodos só são seguros ser chamada de forma síncrona e imediatamente falhará caso contrário.  Portanto, se a DLL do criador de perfil reutiliza o [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) thread para outras chamadas geralmente são feitas em threads criados pelo criador de perfil (por exemplo, para [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), ou [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), você vai ter problemas.  Até mesmo uma função de segurança assíncrona como [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) tem regras especiais quando chamado de threads gerenciados. (Consulte a postagem do blog [percorrer a pilha Profiler: conceitos básicos e superiores](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) para obter mais informações.)  
  
 Portanto, é recomendável que qualquer thread que cria a DLL do criador de perfil para chamar [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) deve ser usado *somente* para fins de disparo GCs e, em seguida, responder para os retornos de chamada de GC.  Ele não deve chamar a API de criação de perfil para realizar outras tarefas como a pilha de amostragem ou desanexar.  
  
<a name="WeakTable"></a>   
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences  
 Começando com o .NET Framework 4.5, há um retorno de chamada de GC novo, [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), que fornece o criador de perfil concluir mais informações sobre *identificadores dependentes*. Essas alças efetivamente adicionar uma referência de um objeto de origem para um objeto de destino para fins de gerenciamento de tempo de vida do GC.  Identificadores dependentes são nada de novo, e os desenvolvedores que programa no código gerenciado tem sido capazes de criar seus próprios identificadores dependentes usando o <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> classe mesmo antes do Windows 8 e o .NET Framework 4.5.  
  
 No entanto, aplicativos da Windows Store do XAML gerenciados agora fazer uso intenso de identificadores dependentes.  Em particular, o CLR usa-los para ajudar com o gerenciamento de ciclo de referência entre os objetos gerenciados e os objetos de tempo de execução do Windows não gerenciados.  Isso significa que é mais importante do que nunca para criadores de perfil de memória ser informado sobre essas alças dependentes para que eles podem ser visualizados juntamente com o restante das bordas do gráfico de heap.  A DLL do criador de perfil devem usar [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), e [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) para formar uma visão completa do gráfico de heap .  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusão  
 É possível usar a API de criação de perfil CLR para analisar o código gerenciado em execução dentro de aplicativos da Windows Store.  Na verdade, você pode levar um criador de perfil existente que você está desenvolvendo e fazer algumas alterações específicas para que ele pode direcionar os aplicativos da Windows Store.   Interface de usuário do criador de perfil devem usar as novas APIs para ativar o aplicativo da Windows Store no modo de depuração.  Certifique-se de que a DLL do criador de perfil consome apenas essas APIs aplicáveis para aplicativos da Windows Store.  O mecanismo de comunicação entre o DLL do criador de perfil e o criador de perfil da interface do usuário deve ser escrito com as restrições de API do aplicativo da Windows Store em mente e com reconhecimento das permissões restritas em vigor para aplicativos da Windows Store.  A DLL do criador de perfil deve estar ciente de como o CLR o tratará WinMDs, e como o comportamento do coletor de lixo é diferente em relação ao threads gerenciados.  
  
<a name="Resources"></a>   
## <a name="resources"></a>Recursos  
 **O Common Language Runtime**  
 -   [Referência de API de criação de perfil CLR](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [Referência de API de metadados do CLR](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Interação do CLR com o tempo de execução do Windows**  
 [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Aplicativos da Windows Store**  
 -   [Acesso a arquivos e permissões (aplicativos de tempo de execução do Windows](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Obter uma licença de desenvolvedor](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [Interface IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
