---
title: "Tempo de inicialização do aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- splash screen [WPF], startup time
- WPF [WPF], startup time
- startup time [WPF]
- application startup [WPF]
- performance [WPF], startup time
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af07e1876666351d72eada56e7af3e787ccc90f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="application-startup-time"></a>Tempo de inicialização do aplicativo
A quantidade de tempo que é necessário para iniciar um aplicativo do WPF pode variar consideravelmente. Este tópico descreve diversas técnicas para reduzir o tempo de inicialização percebido e real de um aplicativo do WPF (Windows Presentation Foundation).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Noções básicas sobre a inicialização a frio e a inicialização a quente  
 A inicialização a frio ocorre quando o aplicativo é iniciado pela primeira vez após um reinício do sistema ou quando você inicia seu aplicativo, fecha-o e, em seguida, o inicia novamente após um longo período de tempo. Quando um aplicativo é iniciado, se as páginas necessárias (código, dados estáticos, Registro, etc) não estão presentes na lista de espera do Gerenciador de memória do Windows, ocorrem falhas de página. O acesso ao disco é necessário para colocar as páginas na memória.  
  
 A inicialização a quente ocorre quando a maioria das páginas dos componentes principais do CLR (Common Language Runtime) já está carregada na memória, o que economiza tempo valioso de acesso a disco. É por isso que um aplicativo gerenciado é iniciado mais rapidamente quando é executado pela segunda vez.  
  
