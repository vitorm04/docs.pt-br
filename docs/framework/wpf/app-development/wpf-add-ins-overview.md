---
title: Visão geral dos suplementos do WPF
ms.date: 03/30/2017
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
ms.openlocfilehash: 36cfcaca5ae49c87916f6d7c769c878c4321247f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091610"
---
# <a name="wpf-add-ins-overview"></a>Visão geral dos suplementos do WPF
<a name="Introduction"></a> O .NET Framework inclui um modelo de suplemento que os desenvolvedores podem usar para criar aplicativos que dão suporte à extensibilidade de suplementos. Esse modelo permite a criação de suplementos que integram e estendem a funcionalidade do aplicativo. Em alguns cenários, os aplicativos também precisam exibam interfaces de usuário que são fornecidas pelos suplementos. Este tópico mostra como o WPF aumenta a modelo suplemento do .NET Framework para habilitar estes cenários, a arquitetura por trás, seus benefícios e suas limitações.  

<a name="Requirements"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 Familiaridade com o modelo de suplemento do .NET Framework é necessária. Para obter mais informações, consulte [Suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>Visão geral dos suplementos  
 Para evitar as complexidades da recompilação do aplicativo e de sua reimplantação para incorporação de uma nova funcionalidade, os aplicativos implementam mecanismos de extensibilidade que permitem aos desenvolvedores (fornecedores principais e terceiros) criar outros aplicativos que se integrem a eles. A maneira mais comum para dar suporte a esse tipo de extensibilidade é através do uso de suplementos (também conhecidos como "complementos" e "plug-ins"). Exemplos de aplicativos reais que expõem extensibilidade com suplementos incluem:  
  
-   Complementos do Internet Explorer.  
  
-   Plug-ins do Windows Media Player.  
  
-   Suplementos do Visual Studio.  
  
 Por exemplo, o modelo de suplemento do Windows Media Player permite que desenvolvedores de terceiros implementem "plug-ins" que estendam o Windows Media Player de várias maneiras, incluindo a criação de decodificadores e codificadores para formatos de mídia que não têm suporte nativo pelo Windows Media Player (por exemplo, DVD, MP3), efeitos de áudio e capas. Cada modelo de suplemento é desenvolvido para expor a funcionalidade que é exclusiva de um aplicativo, embora haja várias entidades e comportamentos que são comuns a todos os modelos de suplemento.  
  
 As três principais entidades das soluções típicas de extensibilidade de suplementos são *contratos*, *suplementos* e *aplicativos host*. Contratos definem como os suplementos se integram a aplicativos host de duas maneiras:  
  
-   Suplementos se integram à funcionalidade que é implementada por aplicativos host.  
  
-   Aplicativos host expõem a funcionalidade que os suplementos se integrem a ela.  
  
 Para que suplementos possam ser usados, é necessário que eles sejam localizados e carregados em tempo de execução pelos aplicativos host. Consequentemente, os aplicativos que dão suporte a suplementos têm as seguintes responsabilidades adicionais:  
  
-   **Descoberta**: Localizando suplementos que aderem a contratos suportados por aplicativos host.  
  
-   **Ativação**: Carregando, executando e estabelecer comunicação com suplementos.  
  
-   **Isolamento**: Usando domínios de aplicativo ou processos para estabelecer limites de isolamento que protegem aplicativos de possíveis problemas de segurança e execução com suplementos.  
  
-   **Comunicação**: Permitindo que os suplementos e aplicativos host se comuniquem entre si por limites de isolamento pela chamada de métodos e transmissão de dados.  
  
-   **Gerenciamento de tempo de vida**: Carregar e descarregar domínios de aplicativos e processos de uma maneira limpa e previsível (consulte [domínios de aplicativo](../../app-domains/application-domains.md)).  
  
-   **Controle de versão**: Garantindo que os aplicativos host e suplementos podem se comunicar quando novas versões de ambos são criadas.  
  
 Por fim, desenvolver um modelo de suplemento robusto é uma tarefa não trivial. Por esse motivo, o .NET Framework fornece uma infra-estrutura para a criação de modelos de suplementos.  
  
> [!NOTE]
>  Para obter informações mais detalhadas sobre suplementos, consulte [Suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Visão geral de modelo de suplemento do .NET Framework  
 O modelo do .NET Framework suplemento, encontrado no <xref:System.AddIn> namespace, contém um conjunto de tipos que são projetados para simplificar o desenvolvimento da extensibilidade de suplementos. A unidade fundamental de modelo de suplemento do .NET Framework é o *contrato*, que define como um aplicativo host e um suplemento se comunicam entre si. Um contrato é exposto a um aplicativo host utilizando uma *exibição* do contrato específica do aplicativo host. Da mesma forma, uma *exibição* do contrato específica do suplemento é exposta ao suplemento. Um *adaptador* é usado para permitir que um aplicativo host e um suplemento se comuniquem entre suas respectivas exibições do contrato. Contratos, exibições e adaptadores são referidos como segmentos, enquanto um conjunto de segmentos relacionados constitui um *pipeline*. Pipelines são a base sobre a qual o modelo de suplemento do .NET Framework dá suporte à descoberta, ativação, isolamento de segurança, isolamento de execução (usando domínios de aplicativos e processos), comunicação, gerenciamento de tempo de vida e controle de versão.  
  
 A soma desse suporte permite aos desenvolvedores compilar suplementos que se integram com a funcionalidade de um aplicativo host. No entanto, alguns cenários exigem aplicativos host exibam interfaces de usuário fornecidas pelos suplementos. Como cada tecnologia de apresentação no .NET Framework tem seu próprio modelo para a implementação de interfaces do usuário, o modelo de suplemento do .NET Framework não dá suporte a nenhuma tecnologia de apresentação específico. Em vez disso, o WPF estende o modelo do .NET Framework suplemento com o suporte de interface do usuário para suplementos.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Suplementos do WPF  
 O WPF, junto com o .NET Framework suplemento do modelo, permite que você direcione uma ampla variedade de cenários que exigem aplicativos host exibam interfaces de usuário dos suplementos. Em particular, estes cenários são endereçados pelo WPF com os dois modelos de programação a seguir:  
  
1.  **O suplemento retorna uma interface do usuário**. Um suplemento retorna uma interface do usuário para o aplicativo host via uma chamada de método, conforme definido pelo contrato. Esse cenário é utilizado nos seguintes casos:  
  
    -   A aparência de uma interface do usuário que é retornado por um suplemento é dependente de dados ou condições que existem somente em tempo de execução, tais como dinamicamente relatórios gerados.  
  
    -   A interface do usuário para serviços fornecidos por um suplemento difere da interface do usuário dos aplicativos host que pode usar o suplemento.  
  
    -   O suplemento principalmente executa um serviço para o aplicativo host e relata o status para o aplicativo host com uma interface do usuário.  
  
2.  **O suplemento é uma interface do usuário**. Um suplemento é uma interface do usuário, conforme definido pelo contrato. Esse cenário é utilizado nos seguintes casos:  
  
    -   Um suplemento não fornece nenhum serviço além de ser exibido, por exemplo, um anúncio.  
  
    -   A interface do usuário para serviços fornecidos por um suplemento é comum a todos os aplicativos host que podem usar esse suplemento, como uma calculadora ou um seletor de cores.  
  
 Esses cenários exigem que os objetos de interface do usuário podem ser passados entre aplicativos host e domínios de aplicativo do suplemento. Desde o modelo de suplemento depende da comunicação remota para se comunicar entre domínios de aplicativos do .NET Framework, os objetos que são passados entre eles devem ser remotos.  
  
 Um objeto remoto é uma instância de uma classe que satisfaz uma ou mais das condições a seguir:  
  
-   Deriva o <xref:System.MarshalByRefObject> classe.  
  
-   Implementa a interface <xref:System.Runtime.Serialization.ISerializable>.  
  
-   Tem o <xref:System.SerializableAttribute> atributo aplicado.  
  
> [!NOTE]
>  Para obter mais informações sobre a criação de objetos do .NET Framework que devem ser remotos, consulte [tornando os objetos em remotos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100)).  
  
 Os tipos de UI WPF não são remotos. Para resolver o problema, o WPF estende o modelo do .NET Framework suplemento para habilitar o WPF UI criadas por suplementos a ser exibida de aplicativos host. Esse suporte é fornecido pelo WPF por dois tipos: o <xref:System.AddIn.Contract.INativeHandleContract> interface e dois métodos estáticos implementados pela <xref:System.AddIn.Pipeline.FrameworkElementAdapters> classe: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Em um nível elevado, esses tipos e métodos são usados da seguinte maneira:  
  
1.  WPF exige que as interfaces de usuário fornecidas pelos suplementos sejam classes que derivam direta ou indiretamente de <xref:System.Windows.FrameworkElement>, como formas, controles, controles de usuário, painéis de layout e páginas.  
  
2.  Aonde o contrato declarar que uma interface do usuário será transmitida entre o suplemento e o aplicativo host, ele deve ser declarado como um <xref:System.AddIn.Contract.INativeHandleContract> (não um <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> é uma representação remota do suplemento a interface do usuário que pode ser passada entre limites de isolamento.  
  
3.  Antes de ser transmitido do domínio de aplicativo do suplemento, um <xref:System.Windows.FrameworkElement> é empacotado como um <xref:System.AddIn.Contract.INativeHandleContract> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Após ser transmitido ao domínio de aplicativo do aplicativo host, o <xref:System.AddIn.Contract.INativeHandleContract> deve ser reempacotado como um <xref:System.Windows.FrameworkElement> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Como <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> são usados dependendo do cenário específico. As seções a seguir fornecem detalhes para cada modelo de programação.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>O suplemento retorna uma interface do usuário  
 Para um suplemento retornar uma interface do usuário para um aplicativo host, são necessários:  
  
1.  O aplicativo host, suplemento e pipeline devem ser criados, conforme descrito pelo .NET Framework [suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentação.  
  
2.  O contrato deve implementar <xref:System.AddIn.Contract.IContract> e, para retornar uma interface do usuário, o contrato deve declarar um método com um valor de retorno do tipo <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  A interface do usuário que é passado entre o suplemento e o aplicativo host deve derivar diretamente ou indiretamente de <xref:System.Windows.FrameworkElement>.  
  
4.  A interface do usuário que é retornado pelo suplemento deve ser convertido de um <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.  
  
5.  A interface do usuário que é retornado deve ser convertido de um <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> depois de cruzar o limite de isolamento.  
  
6.  O aplicativo host exibe retornado <xref:System.Windows.FrameworkElement>.  
  
 Para obter um exemplo que demonstra como implementar um suplemento que retorna uma interface do usuário, consulte [criar um suplemento que retorna uma interface do usuário](how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>O suplemento é uma interface do usuário  
 Quando um suplemento é uma interface do usuário, são necessários os seguintes:  
  
1.  O aplicativo host, suplemento e pipeline devem ser criados, conforme descrito pelo .NET Framework [suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)) documentação.  
  
2.  A interface de contrato para o suplemento deve implementar <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  O suplemento que é passado para o aplicativo host deve derivar direta ou indiretamente de <xref:System.Windows.FrameworkElement>.  
  
4.  O suplemento deve ser convertido de um <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.  
  
5.  O suplemento deve ser convertido de um <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> depois de cruzar o limite de isolamento.  
  
6.  O aplicativo host exibe retornado <xref:System.Windows.FrameworkElement>.  
  
 Para obter um exemplo que demonstra como implementar um suplemento que é uma interface do usuário, consulte [criar um suplemento que é uma interface do usuário](how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Retornando múltiplas interfaces do usuário de um suplemento  
 Suplementos muitas vezes fornecem várias interfaces de usuário para aplicativos host exibam. Por exemplo, considere um suplemento que é uma interface do usuário que também fornece informações de status ao aplicativo host, também como uma interface do usuário. Um suplemento como esse pode ser implementado pelo uso de uma combinação de técnicas de ambos os modelos [O suplemento retorna uma interface do usuário](#ReturnUIFromAddInContract) e [O suplemento é uma interface do usuário](#AddInIsAUI).  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Suplementos e aplicativos de navegação XAML  
 Nos exemplos até agora, o aplicativo host tem sido um aplicativo autônomo instalado. Mas [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] também podem hospedar suplementos, embora com os seguintes requisitos adicionais de build e implementação:  
  
-   O manifesto do aplicativo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] deve ser configurado especialmente para baixar o pipeline (pastas e assemblies) e o assembly do suplemento para o cache do aplicativo [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] no computador cliente, na mesma pasta que o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   O código do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] para descobrir e carregar suplementos deve usar o cache de aplicativo [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] para o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] como o local do pipeline e do suplemento.  
  
-   O [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] deverá carregar o suplemento em um contexto de segurança especial se o suplemento fizer referência a arquivos flexíveis localizados no site de origem; quando hospedados por [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], suplementos poderão referenciar apenas arquivos flexíveis localizados no site de origem do aplicativo host.  
  
 Essas tarefas são descritas detalhadamente nas subseções a seguir.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Configurar o pipeline e o suplemento para a implantação do ClickOnce  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] são baixados e executados de uma pasta segura no [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] cache de implantação. Para que um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hospede um suplemento, o assembly do suplemento e do pipeline também devem ser baixados para a pasta segura. Para fazer isso, você precisa configurar o manifesto do aplicativo para incluir ambos o assembly do suplemento e do pipeline para baixar. Isso é feito com mais facilidade no [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], embora o assembly do suplemento e o do pipeline precisem estar na pasta raiz do projeto do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] host para que [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] detecte os assemblies do pipeline.  
  
 Consequentemente, a primeira etapa é compilar o assembly do suplemento e do pipeline para a raiz do projeto do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], definindo a saída de build de cada projeto de assembly do pipeline e do suplemento. A tabela a seguir mostra os caminhos de saída de build para projetos de assembly do pipeline e projetos de assembly do suplemento que estão na mesma solução e pasta raiz que o projeto do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] host.  
  
 Tabela 1: Criar caminhos de saída para os Assemblies do Pipeline que são hospedados por um XBAP  
  
