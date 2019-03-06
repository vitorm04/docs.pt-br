---
title: Visão geral dos aplicativos de navegador XAML do WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: 6229e7fff4171f04d35bbc5be0596526f513191a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370183"
---
# <a name="wpf-xaml-browser-applications-overview"></a>Visão geral dos aplicativos de navegador XAML do WPF
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] combina recursos de aplicativos Web e aplicativos cliente avançados. Assim como aplicativos Web, os XBAPs podem ser implantados em um servidor Web e iniciados no Internet Explorer ou no Firefox. Como aplicativos de cliente rico, XBAPs podem tirar proveito dos recursos do WPF. O desenvolvimento de XBAPs também é semelhante ao desenvolvimento de cliente avançado. Este tópico fornece uma introdução simples e de alto nível ao desenvolvimento de XBAP e descreve em que o desenvolvimento XBAP difere do desenvolvimento padrão de cliente avançado.  
  
 Esse tópico contém as seguintes seções:  
  
-   [Criando um novo aplicativo de navegador XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)  
  
-   [Implantando um XBAP](#deploying_a_xbap)  
  
-   [Comunicando-se com a página da Web de host](#communicating_with_the_host_web_page)  
  
-   [Considerações sobre segurança de XBAP](#xbap_security_considerations)  
  
-   [Considerações sobre desempenho de tempo de início de XBAP](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Criando um novo aplicativo de navegador XAML (XBAP)  
 A maneira mais simples para criar um novo projeto XBAP é com o Microsoft Visual Studio. Ao criar um novo projeto, selecione **Aplicativo de Navegador do WPF** na lista de modelos. Para obter mais informações, confira [Como: Criar um novo projeto de aplicativo de navegador WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).  
  
 Quando você executa o projeto XBAP, ele é aberto em uma janela do navegador, em vez de uma janela autônoma. Quando você depura o XBAP no Visual Studio, o aplicativo é executado com permissão de zona da Internet e, portanto, gerará exceções de segurança se essas permissões forem excedidas. Para obter mais informações, consulte [Segurança](../security-wpf.md) e [Segurança de confiança parcial do WPF](../wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Se você não estiver desenvolvendo com Visual Studio ou aprender mais sobre os arquivos de projeto, consulte [criando um aplicativo WPF](building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Implantando um XBAP  
 Quando você compila um XBAP, a saída inclui os três arquivos a seguir:  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|Executável (.exe)|Este arquivo contém o código compilado e tem uma extensão .exe.|  
|Manifesto do aplicativo (.manifest)|Este arquivo contém os metadados associados ao aplicativo e tem uma extensão .manifest.|  
|Manifesto de implantação (.xbap)|Esse arquivo contém as informações que o ClickOnce usa para implantar o aplicativo e tem a extensão. xbap.|  
  
 Você implanta XBAPs em um servidor Web, por exemplo o [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou versões posteriores. Você não precisa instalar o .NET Framework no servidor Web, mas você deve registrar o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] extensões de nome de arquivo e tipos. Para obter mais informações, consulte [Configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Para preparar seu XBAP para implantação, copie o .exe e os manifestos associados para o servidor Web. Crie uma página HTML que contenha um hiperlink para abrir o manifesto de implantação, que é o arquivo que tem a extensão .xbap. Quando o usuário clica no link para o arquivo. xbap, o ClickOnce manipula automaticamente a mecânica de baixar e inicializar o aplicativo. O exemplo de código a seguir mostra uma página HTML que contém um hiperlink que aponta para um XBAP.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Você também pode hospedar um XBAP no quadro de uma página da Web. Crie uma página da Web com um ou mais quadros. Defina a propriedade de origem de um quadro como o arquivo de manifesto de implantação. Se você quiser usar o mecanismo interno para se comunicar entre a página da Web de hospedagem e o XBAP, deverá hospedar o aplicativo em um quadro. O exemplo de código a seguir mostra uma página HTML com dois quadros; a fonte para o segundo quadro está definida como um XBAP.  
  
```html
<html>   
    <head>
        <title>A page with frames</title>
    </head>  
    <frameset cols="50%,50%">   
        <frame src="introduction.htm">   
        <frame src="XbapEx.xbap">   
    </frameset>   
</html>  
```  
  
### <a name="clearing-cached-xbaps"></a>Limpando XBAPs em cache  
 Em algumas situações, depois de recompilar e iniciar o XBAP, você pode achar que uma versão anterior do XBAP está aberta. Por exemplo, esse comportamento pode ocorrer quando o número de versão do assembly do XBAP é estático e você inicia o XBAP através da linha de comando. Nesse caso, como o número de versão entre a versão em cache (a versão que foi anteriormente iniciada) e a nova versão permanece o mesmo, a nova versão do XBAP não é baixada. Em vez disso, é carregada a versão em cache.  
  
 Nessas situações, você pode remover a versão em cache usando o **Mage** (instalado com o Visual Studio ou o SDK do Windows) de comando no prompt de comando. O comando a seguir limpa o cache do aplicativo.  
  
 ```console
 Mage.exe -cc
 ```
  
 Esse comando garante que a versão mais recente do seu XBAP será iniciada. Quando você depura seu aplicativo no Visual Studio, a versão mais recente do seu XBAP deve ser iniciada. Em geral, você deve atualizar o número de versão de implantação a cada build. Para obter mais informações sobre a Mage, consulte [Mage.exe (Manifest Generation and Editing Tool)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Comunicando-se com a página da Web de host  
 Quando o aplicativo é hospedado em um quadro HTML, você pode se comunicar com a página da Web que contém o XBAP. Para fazer isso, recuperando os <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> propriedade de <xref:System.Windows.Interop.BrowserInteropHelper>. Essa propriedade retorna um objeto de script que representa a janela do HTML. Assim, você poderá acessar as propriedades, os métodos e os eventos no [objeto de janela](https://go.microsoft.com/fwlink/?LinkId=160274), usando a sintaxe de ponto regular. Você também pode acessar os métodos de script e as variáveis globais. O exemplo a seguir mostra como recuperar o objeto de script e fechar o navegador.  
  
 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>Depurando XBAPs que usam HostScript  
 Se seu XBAP usa o <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> objeto para se comunicar com a janela do HTML, há duas configurações que você deve especificar para executar e depurar o aplicativo no Visual Studio. O aplicativo deve ter acesso ao seu site de origem e você deve iniciar o aplicativo com a página HTML que contém o XBAP. As etapas a seguir descrevem como verificar essas duas configurações:  
  
1.  No Visual Studio, abra as propriedades do projeto.  
  
2.  Na guia **Segurança**, clique em **Avançada**.  
  
     A caixa de diálogo Configurações Avançadas de Segurança é exibida.  
  
3.  Verifique se a caixa de seleção **Conceder ao aplicativo acesso ao site de origem** está marcada e, em seguida, clique em **OK**.  
  
4.  Na guia **Depurar**, selecione a opção **Iniciar Navegador com URL** e especifique a URL da página HTML que contém o XBAP.  
  
5.  No Internet Explorer, clique no botão **Ferramentas** e, em seguida, selecione **Opções da Internet**.  
  
     É exibida a caixa de diálogo Opções da Internet.  
  
6.  Clique na aba **Avançado**.  
  
7.  Na lista **Configurações** em **Segurança**, marque a caixa de seleção **Permitir que o conteúdo ativo seja executado em arquivos no Meu Computador**.  
  
8.  Clique em **OK**.  
  
     As alterações entrarão em vigor depois que você reiniciar o Internet Explorer.  
  
> [!CAUTION]
>  Habilitar conteúdo ativo no Internet Explorer pode colocar seu computador em risco. Se você não quiser alterar as configurações de segurança do Internet Explorer, você pode iniciar a página HTML de um servidor e anexar o depurador do Visual Studio ao processo.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>Considerações sobre segurança de XBAP  
 Os XBAPs normalmente são executados em uma área restrita de segurança de confiança parcial, que é restrita ao conjunto de permissões da zona da Internet. Consequentemente, a implementação deve suportar o subconjunto de elementos do WPF que têm suporte na zona da Internet ou você precisa elevar as permissões do seu aplicativo. Para obter mais informações, consulte [Segurança](../security-wpf.md).  
  
 Quando você usa um <xref:System.Windows.Controls.WebBrowser> controle em seu aplicativo, o WPF cria internamente uma instância do controle WebBrowser ActiveX nativo. Quando seu aplicativo é um XBAP de confiança parcial em execução no Internet Explorer, o controle ActiveX é executado em um thread dedicado do processo do Internet Explorer. Portanto, as seguintes limitações se aplicam:  
  
-   O <xref:System.Windows.Controls.WebBrowser> controle deve fornecer um comportamento semelhante para o navegador host, incluindo as restrições de segurança. Algumas dessas restrições de segurança podem ser controladas por meio das configurações de segurança do Internet Explorer. Para obter mais informações, consulte [Segurança](../security-wpf.md).  
  
-   Uma exceção é lançada quando um XBAP é carregado entre domínios em uma página HTML.  
  
-   A entrada está em um thread separado do WPF <xref:System.Windows.Controls.WebBrowser>, portanto, a entrada do teclado não pode ser interceptada e o estado do IME não é compartilhado.  
  
-   O tempo ou a ordem de navegação pode ser diferente devido ao controle ActiveX em execução em outro thread. Por exemplo, a navegação até uma página nem sempre é cancelada ao iniciar outra solicitação de navegação.  
  
-   Um controle ActiveX personalizado pode ter problemas com a comunicação, pois o aplicativo do WPF está em execução em um thread separado.  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook> não é acionado porque <xref:System.Windows.Interop.HwndHost> não pode ser subclasse uma janela em execução em outro thread ou processo.  
  
### <a name="creating-a-full-trust-xbap"></a>Criando um XBAP de confiança total  
 Se seu XBAP requer confiança total, você pode alterar seu projeto para habilitar essa permissão. As etapas a seguir descrevem como habilitar a confiança total:  
  
1.  No Visual Studio, abra as propriedades do projeto.  
  
2.  Na guia **Segurança**, selecione a opção **Este é um aplicativo de confiança total**.  
  
 Essa configuração faz as seguintes alterações:  
  
-   No arquivo de projeto, o valor do elemento `<TargetZone>` é alterado para `Custom`.  
  
-   No manifesto do aplicativo (app.manifest), um atributo `Unrestricted="true"` é adicionado ao elemento `PermissionSet`.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Implantando um XBAP de confiança total  
 Quando você implanta um XBAP de confiança total que não segue o modelo de implantação confiável do ClickOnce, o comportamento quando o usuário executar o aplicativo dependerá da zona de segurança. Em alguns casos, o usuário receberá um aviso ao tentar instalá-lo. O usuário pode optar por continuar ou cancelar a instalação. A tabela a seguir descreve o comportamento do aplicativo para cada zona de segurança e o que você precisa fazer para que o aplicativo receba confiança total.  
  
|Zona de segurança|Comportamento|Obtendo confiança total|  
|-------------------|--------------|------------------------|  
|Computador local|Confiança total automática|Nenhuma ação é necessária.|  
|Intranet e sites confiáveis|Aviso para confiança total|Assinar o XBAP com um certificado para que o usuário veja o código-fonte no aviso.|  
|Internet|Falha com "Confiança não concedida"|Assinar o XBAP com um certificado.|  
  
> [!NOTE]
>  O comportamento descrito na tabela anterior é para XBAPs de confiança total que não seguem o modelo de implantação confiável do ClickOnce.  
  
 É recomendável que você use o modelo de implantação confiável do ClickOnce para implantar um XBAP de confiança total. Esse modelo permite que seu XBAP receba a confiança total automaticamente, independentemente da zona de segurança, de forma que o usuário não receba um aviso. Como parte desse modelo, você deve assinar o aplicativo com um certificado de um fornecedor confiável. Para obter mais informações, consulte [Visão geral da implantação de aplicativos confiáveis](/visualstudio/deployment/trusted-application-deployment-overview) e [Introdução à assinatura de código](https://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>Considerações sobre desempenho de tempo de início de XBAP  
 Um aspecto importante do desempenho do XBAP é seu tempo de início. Se um XBAP for o primeiro aplicativo do WPF a ser carregado, o tempo de *inicialização a frio* poderá ser de dez segundos ou mais. Isso ocorre porque a página de progresso é renderizada pelo WPF e tanto o CLR quanto o WPF devem ser iniciados a frio para exibir o aplicativo.  
  
 Começando com o [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], o tempo de inicialização a frio do XBAP é reduzido através da exibição de uma página de progresso não gerenciada antecipadamente no ciclo de implantação. A página de progresso é exibida quase que imediatamente após o aplicativo ser iniciado, porque ela é exibida pelo código de hospedagem nativo e é renderizada em HTML.  
  
 Além disso, a simultaneidade aprimorada da sequência de download do ClickOnce melhora a hora de início em até dez por cento. Depois que o ClickOnce baixa e valida manifestos, o download do aplicativo for iniciado e a barra de progresso começa a atualizar.  
  
## <a name="see-also"></a>Consulte também
- [Configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [Implantando um aplicativo WPF](deploying-a-wpf-application-wpf.md)
