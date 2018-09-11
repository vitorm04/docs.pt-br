---
title: Criadores de perfil CLR e aplicativos da Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1747d99fbfbc31fb592aee570d10d574b8480b0
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44265046"
---
# <a name="clr-profilers-and-windows-store-apps"></a>Criadores de perfil CLR e aplicativos da Windows Store

Este tópico discute o que você precisa pensar sobre quando as ferramentas de diagnóstico de escrita analisarem gerenciado código em execução dentro de um aplicativo da Windows Store.  Ele também fornece diretrizes para modificar suas ferramentas de desenvolvimento existentes, para que eles continuam a funcionar quando você executá-los nos aplicativos da Windows Store.  Para entender essas informações, é melhor que se você estiver familiarizado com a Common Language Runtime de criação de perfil API, você já tiver usado essa API em uma ferramenta de diagnóstico que é executado corretamente em relação a aplicativos de desktop do Windows e você agora está interessado em modificando a ferramenta para ser executado corretamente em relação a aplicativos da Windows Store.  
  
## <a name="introduction"></a>Introdução

 Se você o feita após o parágrafo introdutório, em seguida, você está familiarizado com a API de criação de perfil do CLR.  Você já escreveu uma ferramenta de diagnóstico que funciona bem em aplicativos da área de trabalho gerenciados.  Agora você está curioso o que fazer para que sua ferramenta funciona com um aplicativo gerenciado da Windows Store.  Talvez você já tentou fazer esse trabalho e ter descoberto que não é uma tarefa simples.  Na verdade, há várias considerações que podem não ser óbvio para todos os desenvolvedores de ferramentas.  Por exemplo:  
  
-   Aplicativos da Windows Store executados em um contexto com permissões reduzidas severos.  
  
-   Arquivos de metadados do Windows têm características exclusivas em comparação com módulos gerenciados tradicionais.  
  
-   Aplicativos da Windows Store têm o hábito de suspender a mesmos quando interatividade fica inativo.  
  
-   Seus mecanismos de comunicação entre processos podem não funcionar por vários motivos.  
  
 Este tópico lista as coisas que você precisa estar atento e como lidar com eles corretamente.  
  
 Se você estiver familiarizado com a API de criação de perfil do CLR, vá para os recursos no final deste tópico para localizar o melhor informações introdutórias.  
  
 Fornecendo detalhes sobre APIs específicas do Windows e como eles devem ser usados também está fora do escopo deste tópico.  Considere este tópico um ponto de partida e consulte o MSDN para saber mais sobre as APIs do Windows referenciado aqui.  
  
## <a name="architecture-and-terminology"></a>Arquitetura e terminologia

 Normalmente, uma ferramenta de diagnóstico tem uma arquitetura semelhante à mostrada na ilustração a seguir. Ele usa o termo "profiler", mas muitas dessas ferramentas ir muito além do desempenho típico ou criação de perfil de memória em áreas como cobertura de código, estruturas de objeto de simulação, viajar depuração, o aplicativo monitoramento e assim por diante.  Para simplificar, este tópico continuará para se referir a todas essas ferramentas, como os criadores de perfil.  
  
 A seguinte terminologia é usada ao longo deste tópico:  
  
**Aplicativo**

Este é o aplicativo que está analisando o criador de perfil.  Normalmente, o desenvolvedor desse aplicativo agora está usando o criador de perfil para ajudar a diagnosticar problemas com o aplicativo.  Tradicionalmente, esse aplicativo seria um aplicativo de desktop do Windows, mas neste tópico, estamos examinando aplicativos da Windows Store.  
  
**Profiler DLL**