## <a name="implement-a-splash-screen"></a>Implementar uma tela inicial  
 Em casos em que há um atraso significativo e inevitável entre o início de um aplicativo e a exibição da primeira interface do usuário, otimize o tempo de inicialização percebido através de uma *tela inicial*. Essa abordagem exibe uma imagem quase que imediatamente após o usuário iniciar o aplicativo. Quando o aplicativo estiver pronto para exibir sua primeira interface do usuário, a tela inicial desaparece. A partir de [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], você pode usar o <xref:System.Windows.SplashScreen> classe para implementar uma tela inicial. Para obter mais informações, consulte [Adicionar uma tela inicial a um aplicativo do WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Você também pode implementar sua própria tela inicial, usando gráficos do Win32 nativos. Exibir sua implementação antes do <xref:System.Windows.Application.Run%2A> método é chamado.  
  
## <a name="analyze-the-startup-code"></a>Analisar o código de inicialização  
 Determine o motivo de uma inicialização a frio lenta. A E/S do disco pode ser a responsável, mas nem sempre é o caso. Em geral, você deve minimizar o uso de recursos externos, como rede, serviços Web ou disco.  
  
 Antes de testar, verifique se não há outros aplicativos ou serviços em execução que usam código gerenciado ou código do WPF.  
  
 Inicie o aplicativo do WPF imediatamente após um reinício e determine quanto tempo ele demora para ser exibido. Se todas as inicializações subsequentes do seu aplicativo (inicialização a quente) forem muito mais rápidas, o problema de inicialização a frio será provavelmente causado pela E/S.  
  
 Se o problema de inicialização a frio do seu aplicativo não está relacionado à E/S, é provável que seu aplicativo realize algumas inicializações ou computações mais demoradas, aguarde algum evento ser concluído ou exija muita compilação JIT durante a inicialização. As seções a seguir descrevem algumas dessas situações com mais detalhes.  
  
## <a name="optimize-module-loading"></a>Otimizar o carregamento de módulo  
 Use ferramentas como o Explorador de Processos (Procexp.exe) e Tlist.exe para determinar quais módulos são carregados pelo seu aplicativo. O comando `Tlist <pid>` mostra todos os módulos que são carregados por um processo.  
  
 Por exemplo, se você não estiver se conectando à Web e notar que a System.Web.dll é carregada, há um módulo em seu aplicativo que faz referência a esse assembly. Verifique se a referência é necessária.  
  
 Se seu aplicativo tem vários módulos, mescle-os em um único módulo. Essa abordagem requer menos sobrecarga de carregamento de assemblies do CLR. Menos assemblies também significam que o CLR mantém menos estado.  
  
## <a name="defer-initialization-operations"></a>Adiar operações de inicialização  
 Considere a possibilidade de adiar o código de inicialização para depois que a janela do aplicativo principal for renderizada.  
  
 Lembre-se que a inicialização pode ser realizada dentro de um construtor de classe e, se o código de inicialização faz referência a outras classes, isso pode causar um efeito em cascata, em que vários construtores de classe são executados.  
  
## <a name="avoid-application-configuration"></a>Evitar a configuração do aplicativo  
 Considere a possibilidade de evitar a configuração do aplicativo. Por exemplo, se um aplicativo tem requisitos de configuração simples e tem metas de tempo de inicialização estritas, as entradas de Registro ou um arquivo INI simples pode ser uma alternativa de inicialização mais rápida.  
  
## <a name="utilize-the-gac"></a>Utilizar o GAC  
 Se um assembly não estiver instalado no GAC (cache de assembly global), haverá atrasos causados pela verificação de hash de assemblies de nomes fortes e pela validação da imagem de Ngen, se uma imagem nativa desse assembly estiver disponível no computador. A verificação de nome forte é ignorada para todos os assemblies instalados no GAC. Para obter mais informações, consulte [Gacutil.exe (ferramenta de cache de assembly global)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Usar Ngen.exe  
 Considere usar o gerador de imagem nativa (Ngen.exe) em seu aplicativo. O uso do Ngen.exe significa negociar o consumo de CPU por mais acesso ao disco, porque a imagem nativa gerada pelo Ngen.exe é, provavelmente, maior que a imagem MSIL.  
  
 Para melhorar o tempo de inicialização a quente, você deve usar sempre o Ngen.exe em seu aplicativo, porque isso evita o custo de CPU da compilação JIT do código do aplicativo.  
  
 Em alguns cenários de inicialização a frio, o uso do Ngen.exe também pode ser útil. Isso porque o compilador JIT (mscorjit.dll) não terá que ser carregado.  
  
 Ter módulos Ngen e JIT pode ter o efeito pior. Isso ocorre porque a mscorjit.dll deve ser carregada e quando o compilador JIT trabalha em seu código, muitas páginas nas imagens Ngen devem ser acessadas quando o compilador JIT lê os metadados dos assemblies.  
  
### <a name="ngen-and-clickonce"></a>Ngen e ClickOnce  
 A maneira como você planeja implantar seu aplicativo também pode fazer diferença no tempo de carregamento. A implantação de aplicativo do [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] não dá suporte ao Ngen. Se você decidir usar o Ngen.exe para o seu aplicativo, terá que usar outro mecanismo de implantação, como o Windows Installer.  
  
 Para obter mais informações, consulte [Ngen.exe (Gerador de Imagens Nativas)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Troca de base e colisões de endereço de DLL  
 Se você usar o Ngen.exe, lembre-se de que a troca de base poderá ocorrer quando as imagens nativas forem carregadas na memória. Se uma DLL não for carregada como seu endereço básico preferido, porque esse intervalo de endereços já está alocado, o carregador do Windows carregará a DLL em outro endereço, o que poderá ser uma operação demorada.  
  
 Você pode usar a ferramenta de despejo de endereço virtual (Vadump.exe) para verificar se há módulos nos quais todas as páginas são particulares. Se esse for o caso, o módulo poderá ter tido a base trocada para um endereço diferente. Portanto, suas páginas não podem ser compartilhadas.  
  
 Para obter mais informações sobre como definir o endereço básico, consulte [Ngen.exe (Gerador de Imagens Nativas)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Otimizar Authenticode  
 A verificação de Authenticode aumenta o tempo de inicialização. Os assemblies assinados por Authenticode precisam ser verificados com a AC (autoridade de certificação). Essa verificação pode ser demorada, porque pode exigir a conexão com a rede várias vezes para baixar as listas atuais de revogação de certificados. Ela também verifica se há uma cadeia completa de certificados válidos no caminho para uma raiz confiável. Isso pode significar vários segundos de atraso enquanto o assembly está sendo carregado.  
  
 Considere a instalação do Certificado de Autoridade de Certificação no computador cliente ou evite o uso de Authenticode quando for possível. Se você sabe que seu aplicativo não precisa de prova do editor, não é necessário pagar pelo custo da verificação de assinatura.  
  
 Começando com o [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], há uma opção de configuração que permite que a verificação de Authenticode seja ignorada. Para fazer isso, adicione a seguinte configuração no arquivo app.exe.config:  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 Para obter mais informações, consulte [Elemento \<generatePublisherEvidence >](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Comparar o desempenho no Windows Vista  
 O gerenciador de memória no Windows Vista tem uma tecnologia chamada SuperFetch. O SuperFetch analisa os padrões de uso de memória ao longo do tempo para determinar o conteúdo de memória ideal para um usuário específico. Ele funciona continuamente para manter esse conteúdo em todos os momentos.  
  
 Essa abordagem difere da técnica de pré-busca usada no Windows XP, que pré-carrega os dados na memória sem analisar padrões de uso. Ao longo do tempo, se o usuário usa o aplicativo do WPF com frequência no Windows Vista, o tempo de inicialização a frio do seu aplicativo pode melhorar.  
  
## <a name="use-appdomains-efficiently"></a>Usar AppDomains com eficiência  
 Se possível, carregue os assemblies em uma área do código de domínio neutro para certificar-se de que a imagem nativa, se houver, é usada em todos os AppDomains criados no aplicativo.  
  
 Para um melhor desempenho, imponha uma comunicação eficiente entre domínios, reduzindo as chamadas entre domínios. Quando possível, use chamadas sem argumentos ou com argumentos de tipo primitivo.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Usar o atributo NeutralResourcesLanguage  
 Use o <xref:System.Resources.NeutralResourcesLanguageAttribute> para especificar a cultura neutra para o <xref:System.Resources.ResourceManager>. Essa abordagem evita pesquisas de assembly sem êxito.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Usar a classe BinaryFormatter para serialização  
 Se você usar a serialização, use o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> classe o <xref:System.Xml.Serialization.XmlSerializer> classe. O <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> classe é implementada na BCL Base Class Library () no assembly mscorlib. O <xref:System.Xml.Serialization.XmlSerializer> é implementado no assembly System.Xml.dll, que pode ser um DLL adicional para carregar.  
  
 Se você deve usar o <xref:System.Xml.Serialization.XmlSerializer> classe, você pode obter o melhor desempenho se você gerar previamente o assembly de serialização.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Configurar o ClickOnce para verificar se há atualizações após a inicialização  
 Se seu aplicativo usa o [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], evite o acesso à rede na inicialização, configurando o [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] para verificar se há atualizações no site de implantação depois que o aplicativo for iniciado.  
  
 Se você usa o modelo XBAP (aplicativo de navegador XAML), tenha em mente que o [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] verifica se há atualizações no site de implantação, mesmo que o XBAP já esteja no cache do [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Para obter mais informações, consulte [Segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Configurar o serviço PresentationFontCache para iniciar automaticamente  
 O primeiro aplicativo do WPF a ser executado após um reinício é o serviço PresentationFontCache. O serviço armazena em cache as fontes do sistema, melhora o acesso à fonte e melhora o desempenho geral. Há uma sobrecarga na inicialização do serviço e, em alguns ambientes controlados, considere a possibilidade de configurar o serviço para iniciar automaticamente quando o sistema for reiniciado.  
  
## <a name="set-data-binding-programmatically"></a>Definir a vinculação de dados programaticamente  
 Em vez de usar XAML para definir o <xref:System.Windows.FrameworkElement.DataContext%2A> declarativamente para a janela principal, considere configurá-la por meio de programação no <xref:System.Windows.Application.OnActivated%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.SplashScreen>  
 <xref:System.AppDomain>  
 <xref:System.Resources.NeutralResourcesLanguageAttribute>  
 <xref:System.Resources.ResourceManager>  
 [Adicionar uma tela inicial a um aplicativo WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)  
 [Ngen.exe (Gerador de Imagens Nativas)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 [Elemento \<generatePublisherEvidence >](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