|Projeto de assembly do pipeline|Caminho de saída de build|  
|-------------------------------|-----------------------|  
|Contrato|`..\HostXBAP\Contracts\`|  
|Exibição do suplemento|`..\HostXBAP\AddInViews\`|  
|Adaptador no lado do suplemento|`..\HostXBAP\AddInSideAdapters\`|  
|Adaptador no lado do host|`..\HostXBAP\HostSideAdapters\`|  
|Suplemento|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 A próxima etapa é especificar os assemblies de pipeline e o assembly do suplemento como os arquivos de conteúdo do [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] em [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], fazendo o seguinte:  
  
1.  Incluindo o assembly do pipeline e do suplemento no projeto clicando com o botão direito do mouse em cada pasta de pipeline no Gerenciador de Soluções e escolhendo **Incluir no Projeto**.  
  
2.  Definindo a **Ação de Build** de cada assembly do pipeline e assembly do suplemento para **Conteúdo** da janela **Propriedades**.  
  
 A etapa final é configurar o manifesto do aplicativo para incluir os arquivos do assembly do pipeline e o arquivo do assembly do suplemento para download. Os arquivos devem estar localizados em pastas na raiz da pasta no cache do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] que o aplicativo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] ocupa. A configuração pode ser obtida em [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], fazendo o seguinte:  
  
1.  Clique com o botão direito do mouse no projeto do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], clique em **Propriedades**, clique em **Publicar** e, em seguida, clique no botão **Arquivos de Aplicativo**.  
  
2.  Na caixa de diálogo **Arquivos de Aplicativo**, defina o **Status da Publicação** de cada DLL de suplemento e de pipeline a **Incluir (Auto)** e defina o **Grupo de Download** para cada DLL de pipeline e de suplemento para **(Obrigatório)**.  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>Usando o pipeline e o suplemento da base de aplicativo  
 Quando o pipeline e o suplemento são configurados para a implantação do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], eles são baixados para a mesma pasta de cache do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] que o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Para usar o pipeline e o suplemento por meio do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], o código do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] deve obtê-los da base de aplicativo. Os diversos tipos e membros do modelo do .NET Framework suplemento para usar pipelines e suplementos fornecem suporte especial para esse cenário. Em primeiro lugar, o caminho é identificado pelo <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> valor de enumeração. Você pode usar esse valor com sobrecargas de membros de suplemento pertinentes para usar pipelines que incluem o seguinte:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Acessar o site de origem do host  
 Para garantir que um suplemento possa referenciar arquivos do site de origem, o suplemento deve ser carregado com isolamento de segurança que é equivalente ao do aplicativo host. Esse nível de segurança é identificado pelo <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> valor de enumeração e passado para o <xref:System.AddIn.Hosting.AddInToken.Activate%2A> método quando um suplemento é ativado.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Arquitetura de suplemento do WPF  
 O nível mais alto, como vimos, o WPF permite suplementos do .NET Framework implementar interfaces do usuário (que derivam direta ou indiretamente <xref:System.Windows.FrameworkElement>) usando <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. O resultado é que o aplicativo host é retornado um <xref:System.Windows.FrameworkElement> que é exibido na interface do usuário no aplicativo host.  
  
 Para cenários simples, da interface do usuário suplementar, isso é o máximo de detalhes que um desenvolvedor precisa. Para cenários mais complexos, especialmente aqueles que tentam utilizar serviços adicionais do WPF como layout, recursos e associação de dados, dados de conhecimento mais detalhado de como o WPF estende o modelo do .NET Framework suplemento com o suporte de interface do usuário é necessária para compreender seus benefícios e limitações.  
  
 Fundamentalmente, WPF não passa uma interface do usuário de um suplemento para um aplicativo host; em vez disso, o WPF passa o identificador de janela Win32 para a interface do usuário por meio da interoperabilidade do WPF. Assim, quando uma interface do usuário de um suplemento é passado para um aplicativo host, ocorre o seguinte:  
  
-   No lado do suplemento, o WPF adquire um identificador de janela para a interface do usuário que será exibido pelo aplicativo host. O identificador de janela é encapsulado por uma classe interna do WPF que deriva <xref:System.Windows.Interop.HwndSource> e implementa <xref:System.AddIn.Contract.INativeHandleContract>. Uma instância dessa classe é retornada por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> e é empacotada do domínio de aplicativo do suplemento ao domínio de aplicativo do aplicativo host.  
  
-   No lado do aplicativo host, o WPF reempacota os <xref:System.Windows.Interop.HwndSource> como uma classe interna do WPF que deriva <xref:System.Windows.Interop.HwndHost> e consome <xref:System.AddIn.Contract.INativeHandleContract>. Uma instância dessa classe é retornada por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> para o aplicativo host.  
  
 <xref:System.Windows.Interop.HwndHost> existe para exibir as interfaces do usuário, identificados por identificadores de janela WPF de interfaces do usuário. Para obter mais informações, consulte [Interoperação Win32 e WPF](../advanced/wpf-and-win32-interoperation.md).  
  
 Em resumo, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existem para permitir que o identificador de janela para uma UI do WPF a ser passado de um suplemento para um aplicativo host, onde ele é encapsulado por um <xref:System.Windows.Interop.HwndHost> e exibidas da interface do usuário do aplicativo host.  
  
> [!NOTE]
>  Como o aplicativo host recebe um <xref:System.Windows.Interop.HwndHost>, o aplicativo host não é possível converter o objeto que é retornado por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> para o tipo é implementado pelo suplemento (por exemplo, um <xref:System.Windows.Controls.UserControl>).  
  
 Por sua natureza, <xref:System.Windows.Interop.HwndHost> tem certas limitações que afetam como aplicativos host podem utilizá-los. No entanto, o WPF estende <xref:System.Windows.Interop.HwndHost> com vários recursos para cenários de suplemento. Essas limitações e benefícios são descritos abaixo.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>Benefícios de suplementos do WPF  
 Como interfaces de usuário em suplementos do WPF são exibidos em aplicativos host usando uma classe interna que deriva de <xref:System.Windows.Interop.HwndHost>, essas interfaces de usuário são limitadas pelas funcionalidades de <xref:System.Windows.Interop.HwndHost> em relação aos serviços de UI WPF, como o layout, renderização, vinculação de dados, estilos, modelos e recursos. No entanto, o WPF aumenta sua interno <xref:System.Windows.Interop.HwndHost> subclasse com recursos adicionais que incluem o seguinte:  
  
-   Uso da tecla TAB entre a interface do usuário de um aplicativo host e interface do usuário de um suplemento. Observe que o modelo de programação "suplemento é uma interface do usuário" requer que o adaptador do lado do suplemento substituir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> para habilitar tabulações, seja o suplemento é totalmente confiável ou parcialmente confiável.  
  
-   Respeitar requisitos de acessibilidade para interfaces do usuário do suplemento que são exibidos a partir de interfaces de usuário do aplicativo host.  
  
-   Permitindo que os aplicativos do WPF executar com segurança em vários cenários de domínio de aplicativo.  
  
-   Impedir o acesso para interface do usuário do suplemento identificadores de janela ao executar os suplementos com isolamento de segurança (ou seja, uma proteção de segurança de confiança parcial). Chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> garante essa segurança:  
  
    -   Para o modelo de programação "suplemento retorna uma interface do usuário", a única maneira de passar o identificador de janela para uma interface de usuário além do limite de isolamento é chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Para o modelo de programação "suplemento é uma interface do usuário", substituindo <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> no adaptador do lado do suplemento e chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (conforme mostrado nos exemplos anteriores) é necessária, como é chamar o adaptador lado do suplemento `QueryContract` implementação desde o adaptador do lado do host.  
  
-   Fornecer proteção contra múltiplas execuções de domínio do aplicativo. Devido a limitações com domínios do aplicativo, as exceções sem tratamento que forem lançadas em domínios do aplicativo do suplemento fazem com que todo o aplicativo falhe, mesmo com a existência do limite de isolamento. No entanto, o WPF e o modelo de suplemento do .NET Framework fornecem uma maneira simples de contornar esse problema e melhorar a estabilidade do aplicativo. Um suplemento do WPF que exibe uma interface do usuário cria um <xref:System.Windows.Threading.Dispatcher> para o thread que o domínio de aplicativo é executado, se o aplicativo host é um aplicativo WPF. Você pode detectar exceções sem tratamento que ocorrem no domínio do aplicativo manipulando o <xref:System.Windows.Threading.Dispatcher.UnhandledException> eventos do WPF adicionar-in <xref:System.Windows.Threading.Dispatcher>. Você pode obter o <xref:System.Windows.Threading.Dispatcher> do <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> propriedade.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>Limitações de suplementos WPF  
 Além dos benefícios que o WPF adiciona os comportamentos padrão fornecidos pelo <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>e identificadores de janela, também há limitações para interfaces do usuário do suplemento que são exibidas em aplicativos host:  
  
-   Interfaces de usuário em suplementos exibidos a partir de um aplicativo host não respeitam o comportamento de recorte do aplicativo host.  
  
-   O conceito de *espaço aéreo* em cenários de interoperabilidade também se aplica a suplementos (consulte [Visão geral das regiões de tecnologia](../advanced/technology-regions-overview.md)).  
  
-   Serviços de interface do usuário de um aplicativo host, como herança de recursos, associação de dados e comandos, não estão automaticamente disponíveis para o suplemento interfaces do usuário. Para fornecer esses serviços para o suplemento, você precisa atualizar o pipeline.  
  
-   Uma interface de usuário não pode ser girada, dimensionada, distorcida ou contrário é afetado por uma transformação (consulte [visão geral de transformações](../graphics-multimedia/transforms-overview.md)).  
  
-   Conteúdo dentro de interfaces do usuário do suplemento que é renderizado por operações de desenho a <xref:System.Drawing> namespace pode incluir combinação alfa. No entanto, uma interface de usuário e o aplicativo de host da interface do usuário que o contém devem ser 100% opaco; em outras palavras, o `Opacity` propriedade nos dois deve ser definida como 1.  
  
-   Se o <xref:System.Windows.Window.AllowsTransparency%2A> de uma janela no aplicativo host que contém uma interface de usuário estiver definida como `true`, o suplemento é invisível. Isso é verdadeiro mesmo se a interface do usuário suplemento for 100% opaco (ou seja, o `Opacity` propriedade tem um valor de 1).  
  
-   Uma interface de usuário deve aparecer sobre outros elementos do WPF na mesma janela de nível superior.  
  
-   Nenhuma parte de interface do usuário de um suplemento pode ser renderizado usando um <xref:System.Windows.Media.VisualBrush>. Em vez disso, o suplemento pode tirar um instantâneo da interface do usuário gerada para criar um bitmap que pode ser passado para o aplicativo host usando métodos definidos pelo contrato.  
  
-   Arquivos de mídia não podem ser executados de um <xref:System.Windows.Controls.MediaElement> em uma interface de usuário.  
  
-   Eventos de mouse gerados para o suplemento da interface do usuário não são recebidos nem gerados pelo aplicativo host e o `IsMouseOver` propriedade para a interface do usuário do aplicativo host tem um valor de `false`.  
  
-   Quando o foco alterna entre os controles em um suplemento da interface do usuário, o `GotFocus` e `LostFocus` eventos não são recebidos nem gerados pelo aplicativo host.  
  
-   A parte de um aplicativo host que contém uma interface de usuário é exibida em branco quando impressa.  
  
-   Todos os dispatchers (consulte <xref:System.Windows.Threading.Dispatcher>) criado pelo suplemento interface do usuário deve ser desligado manualmente antes que o suplemento proprietário seja descarregado se o aplicativo host continua a execução. O contrato pode implementar métodos que permitem que o aplicativo host sinalize o suplemento antes que o suplemento seja descarregado, permitindo assim que a interface do suplemento desligue seus dispatchers.  
  
-   Se uma interface de usuário é um <xref:System.Windows.Controls.InkCanvas> ou contém um <xref:System.Windows.Controls.InkCanvas>, é possível descarregar o suplemento.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Otimização do desempenho  
 Por padrão, quando vários domínios de aplicativo são usados, os vários assemblies do .NET Framework necessários para cada aplicativo são todos carregados no domínio do aplicativo. Como resultado, o tempo necessário para criar novos domínios de aplicativo e iniciar aplicativos neles pode afetar o desempenho. No entanto, o .NET Framework fornece uma maneira de reduzir os tempos de inicialização instruindo os aplicativos a compartilhar assemblies entre domínios de aplicativo se eles já estiverem carregados. Você pode fazer isso usando o <xref:System.LoaderOptimizationAttribute> atributo, que deve ser aplicado ao método de ponto de entrada (`Main`). Nesse caso, você deve usar apenas código para implementar sua definição de aplicativo (consulte [Visão geral de gerenciamento do aplicativo](application-management-overview.md)).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.LoaderOptimizationAttribute>
- [Suplementos e extensibilidade](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [Domínios do aplicativo](../../app-domains/application-domains.md)
- [Visão geral de comunicação remota do .NET framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kwdt6w2k(v=vs.100))
- [Tornando os objetos em remotos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/wcf3swha(v=vs.100))
- [Tópicos explicativos ](how-to-topics.md)