Este é o componente que carrega no espaço de processo do aplicativo que está sendo analisado.  Esse componente, também conhecido como o criador de perfil de "agente", implementa a [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[ICorProfilerCallback Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2,3, etc.) interfaces e consome o [ ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2,3, etc.) interfaces para coletar dados sobre o aplicativo analisado e potencialmente modificar os aspectos do comportamento do aplicativo.  
  
**Interface do usuário do Profiler**

Isso é um aplicativo da área de trabalho que o criador de perfil usuário interage com.  Ele é responsável por exibir o status do aplicativo para o usuário e dar ao usuário os meios para controlar o comportamento do aplicativo analisado.  Esse componente sempre é executado em seu próprio espaço de processo separado do espaço de processo do aplicativo que está sendo analisado.  A interface do usuário do Profiler também pode atuar como o "Anexação" gatilho, que é o processo que chama o [iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método para fazer com que o aplicativo analisado para carregar a DLL do Profiler nos casos em que a DLL do criador de perfil não especificou carregar na inicialização.  
  
> [!IMPORTANT]
> A interface do usuário do Profiler deve permanecer um aplicativo da área de trabalho do Windows, mesmo quando ele é usado para o controle e o relatório em um aplicativo da Windows Store.  Não espere poder empacotar e enviar sua ferramenta de diagnóstico do Windows Store.  Sua ferramenta precisa fazer coisas que aplicativos da Windows Store não é possível fazer, e muitas dessas coisas residem dentro de sua interface do usuário do Profiler.  
  
 Ao longo deste documento, o código de exemplo pressupõe que:  
  
- O Profiler DLL é escrito em C++, porque ele deve ser uma DLL nativa, de acordo com os requisitos da API de criação de perfil do CLR.  
  
- A interface do usuário do Profiler é escrito em c#.  Isso não é necessário, mas porque não há nenhum requisito no idioma para o processo de seu Profiler da interface do usuário, por que não escolher um idioma que seja simples e conciso?  
  
### <a name="windows-rt-devices"></a>Dispositivos Windows RT

Dispositivos Windows RT bastante estão bloqueados.  Criadores de perfil de terceiros simplesmente não não possível carregadas esses dispositivos.  Este documento se concentra em PCs com Windows 8.  
  
## <a name="consuming-windows-runtime-apis"></a>Consumo de APIs de tempo de execução do Windows

 Em um número de cenários discutidos nas seções a seguir, seu aplicativo de área de trabalho da interface do usuário do Profiler precisa consumir algumas novas APIs do Windows Runtime.  Você deve consultar a documentação para entender quais APIs de tempo de execução do Windows pode ser usado em aplicativos da área de trabalho, e se seu comportamento é diferente quando chamado a partir de aplicativos de desktop e Windows Store apps.  
  
 Se a interface do usuário do Profiler é escrito em código gerenciado, haverá algumas etapas, que você precisará fazer para que o consumo fácil das APIs do tempo de execução do Windows.  Consulte a [gerenciado da área de trabalho e tempo de execução do Windows](https://go.microsoft.com/fwlink/?LinkID=271858) artigo para obter mais informações.  
  
## <a name="loading-the-profiler-dll"></a>Ao carregar o DLL do Profiler

 Esta seção descreve como a interface do usuário do Profiler faz com que o aplicativo da Windows Store carregar a DLL do Profiler.  O código discutido nesta seção pertence em seu aplicativo de área de trabalho do Profiler da interface do usuário e, portanto, envolve o uso de APIs do Windows que são seguros para aplicativos da área de trabalho, mas não necessariamente é seguro para aplicativos da Windows Store.  
  
 A interface do usuário do Profiler pode fazer com que o Profiler DLL seja carregada no espaço de processo do aplicativo de duas maneiras:  
  
-   Na inicialização do aplicativo, conforme controlado pelas variáveis de ambiente.  
  
-   Anexando ao aplicativo após a inicialização for concluída, chamando o [iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método.  
  
 Uma das suas dificuldades primeiro obterá iniciar-carregar e anexar-carregar da DLL Profiler funcione corretamente com os aplicativos da Windows Store.  As duas formas de carregamento compartilham algumas considerações especiais em comum, então vamos começar com eles.  
  
### <a name="common-considerations-for-startup-and-attach-loads"></a>Considerações comuns para inicialização e anexar cargas

 **O Profiler DLL de assinatura**  
 Quando o Windows tenta carregar a DLL do Profiler, ele verifica que o Profiler DLL está assinado corretamente.  Caso contrário, o carregamento falhará por padrão. Há duas formas de fazer isso:  
  
-   Certifique-se de que o Profiler DLL está assinado.  
  
-   Informe o usuário que eles devem instalar uma licença de desenvolvedor em seu computador Windows 8 antes de usar sua ferramenta.  Isso pode ser feito automaticamente pelo Visual Studio ou manualmente em um prompt de comando.  Para obter mais informações, consulte [obter uma licença de desenvolvedor](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Permissões do sistema de arquivos**  
 O aplicativo da Windows Store deve ter permissão para carregar e executar o Profiler DLL do local no sistema de arquivos no qual ele reside.  Por padrão, o aplicativo da Windows Store não tem essa permissão na maioria das pastas e qualquer falha ao tentar carregar a DLL do Profiler produzirá uma entrada no log de eventos do aplicativo do Windows que pode ter esta aparência:  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 Em geral, os aplicativos da Windows Store só têm permissão para acessar um conjunto limitado de locais no disco.  Cada aplicativo da Windows Store pode acessar suas próprias pastas de dados do aplicativo, bem como algumas outras áreas no sistema de arquivos para o qual todos os aplicativos da Windows Store têm acesso.  É melhor instalar a DLL do Profiler e suas dependências em algum lugar em arquivos de programas ou arquivos de programa (x86), porque todos os aplicativos da Windows Store têm permissões read e execute lá por padrão.  
  
### <a name="startup-load"></a>Carga de inicialização

 Normalmente, em um aplicativo da área de trabalho, sua interface do usuário do Profiler solicita uma carga de inicialização da DLL Profiler inicializando um bloco de ambiente que contém as variáveis de ambiente necessárias do API de criação de perfil do CLR (ou seja, `COR_PROFILER`, `COR_ENABLE_PROFILING`, e `COR_PROFILER_PATH`), e em seguida, criando um novo processo com esse bloco de ambiente.  O mesmo se aplica para aplicativos da Windows Store, mas os mecanismos são diferentes.  
  
 **Não são executados com privilégios elevados**  
 Se o processo tenta gerar um aplicativo da Windows Store processo B, um processo de deve ser executado em integridade média nível, não no nível de integridade alto (isto é, não elevado).  Isso significa que a interface do usuário do Profiler deve estar em execução no nível de integridade média, ou que ele deve gerar outro processo da área de trabalho no nível de integridade médio para cuidar da inicialização do aplicativo da Windows Store.  
  
 **Escolhendo um aplicativo Windows Store perfil**  
 Primeiro, você vai querer perguntar qual aplicativo da Windows Store para iniciar de seu usuário do criador de perfil.  Para aplicativos da área de trabalho, talvez mostraria uma caixa de diálogo de procura de arquivo e o usuário deve localizar e selecionar um arquivo de .exe.  Mas os aplicativos da Windows Store são diferentes e usar uma caixa de diálogo de procura não faz sentido.  Em vez disso, é melhor Mostrar ao usuário uma lista de aplicativos da Windows Store instalado para que o usuário selecione.  
  
 Você pode usar o [PackageManager classe](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) para gerar essa lista.  `PackageManager` é uma classe de tempo de execução do Windows que está disponível para aplicativos da área de trabalho e, na verdade é *apenas* disponível para aplicativos da área de trabalho.  
  
 O exemplo a seguir ode de uma interface de usuário hipotético do Profiler, gravado como um aplicativo da área de trabalho no c# yses o `PackageManager` para gerar uma lista de aplicativos do Windows:  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **Especificando o bloco de ambiente personalizado**  
 Uma nova interface COM, [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), permite que você personalize o comportamento de execução de um aplicativo da Windows Store para facilitar a algumas formas de diagnóstico.  Um de seus métodos [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), permite que você passe um bloco de ambiente para o aplicativo da Windows Store quando ele é iniciado, juntamente com outros efeitos úteis, incluindo desabilitar suspensão automática de processo.  O bloco de ambiente é importante porque é onde você precisa especificar as variáveis de ambiente (`COR_PROFILER`, `COR_ENABLE_PROFILING`, e `COR_PROFILER_PATH)`) usado pelo CLR para carregar a DLL do Profiler.  
  
 Considere o seguinte trecho de código:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Há alguns itens que você precisará obter à direita:  
  
-   `packageFullName` pode ser determinado ao iterar sobre os pacotes e buscando `package.Id.FullName`.  
  
-   `debuggerCommandLine` é um pouco mais interessante.  Para passar o bloco de ambiente personalizadas para o aplicativo da Windows Store, você precisa escrever seu próprio, depurador fictício simplista.  Cria o Windows, o aplicativo da Windows Store suspenso e, em seguida, anexa o depurador iniciando o depurador com uma linha de comando, como neste exemplo:  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     em que `-p 1336` significa que o aplicativo da Windows Store tem 1336 de ID de processo, e `-tid 1424` significa 1424 de ID de Thread é o thread que está suspenso.  Seu depurador fictício seria analisar o ThreadID na linha de comando, retomar o thread em questão e, em seguida, sair.  
  
     Eis alguns exemplos de código C++ para fazer isso (certifique-se de adicionar a verificação de erro!):  
  
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
  
     Você precisará implantar este depurador fictício como parte de sua instalação da ferramenta de diagnóstico e, em seguida, especifique o caminho para esse depurador no `debuggerCommandLine` parâmetro.  
  
 **Iniciar o aplicativo da Windows Store**  
 Finalmente chegou o momento para iniciar o aplicativo da Windows Store. Se você já já tiver tentado fazer isso sozinho, você talvez tenha notado que [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) não como criar um processo de aplicativo da Windows Store.  Em vez disso, você precisará usar o [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) método.  Para fazer isso, você precisará obter a ID do modelo do usuário de aplicativo do aplicativo Windows Store que você está iniciando.  E isso significa que você precisará fazer uma pequena aprofundar-se por meio do manifesto.  
  
 Durante a iteração ao longo de seus pacotes (consulte "Escolhendo a Windows Store App para o perfil" a [carga de inicialização](#Startup) seção anteriormente), você talvez queira coletar o conjunto de aplicativos contida no manifesto do pacote atual:  
  
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
  
 Sim, um pacote pode ter vários aplicativos, e cada aplicativo tem sua própria ID de modelo de usuário do aplicativo.  Portanto, você vai querer peça ao seu usuário qual aplicativo ao perfil e, em seguida, pegar a ID de modelo de usuário do aplicativo desse aplicativo específico:  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
    //...
}
```  
  
 Por fim, agora você tem o que você precisa para iniciar o aplicativo da Windows Store:  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **Lembre-se de chamar DisableDebugging**  
 Quando você chamou [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), você fez uma promessa que você limparia após por conta própria por meio da chamada a [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) método, portanto, certifique-se de fazer que quando a sessão de criação de perfil está sobre.  
  
### <a name="attach-load"></a>Anexar a carga

 Quando sua interface do usuário do Profiler deseja anexar o Profiler DLL a um aplicativo que já foi iniciada em execução, ele usa [iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  O mesmo ocorre com os aplicativos da Windows Store.  Mas além das considerações comuns listadas anteriormente, certifique-se de que o aplicativo da Windows Store de destino não está suspenso.  
  
 **EnableDebugging**  
 Assim como acontece com carga de inicialização, chame o [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) método.  Você não precisa dela para a passagem de um bloco de ambiente, mas você precisa de um dos seus outros recursos: desabilitar suspensão automática de processo.  Caso contrário, quando a interface do usuário do Profiler chama [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), o aplicativo da Windows Store de destino pode ser suspenso.  Na verdade, isso provavelmente se o usuário está interagindo com a interface do usuário do Profiler e o aplicativo da Windows Store não está ativo em qualquer uma das telas do usuário.  E se o Store do Windows aplicativo está suspenso, ele não será capaz de responder a qualquer sinalizam de que o CLR envia a ele para anexar o Profiler DLL.  
  
 Portanto, você deve fazer algo parecido com isto:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 Isso é a mesma chamada em que você faria no caso de carga de inicialização, exceto que você não especificar uma linha de comando do depurador ou um bloco de ambiente.  
  
 **DisableDebugging**  
 Como sempre, não se esqueça de chamar [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) quando a sessão de criação de perfil é concluída.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Em execução dentro do aplicativo da Windows Store  
 Portanto, o aplicativo da Windows Store, por fim, carregou a DLL do Profiler.  Agora o Profiler DLL devem ser ensinado como reproduzir pelas regras diferentes exigidas pelos aplicativos da Windows Store, incluindo quais APIs são permitidas e como executar com permissões reduzidas.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Continuar com as APIs de aplicativos da Windows Store  
 Enquanto você navega a API do Windows, você observará que todas as APIs documentada como sendo aplicáveis a aplicativos da área de trabalho, aplicativos da Windows Store ou ambos.  Por exemplo, o **requisitos** seção da documentação para o [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) função indica que a função se aplica a apenas os aplicativos da área de trabalho. Em contraste, o [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) função está disponível para aplicativos da área de trabalho e aplicativos da Windows Store.  
  
 Ao desenvolver a sua DLL Profiler, tratá-lo como se fosse um aplicativo da Windows Store e usar apenas APIs que são documentadas como disponível para aplicativos da Windows Store.  Analisar as dependências (por exemplo, você pode executar `link /dump /imports` em relação a sua DLL do Profiler para auditar) e, em seguida, pesquise os documentos para ver quais das suas dependências são okey e que não são.  Na maioria dos casos, suas violações podem ser corrigidas, simplesmente substituindo-os com um formulário mais recente da API que está documentado como safe (por exemplo, substituindo [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) com [ InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).  
  
 Você pode notar que a sua DLL Profiler chama algumas APIs que se aplicam a apenas os aplicativos da área de trabalho, e ainda que eles parecem funcionar até mesmo quando o Profiler DLL é carregado dentro de um aplicativo da Windows Store.  Lembre-se de que é arriscado para usar qualquer API não documentada para uso com aplicativos da Windows Store na DLL Profiler quando carregado em um processo de aplicativo da Windows Store:  
  
-   Essas APIs não são garantidos para trabalhar quando chamado no contexto exclusivo de aplicativos da Windows Store executados em.  
  
-   Essas APIs podem não funcionar consistentemente quando chamado de diferentes processos de aplicativo da Windows Store.  
  
-   Essas APIs podem parecer funcionar bem em aplicativos da Windows Store na versão atual do Windows, mas poderá ser interrompido ou desabilitado em versões futuras do Windows.  
  
 O melhor conselho é corrigir todas as suas violações e evitar o risco.  
  
 Você pode achar que você com certeza não é possível fazer sem uma API em particular e não é possível localizar um substituto adequado para aplicativos da Windows Store.  Nesse caso, no mínimo:  
  
-   Testar, testar, testar os daylights viver fora de seu uso dessa API.  
  
-   Entender o que a API pode, de repente, interromper ou desaparecer se chamado de dentro do Windows Store apps em versões futuras do Windows.  Isso não será considerado um problema de compatibilidade pela Microsoft e dar suporte a seu uso dele não ser uma prioridade.  
  
### <a name="reduced-permissions"></a>Permissões reduzidas

 Ele está fora do escopo deste tópico para listar todas as maneiras diferentes de permissões de aplicativo da Windows Store dos aplicativos da área de trabalho.  Mas certamente o comportamento será diferente sempre que a DLL do Profiler (quando carregado em um aplicativo da Windows Store em comparação com um aplicativo de desktop) tenta acessar todos os recursos.  O sistema de arquivos é o exemplo mais comum.  Existem, mas alguns coloca no disco que um determinado aplicativo da Windows Store tem permissão para acessar (veja [acesso e permissões de arquivo (aplicativos do Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), e a DLL do Profiler serão nas mesmas restrições.  Teste minuciosamente seu código.  
  
### <a name="inter-process-communication"></a>Comunicação entre processos

 Conforme mostrado no diagrama no início deste documento, sua DLL Profiler (carregado no espaço de processo do aplicativo Windows Store) provavelmente será necessário para se comunicar com o Profiler da interface do usuário (em execução em um espaço de processo do aplicativo da área de trabalho separado) por meio de seu próprio processo personalizado de inter canal de comunicação entre processos (IPC).  A interface do usuário do Profiler envia sinais para a DLL do Profiler para modificar seu comportamento e a DLL do Profiler envia dados do aplicativo da Windows Store analisado para a interface do usuário do Profiler para pós-processamento e exibição para o usuário do criador de perfil.  
  
 A maioria dos criadores de perfil precisam funcionar dessa maneira, mas as opções escolhidas para mecanismos IPC são mais limitadas, quando o Profiler DLL é carregado em um aplicativo da Windows Store.  Por exemplo, pipes nomeados não são parte do aplicativo da Windows Store SDK, portanto você não pode usá-los.  
  
 Mas, claro, os arquivos são ainda no, embora de maneira mais limitada.  Eventos também estão disponíveis.  
  
 **Comunicando-se por meio de arquivos**  
 A maioria dos seus dados provavelmente passarão entre o Profiler DLL e o Profiler da interface do usuário por meio de arquivos.  A chave é escolher um local de arquivo que o Profiler DLL (no contexto de um aplicativo da Windows Store) e a interface do usuário do Profiler leu e acesso de gravação.  Por exemplo, o caminho da pasta temporária é um local que podem acessar o Profiler DLL e a interface do usuário do Profiler, mas nenhum outro pacote de aplicativo da Windows Store pode acessar (Protegendo informações de que log de outros pacotes de aplicativo da Windows Store).  
  
 Sua interface do usuário do Profiler e o Profiler DLL podem determinar esse caminho de forma independente.  A interface do usuário do Profiler, quando ele itera em todos os pacotes instalados para o usuário atual (consulte o exemplo de código anterior), obtém acesso ao `PackageId` classe, do qual o caminho da pasta temporária pode ser derivado com código semelhante a este trecho de código.  (Como sempre, verificação de erros é omitida para fins de brevidade).  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 Enquanto isso, sua DLL Profiler pode fazer basicamente a mesma coisa, se pudesse mais facilmente obtém os [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) classe usando o [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) propriedade.  
  
 **Comunicando-se por meio de eventos**  
 Se você quiser a semântica de sinalização simple entre o Profiler da interface do usuário e o Profiler DLL, você pode usar eventos dentro de aplicativos da Windows Store, bem como aplicativos da área de trabalho.  
  
 Da sua DLL Profiler, você pode simplesmente chamar o [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) função para criar um evento nomeado com qualquer nome que desejar.  Por exemplo:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 A interface do usuário do Profiler, em seguida, precisa encontrar o que o evento nomeado no namespace do aplicativo da Windows Store.  Por exemplo, a interface do usuário do Profiler poderia chamar [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), especificando o nome do evento como  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>` é o SID do AppContainer do aplicativo da Windows Store.  Uma seção anterior deste tópico mostrou como iterar sobre os pacotes instalados para o usuário atual.  Esse código de exemplo, você pode obter o packageId.  E o packageId, você pode obter o `<acSid>` com um código semelhante ao seguinte:  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
### <a name="no-shutdown-notifications"></a>Não há notificações de desligamento

 Quando em execução dentro de um aplicativo da Windows Store, sua DLL Profiler não deve confiar nos [ICorProfilerCallback:: Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) ou até mesmo [DllMain](/windows/desktop/Dlls/dllmain) (com `DLL_PROCESS_DETACH`) que está sendo chamado para notificar a DLL do Profiler Se o aplicativo da Windows Store está sendo encerrado.  Na verdade, você deve esperar que eles nunca serão chamados.  Historicamente, muitas DLLs do Profiler têm usado essas notificações como locais práticos para liberar caches para disco, fechar arquivos, enviar notificações de volta para a interface do usuário do Profiler, etc.  Mas agora o Profiler DLL precisa ser organizados de forma um pouco diferente.  
  
 O Profiler DLL deve ser informações de registro em log quando ele passa.  Por motivos de desempenho, você talvez queira informações na memória do lote e libere-o no disco à medida que o lote aumenta de tamanho após algum limite.  Mas suponha que todas as informações ainda não foram liberadas para disco podem ser perdidas.  Isso significa que você vai querer selecionar seu limite com sabedoria e que sua interface do usuário do Profiler deve ser protegida para lidar com informações incompletas gravadas pela DLL Profiler.  
  
## <a name="windows-runtime-metadata-files"></a>Arquivos de metadados de tempo de execução do Windows

 Está fora do escopo deste documento para entrar em detalhes sobre quais metadados de tempo de execução do Windows (WinMD) são arquivos.    Esta seção é limitada a como a API de criação de perfil do CLR reage quando arquivos WinMD são carregados pelo aplicativo do Windows Store que o Profiler DLL está analisando.  
  
### <a name="managed-and-non-managed-winmds"></a>WinMDs gerenciados e não gerenciados

 Se um desenvolvedor usa o Visual Studio para criar um novo projeto de componente de tempo de execução do Windows, uma compilação desse projeto produz um arquivo WinMD que descreve os metadados (as descrições de tipo de classes, interfaces, etc.) criados pelo desenvolvedor.  Se esse projeto é um projeto de linguagem gerenciada escrito em c# ou VB, o mesmo arquivo WinMD também contém a implementação desses tipos (que significa que ele contém o IL compilado do código-fonte do desenvolvedor).  Esses arquivos são conhecidos como arquivos de WinMD gerenciados.  Eles são interessantes em que eles contêm metadados de tempo de execução do Windows e a implementação subjacente.  
  
 Por outro lado, se um desenvolvedor cria um projeto de componente de tempo de execução do Windows para C++, uma compilação desse projeto produz um arquivo WinMD que contém apenas metadados e a implementação é compilada em um DLL nativo separado.  Da mesma forma, os arquivos WinMD incluídos no SDK do Windows contêm apenas os metadados, com a implementação compilada em DLLs nativas separadas que são fornecidos como parte do Windows.  
  
 As informações a seguir se aplica a ambos os WinMDs gerenciado, que contêm metadados e implementação, e para WinMDs não gerenciado, que contêm apenas os metadados.  
  
### <a name="winmd-files-look-like-clr-modules"></a>Arquivos WinMD se parecer com módulos CLR

 No que diz respeito o CLR, todos os arquivos WinMD são módulos.  A API de criação de perfil do CLR, portanto, informa à sua DLL Profiler ao carregar arquivos WinMD e quais são suas ModuleIDs, da mesma forma que para outros módulos gerenciados.  
  
 A DLL do Profiler pode distinguir arquivos WinMD de outros módulos, chamando o [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) método e inspecionando a `pdwModuleFlags` parâmetro de saída a [COR_PRF_MODULE_WINDOWS_ Tempo de execução](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) sinalizador.  (Ele é definido somente se o ModuleID representa um WinMD.)  
  
### <a name="reading-metadata-from-winmds"></a>Ler metadados do WinMDs

 Arquivos WinMD, semelhante aos módulos regulares, contêm metadados que podem ser lidos por meio de [Metadata APIs](../../../../docs/framework/unmanaged-api/metadata/index.md).  No entanto, o CLR mapeia tipos de tempo de execução do Windows para tipos do .NET Framework, quando ele lê que arquivos de WinMD para que os desenvolvedores que programar em código gerenciado e consumam o arquivo WinMD podem ter uma experiência de programação mais natural.  Para obter alguns exemplos desses mapeamentos, consulte [suporte do .NET Framework para Windows Store Apps e tempo de execução do Windows](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Então, qual exibição seu gerador de perfil receberá quando ele usa as APIs de metadados: o modo de exibição bruto do tempo de execução do Windows ou o modo de exibição mapeado do .NET Framework?  A resposta: cabe a você.  
  
 Quando você chama o [ICorProfilerInfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) método em um WinMD para obter uma interface de metadados, como [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), você pode optar por definir [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)no `dwOpenFlags` parâmetro para desativar esse mapeamento.  Caso contrário, por padrão, o mapeamento será habilitado.  Normalmente, um criador de perfil manterá o mapeamento habilitado, para que as cadeias de caracteres que o Profiler DLL obtém de metadados do WinMD (por exemplo, nomes de tipos) parecerá familiar e natural para o usuário do criador de perfil.  
  
### <a name="modifying-metadata-from-winmds"></a>Modificando os metadados do WinMDs

 Não há suporte para a modificação de metadados no WinMDs.  Se você chamar o [ICorProfilerInfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) método para um WinMD de arquivo e especifique [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) no `dwOpenFlags` parâmetro ou pedir uma interface de metadados gravável como [ IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) falhará.  Isso é de particular importância para regravação de IL criadores de perfis, que é necessário modificar os metadados para dar suporte a instrumentação (por exemplo, para adicionar AssemblyRefs ou novos métodos).  Portanto, você deve verificar se há [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) primeiro (como discutido na seção anterior) e evitando o pedindo para interfaces de metadados gravável nesses módulos.  
  
### <a name="resolving-assembly-references-with-winmds"></a>Resolvendo referências de assembly com WinMDs

 Os criadores de perfil muitas precisam resolver referências de metadados manualmente para auxiliar com a inspeção do tipo ou instrumentação.  Esses criadores de perfil precisam estar ciente de como o CLR resolve referências de assembly que apontam para WinMDs, porque essas referências são resolvidas na forma completamente diferente do que as referências de assembly padrão.  
  
## <a name="memory-profilers"></a>Criadores de perfil de memória

 O coletor de lixo e o heap gerenciado não são fundamentalmente diferentes em um aplicativo da Windows Store e um aplicativo da área de trabalho.  No entanto, há algumas diferenças sutis que os autores do criador de perfil precisam estar atento.  
  
### <a name="forcegc-creates-a-managed-thread"></a>ForceGC cria um thread gerenciado

 Ao fazer a criação de perfil de memória, a DLL do Profiler normalmente cria um thread separado da qual chamar o [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) método.  Isso é algo novo.  Mas o que pode ser surpreendente é que o ato de fazer uma coleta de lixo dentro de um aplicativo da Windows Store pode transformar seu thread em um thread gerenciado (por exemplo, um ThreadID de API de criação de perfil será criado para esse thread).  
  
 Para entender as consequências disso, é importante entender as diferenças entre as chamadas síncronas e assíncronas, conforme definido pela API de criação de perfil do CLR. Observe que isso é muito diferente do conceito de chamadas assíncronas nos aplicativos da Windows Store.  Confira a postagem [motivo pelo qual temos CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) para obter mais informações.  
  
 A questão relevante é que as chamadas feitas em threads criados pelo criador de perfil são sempre consideradas síncronas, mesmo que essas chamadas são feitas de fora de uma implementação de um dos sua DLL de Profiler [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) métodos.  Pelo menos, que costumava ser o caso.  Agora que o CLR se transformou o thread de seu gerador de perfil em um thread gerenciado por causa de sua chamada para [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), que thread não é mais considerado o thread de seu gerador de perfil.  Como tal, o CLR impõe uma definição mais rigorosas do que qualifica como síncronas para esse thread — ou seja, que deve ter a origem de uma chamada de dentro de um de sua DLL de Profiler [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) métodos para se qualificar como síncronas.  
  
 O que isso significa na prática?  A maioria dos [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) métodos só são seguros ser chamado de forma síncrona e imediatamente falhará caso contrário.  Portanto, se a sua DLL Profiler reutiliza sua [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) thread para outras chamadas geralmente são feitas em threads criados pelo criador de perfil (por exemplo, para [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), ou [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), você vai ter problemas.  Até mesmo uma função assíncrona-safe, como [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) tem regras especiais quando chamado de threads gerenciados. (Confira a postagem [percorrer a pilha Profiler: Noções básicas e além](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) para obter mais informações.)  
  
 Portanto, é recomendável que qualquer thread que o Profiler DLL cria para chamar [método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) deve ser usado *somente* para fins de disparo GCs e, em seguida, responder aos retornos de chamada GC.  Ele não deve chamar a API de criação de perfil para realizar outras tarefas, como a pilha de amostragem ou desanexar.  
  
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

 Começando com o .NET Framework 4.5, não há um retorno de chamada do GC novos [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), que dá o criador de perfil concluir mais informações sobre *identificadores dependentes*. Essas alças efetivamente adicionar uma referência de um objeto de origem para um objeto de destino para fins de gerenciamento de tempo de vida de GC.  Identificadores dependentes são nada de novo, e os desenvolvedores que programam em código gerenciado tem sido capazes de criar seus próprios identificadores dependentes usando o <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> classe mesmo antes do Windows 8 e o .NET Framework 4.5.  
  
 No entanto, aplicativos gerenciados do XAML Windows Store agora fazem uso intenso de identificadores dependentes.  Em particular, o CLR usa-os para ajudar a gerenciar ciclos de referência entre os objetos gerenciados e os objetos de tempo de execução do Windows não gerenciados.  Isso significa que é mais importante do que nunca para criadores de perfil de memória ser informado dessas alças dependentes para que eles podem ser visualizados com o restante das bordas no grafo de heap.  A DLL do Profiler deve usar [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), e [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) juntas para formar uma exibição completa do gráfico de heap .  
  
## <a name="conclusion"></a>Conclusão

 É possível usar a API de criação de perfil do CLR para analisar o código gerenciado em execução dentro de aplicativos da Windows Store.  Na verdade, você pode levar um criador de perfil existente que você está desenvolvendo e fazer algumas alterações específicas para que ele pode direcionar os aplicativos da Windows Store.   A interface do usuário do Profiler deve usar as novas APIs para ativar o aplicativo da Windows Store no modo de depuração.  Certifique-se de que sua DLL Profiler consome apenas das APIs aplicáveis para aplicativos da Windows Store.  O mecanismo de comunicação entre o Profiler DLL e a interface do usuário do Profiler deve ser escrito com as restrições de API do aplicativo Windows Store em mente e com reconhecimento de permissões restritos em vigor para aplicativos da Windows Store.  O Profiler DLL deve estar ciente de como o CLR trata WinMDs, e como o comportamento do coletor de lixo é diferente em relação aos threads gerenciados.  
  
## <a name="resources"></a>Recursos

 **O Common Language Runtime**  
 -   [Referência de API de criação de perfil do CLR](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [Referência de API de metadados do CLR](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Interação do CLR com o tempo de execução do Windows**  
 [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Aplicativos da Windows Store**  
 -   [Acesso a arquivos e permissões (aplicativos do Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Obter uma licença de desenvolvedor](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [Interface IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Consulte também

[Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)  
