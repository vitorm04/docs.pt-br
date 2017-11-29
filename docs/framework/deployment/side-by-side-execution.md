---
title: "Execução lado a lado no .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: side-by-side execution
ms.assetid: 649f1342-766b-49e6-a90d-5b019a751e11
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25a5092da1526bc266c5cc483cc3cd81d2ac3385
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="side-by-side-execution-in-the-net-framework"></a>Execução lado a lado no .NET Framework
A execução lado a lado é a capacidade de executar várias versões de um aplicativo ou componente no mesmo computador. Você pode ter várias versões do Common Language Runtime e várias versões de aplicativos e componentes que usam uma versão do tempo de execução no mesmo computador ao mesmo tempo.  
  
 A ilustração a seguir mostra vários aplicativos usando duas versões diferentes do tempo de execução no mesmo computador. Os aplicativos A, B e C usam a versão 1.0 do tempo de execução e o aplicativo D usa a versão 1.1 do tempo de execução.  
  
 ![Execução lado a lado](../../../docs/framework/deployment/media/simplesbs.gif "simplesbs")  
Execução lado a lado de duas versões do tempo de execução  
  
 O .NET Framework consiste no Common Language Runtime e uma coleção de assemblies que contêm os tipos de API. Versões são atribuídas ao tempo de execução e aos assemblies do .NET Framework separadamente. Por exemplo, a versão 4.0 do tempo de execução é realmente a versão 4.0.319, enquanto que a versão 1.0 dos assemblies do .NET Framework é a versão 1.0.3300.0.  
  
 A ilustração a seguir mostra vários aplicativos usando duas versões diferentes de um componente no mesmo computador. Os aplicativos A e B usam a versão 1.0 do componente enquanto o aplicativo C usa a versão 2.0 do mesmo componente.  
  
 ![Execução lado a lado](../../../docs/framework/deployment/media/compsbs.gif "compsbs")  
Execução lado a lado de duas versões de um componente  
  
 A execução lado a lado confere mais controle sobre a quais versões de um componente um aplicativo está associado e mais controle sobre qual versão do tempo de execução um aplicativo usa.  
  
## <a name="benefits-of-side-by-side-execution"></a>Benefícios da execução lado a lado  
 Antes do Windows XP e .NET Framework, conflitos de DLL ocorriam porque os aplicativos eram incapazes de distinguir entre versões incompatíveis do mesmo código. Informações de tipo contidas em uma DLL foram associadas a apenas um nome de arquivo. Um aplicativo não tinha como saber se os tipos contidos em uma DLL eram os mesmos tipos com os quais o aplicativo havia sido criado. Como resultado, uma nova versão de um componente poderia substituir uma versão anterior e interromper aplicativos.  
  
 A execução lado a lado e o .NET Framework fornecem os seguintes recursos para eliminar conflitos de DLL:  
  
-   Assemblies com nomes fortes.  
  
     A execução lado a lado usa assemblies com nome forte para associar informações de tipo a uma versão específica de um assembly. Isso impede que um aplicativo ou componente associe-se a uma versão inválida de um assembly. Assemblies com nomes fortes também permitem que várias versões de um arquivo existam no mesmo computador e sejam usadas por aplicativos. Para obter mais informações, consulte [Assemblies com nome forte](../../../docs/framework/app-domains/strong-named-assemblies.md).  
  
-   Armazenamento de código ciente de versão.  
  
     O .NET Framework fornece armazenamento de código ciente de versão no cache de assembly global. O cache de assembly global é um cache de código amplo no computador presente em todos os computadores com o .NET Framework instalado. Ele armazena assemblies baseados em versão, cultura e informações do editor, além de oferecer suporte a várias versões de componentes e aplicativos. Para obter mais informações, consulte [Cache de Assembly Global](../../../docs/framework/app-domains/gac.md).  
  
-   Isolamento.  
  
     Usando o .NET Framework, você pode criar aplicativos e componentes executados em isolamento. O isolamento é um componente essencial da execução lado a lado. Ele envolve estar ciente sobre os recursos que você está usando e compartilhar recursos com confiança entre várias versões de um aplicativo ou componente. O isolamento também inclui armazenar arquivos de forma específica a versões. Para saber mais sobre isolamento, consulte as [Diretrizes para criar componentes para execução lado a lado](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="version-compatibility"></a>Compatibilidade de versões  
 As versões 1.0 e 1.1 do .NET Framework são projetadas para serem compatíveis entre si. Um aplicativo criado com o .NET Framework versão 1.0 deve ser executado na versão 1.1 e um aplicativo criado com o .NET Framework versão 1.1 deve ser executado na versão 1.0. Observe, entretanto, que os recursos da API adicionados na versão 1.1 do .NET Framework não funcionarão com a versão 1.0 do .NET Framework. Aplicativos criados com a versão 2.0 serão executados somente na versão 2.0. Aplicativos da versão 2.0 não serão executados na versão 1.1 ou anterior.  
  
 As versões do .NET Framework são tratadas como uma unidade que consiste no tempo de execução e em seus assemblies do .NET Framework associados (um conceito conhecido como unificação de assemblies). Você pode redirecionar a associação de assembly para incluir outras versões dos assemblies do .NET Framework, mas substituir a associação padrão do assembly pode ser arriscado e deve ser rigorosamente testado antes da implantação.  
  
## <a name="locating-runtime-version-information"></a>Localizando informações da versão do tempo de execução  
 Informações sobre em qual versão do tempo de execução um aplicativo ou componente foi compilado e quais versões do tempo de execução são necessárias para executar o aplicativo são armazenadas em dois locais. Quando um aplicativo ou componente é compilado, as informações sobre a versão de tempo de execução usada para compilá-lo são armazenadas no executável gerenciado. Informações sobre as versões de tempo de execução que exigem que o aplicativo ou componente sejam armazenados no arquivo de configuração de aplicativo.  
  
### <a name="runtime-version-information-in-the-managed-executable"></a>Informações da versão de tempo de execução no executável gerenciado  
 O cabeçalho do arquivo PE (executável portátil) de cada aplicativo gerenciado e componente contém informações sobre a versão de tempo de execução com a qual ele foi compilado. O Common Language Runtime usa essas informações para determinar a versão mais provável do tempo de execução em que o aplicativo precisa ser executado.  
  
### <a name="runtime-version-information-in-the-application-configuration-file"></a>Informações de versão de tempo de execução estão no arquivo de configuração de aplicativo  
 Além das informações no cabeçalho do arquivo PE, um aplicativo pode ser implantado com um arquivo de configuração de aplicativo que fornece informações de versão do tempo de execução. O arquivo de configuração de aplicativo é um arquivo baseado em XML que é criado pelo desenvolvedor do aplicativo e que é fornecido com ele. O elemento [\<requiredRuntime >](../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) da seção [\<startup>](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md), se existir neste arquivo, especifica quais versões do tempo de execução e quais versões de um componente o aplicativo dá suporte. Você também pode usar esse arquivo para testar a compatibilidade do aplicativo com diferentes versões do tempo de execução.  
  
 Código não gerenciado, inclusive aplicativos COM e COM+, podem ter arquivos de configuração de aplicativo que o tempo de execução usa para interagir com código gerenciado. O arquivo de configuração de aplicativo afeta qualquer código gerenciado que você ativar usando COM. O arquivo pode especificar quais versões de tempo de execução têm suporte, bem como redirecionamentos de assembly. Por padrão, aplicativos de interoperabilidade COM que efetuam chamadas para código gerenciado usam a versão mais recente do tempo de execução instalada no computador.  
  
 Para obter mais informações sobre arquivos de configuração de aplicativo, consulte [Configurando aplicativos](../../../docs/framework/configure-apps/index.md).  
  
## <a name="determining-which-version-of-the-runtime-to-load"></a>Determinando a versão do tempo de execução a ser carregada  
 O Common Language Runtime usa as informações a seguir para determinar qual versão do tempo de execução deve ser carregada para um aplicativo:  
  
-   As versões de tempo de execução que estão disponíveis.  
  
-   As versões de tempo de execução com suporte em um aplicativo.  
  
### <a name="supported-runtime-versions"></a>Versões do tempo de execução com suporte  
 O tempo de execução usa o arquivo de configuração de aplicativo e o cabeçalho do arquivo PE (executável portátil) para determinar a qual versão do tempo de execução um aplicativo dá suporte. Se nenhum arquivo de configuração de aplicativo existir, o tempo de execução carregará a versão de tempo de execução especificada no cabeçalho do arquivo PE do aplicativo, se essa versão estiver disponível.  
  
 Se houver um arquivo de configuração de aplicativo, o tempo de execução determinará a versão do tempo de execução apropriada a ser carregada com base nos resultados do processo a seguir:  
  
1.  O tempo de execução examina o elemento [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) no arquivo de configuração de aplicativo. Se uma ou mais das versões com suporte no tempo de execução especificadas no elementos **\<supportedRuntime>** existirem, o tempo de execução carrega a versão de tempo de execução especificada pelo primeiro elementos **\<supportedRuntime>**. Se essa versão não estiver disponível, o tempo de execução examina o próximo elemento  **\<supportedRuntime>** e tenta carregar a versão de tempo de execução especificada nele. Se esta versão do tempo de execução não estiver disponível, os elementos **\<supportedRuntime>** subsequentes serão examinados. Se nenhuma das versões com suporte no tempo de execução estiver disponível, ele não poderá carregar uma versão de tempo de execução e exibirá uma mensagem para o usuário (consulte a etapa 3).  
  
2.  O tempo de execução lê o cabeçalho do arquivo PE do arquivo executável do aplicativo. Se a versão do tempo de execução especificada pelo cabeçalho do arquivo PE estiver disponível, o tempo de execução carregará a versão. Se a versão de tempo de execução especificada não estiver disponível, o tempo de execução procurará por uma versão de tempo de execução determinada pela Microsoft como compatível com a versão de tempo de execução no cabeçalho PE. Se tal versão não for encontrada, o processo continua na etapa 3.  
  
3.  O tempo de execução exibe uma mensagem informando que a versão de tempo de execução com suporte no aplicativo está indisponível. O tempo de execução não está carregado.  
  
    > [!NOTE]
    >  Você pode suprimir a exibição dessa mensagem usando o valor de NoGuiFromShim na chave do Registro HKLM\Software\Microsoft\\.NETFramework ou usando a variável de ambiente COMPLUS_NoGuiFromShim. Por exemplo, você pode suprimir a mensagem para aplicativos que normalmente não interagem com o usuário, como instalações autônomas ou serviços do Windows. Quando a exibição dessa mensagem é suprimida, o tempo de execução grava uma mensagem no log de eventos.  Defina o valor do Registro NoGuiFromShim como 1 para suprimir esta mensagem para todos os aplicativos em um computador. Outra opção é definir a variável de ambiente COMPLUS_NoGuiFromShim como 1 para suprimir a mensagem para aplicativos executados em um contexto de usuário específico.  
  
> [!NOTE]
>  Depois que uma versão de tempo de execução é carregada, os redirecionamentos de associação de assembly pode especificar que uma versão diferente de um assembly do .NET Framework individual será carregada. Tais redirecionamentos de associação afetam somente o assembly específico que é redirecionado.  
  
## <a name="partially-qualified-assembly-names-and-side-by-side-execution"></a>Nomes parcialmente qualificados e execução lado a lado do assembly  
 Como eles são uma fonte potencial de problemas de lado a lado, referências parcialmente qualificadas do assembly podem ser usadas apenas para associar aos assemblies dentro de um diretório de aplicativo. Evite usar referências de assembly parcialmente qualificadas no seu código.  
  
 Para atenuar as referências de assembly parcialmente qualificadas no código, você pode usar o elemento [\<qualifyAssembly>](../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md) em um arquivo de configuração de aplicativo para qualificar totalmente as referências de assembly parcialmente qualificadas que ocorrem no código. Use o elemento **\<qualifyAssembly>** para especificar somente os campos que não foram definidos na referência parcial. A identidade do assembly listada no atributo **fullName** deve conter todas as informações necessárias para qualificar totalmente o nome do assembly: nome do assembly e versão, cultura e chave pública.  
  
 O exemplo a seguir mostra a entrada de arquivo de configuração de aplicativo para qualificar totalmente um assembly denominado `myAssembly`.  
  
```xml  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">   
<qualifyAssembly partialName="myAssembly"   
fullName="myAssembly,  
      version=1.0.0.0,   
publicKeyToken=...,   
      culture=neutral"/>   
</assemblyBinding>   
```  
  
 Sempre que um assembly carregar referências da instrução `myAssembly`, essas definições do arquivo de configuração fazem com que o tempo de execução realize automaticamente a conversão da referência `myAssembly` parcialmente qualificada em uma referência totalmente qualificada. Por exemplo, Assembly.Load("myAssembly") vira Assembly.Load("myAssembly, version=1.0.0.0, publicKeyToken=..., culture=neutral").  
  
> [!NOTE]
>  Você pode usar o método **LoadWithPartialName** para ignorar a restrição do Common Language Runtime que proíbe que assemblies parcialmente referenciados sejam carregados do cache de assembly global. Esse método deve ser usado apenas em cenários de comunicação remota, pois pode facilmente causar problemas na execução lado a lado.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Como habilitar e desabilitar o redirecionamento automático de associações](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)|Descreve como associar um aplicativo a uma versão específica de um assembly.|  
|[Configurando o redirecionamento de associação de assembly](../../../docs/framework/deployment/configuring-assembly-binding-redirection.md)|Explica como redirecionar referências de associação de assembly para uma versão específica de assemblies do .NET Framework.|  
|[Execução lado a lado em processo](../../../docs/framework/deployment/in-process-side-by-side-execution.md)|Discute como você pode usar a ativação de host de tempo de execução lado a lado em processo para executar várias versões do CLR em um único processo.|  
|[Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)|Fornece uma visão geral conceitual de assemblies.|  
|[Domínios do aplicativo](../../../docs/framework/app-domains/application-domains.md)|Fornece uma visão geral conceitual de domínios de aplicativos.|  
  
## <a name="reference"></a>Referência  
 Elemento [\<supportedRuntime>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
