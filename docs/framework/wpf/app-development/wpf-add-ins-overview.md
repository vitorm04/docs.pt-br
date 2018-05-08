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
ms.openlocfilehash: 942f5706a83a9f9e9cd969701ed5625c57b76f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-add-ins-overview"></a>Visão geral dos suplementos do WPF
<a name="Introduction"></a> O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] inclui um modelo de suplemento que os desenvolvedores podem usar para criar aplicativos que deem suporte a extensibilidade de suplemento. Esse modelo permite a criação de suplementos que integram e estendem a funcionalidade do aplicativo. Em alguns cenários, os aplicativos também devem exibir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] que são fornecidas por suplementos. Este tópico mostra como o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aumenta o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para habilitar estes cenários, a arquitetura por trás dele, seus benefícios e suas limitações.  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>Pré-requisitos  
 A familiaridade com o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é requerida. Para obter mais informações, consulte [Suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md).  
  
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
  
-   **Descoberta**: encontrar suplementos que aderem a contratos com suporte por aplicativos host.  
  
-   **Ativação**: carregar, executar e estabelecer comunicação com suplementos.  
  
-   **Isolamento**: usar domínios do aplicativo ou processos para estabelecer limites de isolamento que protegem aplicativos de possíveis problemas de execução e segurança com suplementos.  
  
-   **Comunicação**: permitir, por meio da chamada de métodos e transmissão de dados, que suplementos e aplicativos host se comuniquem uns com os outros através de limites de isolamento.  
  
-   **Gerenciamento de tempo de vida**: Carregando e descarregando domínios do aplicativo e processos de uma maneira limpa e previsível (consulte [Domínios do aplicativo](../../../../docs/framework/app-domains/application-domains.md)).  
  
-   **Controle de versão**: garantir que os aplicativos host e suplementos possam se comunicar quando novas versões de qualquer um deles forem criadas.  
  
 Por fim, desenvolver um modelo de suplemento robusto é uma tarefa não trivial. Por esse motivo, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fornece uma infraestrutura para o build de modelos de suplementos.  
  
> [!NOTE]
>  Para obter informações mais detalhadas sobre suplementos, consulte [Suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md).  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>Visão geral de modelo de suplemento do .NET Framework  
 O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] adicionar no modelo, encontrado no <xref:System.AddIn> namespace, contém um conjunto de tipos que são projetados para simplificar o desenvolvimento de extensibilidade do suplemento. A unidade fundamental do modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] é o *contrato*, que define como um aplicativo host e um suplemento se comunicam um com o outro. Um contrato é exposto a um aplicativo host utilizando uma *exibição* do contrato específica do aplicativo host. Da mesma forma, uma *exibição* do contrato específica do suplemento é exposta ao suplemento. Um *adaptador* é usado para permitir que um aplicativo host e um suplemento se comuniquem entre suas respectivas exibições do contrato. Contratos, exibições e adaptadores são referidos como segmentos, enquanto um conjunto de segmentos relacionados constitui um *pipeline*. Pipelines são a base sobre a qual o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dá suporte à descoberta, ativação, isolamento de segurança, isolamento de execução (usando tanto processos quanto domínios do aplicativo), comunicação, gerenciamento de tempo de vida e controle de versão.  
  
 A soma desse suporte permite aos desenvolvedores compilar suplementos que se integram com a funcionalidade de um aplicativo host. No entanto, alguns cenários exigem que os aplicativos host exibam [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fornecidas pelos suplementos. Já que cada tecnologia de apresentação no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tem seu próprio modelo para implementação de [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] não dá suporte a nenhuma tecnologia de apresentação específica. Em vez disso, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] estende o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] com suporte da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a suplementos.  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>Suplementos do WPF  
 O [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], em conjunto com o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], permite que você direcione uma ampla variedade de cenários que exigem que os aplicativos de host para exibir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] dos suplementos. Em particular, estes cenários são endereçados pelo [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] com os dois modelos de programação a seguir:  
  
1.  **O suplemento retorna uma interface do usuário**. Um suplemento retorna uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ao aplicativo host via uma chamada de método, conforme definido pelo contrato. Esse cenário é utilizado nos seguintes casos:  
  
    -   A aparência de uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que é retornada por um suplemento é dependente de dados ou condições que existem somente em tempo de execução, por exemplo, relatórios gerados dinamicamente.  
  
    -   A [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para serviços fornecidos por um suplemento difere da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dos aplicativos host que podem usar o suplemento.  
  
    -   Como funções principais, o suplemento executa um serviço para o aplicativo host e relata o status ao aplicativo host com uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
2.  **O suplemento é uma interface do usuário**. Um suplemento é uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], conforme definido pelo contrato. Esse cenário é utilizado nos seguintes casos:  
  
    -   Um suplemento não fornece nenhum serviço além de ser exibido, por exemplo, um anúncio.  
  
    -   A [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para serviços fornecidos por um suplemento é comum a todos os aplicativos host que podem usar esse suplemento, por exemplo, uma calculadora ou um seletor de cor.  
  
 Esses cenários exigem que objetos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] possam ser passados entre aplicativos host e domínios do aplicativo do suplemento. Uma vez que o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] depende da comunicação remota para a comunicação entre domínios do aplicativo, os objetos que são passados entre eles devem ser remotos.  
  
 Um objeto remoto é uma instância de uma classe que satisfaz uma ou mais das condições a seguir:  
  
-   Deriva a <xref:System.MarshalByRefObject> classe.  
  
-   Implementa a interface <xref:System.Runtime.Serialization.ISerializable>.  
  
-   Tem o <xref:System.SerializableAttribute> atributo aplicado.  
  
> [!NOTE]
>  Para obter mais informações sobre a criação de objetos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remotos, consulte [Transformar os objetos em remotos](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a).  
  
 Os tipos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] não são remotos. Para resolver o problema, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] estende o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para habilitar uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] criada pelos suplementos para ser exibida de aplicativos host. Esse suporte é fornecido por [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] por dois tipos: o <xref:System.AddIn.Contract.INativeHandleContract> interface e dois métodos estáticos implementados pelo <xref:System.AddIn.Pipeline.FrameworkElementAdapters> classe: <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. Em um nível elevado, esses tipos e métodos são usados da seguinte maneira:  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] requer que [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] fornecidas pelos suplementos são classes que derivam direta ou indiretamente de <xref:System.Windows.FrameworkElement>, como formas, controles, controles de usuário, painéis de layout e páginas.  
  
2.  Sempre que o contrato declara que uma interface do usuário será transmitida entre o suplemento e o aplicativo de host, ele deve ser declarado como um <xref:System.AddIn.Contract.INativeHandleContract> (não um <xref:System.Windows.FrameworkElement>); <xref:System.AddIn.Contract.INativeHandleContract> é uma representação remota do suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que pode ser transmitido por limites de isolamento.  
  
3.  Antes de ser transmitido do domínio de aplicativo do suplemento, um <xref:System.Windows.FrameworkElement> é empacotado como um <xref:System.AddIn.Contract.INativeHandleContract> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
4.  Após ser transmitido ao domínio de aplicativo do aplicativo host, o <xref:System.AddIn.Contract.INativeHandleContract> devem ser empacotados novamente como um <xref:System.Windows.FrameworkElement> chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>.  
  
 Como <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>, e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> são usados dependendo do cenário específico. As seções a seguir fornecem detalhes para cada modelo de programação.  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>O suplemento retorna uma interface do usuário  
 Para um suplemento retornar uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para um aplicativo host, é necessário o seguinte:  
  
1.  O aplicativo host, o suplemento e o pipeline devem ser criados, conforme descrito pela documentação [Suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md) do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
2.  O contrato deve implementar <xref:System.AddIn.Contract.IContract> e, para retornar um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], o contrato deve declarar um método com um valor de retorno do tipo <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que é transmitido entre o suplemento e o host de aplicativo deve derivar direta ou indiretamente de <xref:System.Windows.FrameworkElement>.  
  
4.  O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que é retornado pelo suplemento deve ser convertido de um <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.  
  
5.  O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que é retornado deve ser convertido de um <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> após cruzar o limite de isolamento.  
  
6.  O aplicativo host exibe retornado <xref:System.Windows.FrameworkElement>.  
  
 Para obter um exemplo que demonstra como implementar um suplemento que retorna um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Criar um suplemento que retorna uma interface do usuário](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md).  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>O suplemento é uma interface do usuário  
 Quando um suplemento é uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], há os requisitos a seguir:  
  
1.  O aplicativo host, o suplemento e o pipeline devem ser criados, conforme descrito pela documentação [Suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md) do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
2.  A interface de contrato para o suplemento deve implementar <xref:System.AddIn.Contract.INativeHandleContract>.  
  
3.  O suplemento que é passado para o aplicativo host deve direta ou indiretamente derivar de <xref:System.Windows.FrameworkElement>.  
  
4.  O suplemento deve ser convertido de um <xref:System.Windows.FrameworkElement> para um <xref:System.AddIn.Contract.INativeHandleContract> antes de cruzar o limite de isolamento.  
  
5.  O suplemento deve ser convertido de um <xref:System.AddIn.Contract.INativeHandleContract> para um <xref:System.Windows.FrameworkElement> após cruzar o limite de isolamento.  
  
6.  O aplicativo host exibe retornado <xref:System.Windows.FrameworkElement>.  
  
 Para obter um exemplo que demonstra como implementar um suplemento que é uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Criar um suplemento que é uma interface do usuário](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md).  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>Retornando múltiplas interfaces do usuário de um suplemento  
 Suplementos muitas vezes fornecem várias [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] para serem exibidas por aplicativos de host. Por exemplo, considere um suplemento que é uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que também fornece informações de status ao aplicativo host, também como uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Um suplemento como esse pode ser implementado pelo uso de uma combinação de técnicas de ambos os modelos [O suplemento retorna uma interface do usuário](#ReturnUIFromAddInContract) e [O suplemento é uma interface do usuário](#AddInIsAUI).  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>Suplementos e aplicativos de navegação XAML  
 Nos exemplos até agora, o aplicativo host tem sido um aplicativo autônomo instalado. Mas [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] também podem hospedar suplementos, embora com os seguintes requisitos adicionais de build e implementação:  
  
-   O manifesto do aplicativo [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] deve ser configurado especialmente para baixar o pipeline (pastas e assemblies) e o assembly do suplemento para o cache do aplicativo [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] no computador cliente, na mesma pasta que o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)].  
  
-   O código do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] para descobrir e carregar suplementos deve usar o cache de aplicativo [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] para o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] como o local do pipeline e do suplemento.  
  
-   O [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] deverá carregar o suplemento em um contexto de segurança especial se o suplemento fizer referência a arquivos flexíveis localizados no site de origem; quando hospedados por [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], suplementos poderão referenciar apenas arquivos flexíveis localizados no site de origem do aplicativo host.  
  
 Essas tarefas são descritas detalhadamente nas subseções a seguir.  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>Configurar o pipeline e o suplemento para a implantação do ClickOnce  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] são baixados e executados de uma pasta segura no cache de implantação do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)]. Para que um [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] hospede um suplemento, o assembly do suplemento e do pipeline também devem ser baixados para a pasta segura. Para fazer isso, você precisa configurar o manifesto do aplicativo para incluir ambos o assembly do suplemento e do pipeline para baixar. Isso é feito com mais facilidade no [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], embora o assembly do suplemento e o do pipeline precisem estar na pasta raiz do projeto do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] host para que [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] detecte os assemblies do pipeline.  
  
 Consequentemente, a primeira etapa é compilar o assembly do suplemento e do pipeline para a raiz do projeto do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], definindo a saída de build de cada projeto de assembly do pipeline e do suplemento. A tabela a seguir mostra os caminhos de saída de build para projetos de assembly do pipeline e projetos de assembly do suplemento que estão na mesma solução e pasta raiz que o projeto do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] host.  
  
 Tabela 1: caminhos de saída de build para os assemblies do pipeline hospedados por um XBAP  
  
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
 Quando o pipeline e o suplemento são configurados para a implantação do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)], eles são baixados para a mesma pasta de cache do [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] que o [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]. Para usar o pipeline e o suplemento por meio do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], o código do [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] deve obtê-los da base de aplicativo. Os diversos tipos e membros do modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para usar pipelines e suplementos dão suporte especial para esse cenário. Em primeiro lugar, o caminho é identificado pelo <xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase> valor de enumeração. Você pode usar esse valor com sobrecargas de membros de suplemento pertinentes para usar pipelines que incluem o seguinte:  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>Acessar o site de origem do host  
 Para garantir que um suplemento possa referenciar arquivos do site de origem, o suplemento deve ser carregado com isolamento de segurança que é equivalente ao do aplicativo host. Esse nível de segurança é identificado pelo <xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType> valor de enumeração e passados para o <xref:System.AddIn.Hosting.AddInToken.Activate%2A> método quando um suplemento é ativado.  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>Arquitetura de suplemento do WPF  
 O nível mais alto, como vimos, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permite [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] suplementos para implementar [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] (que derivam direta ou indiretamente <xref:System.Windows.FrameworkElement>) usando <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. O resultado é que o aplicativo host é retornado um <xref:System.Windows.FrameworkElement> que é exibido no [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] no aplicativo host.  
  
 Para cenários de suplemento de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] simples, isso é o máximo de detalhamento de que um desenvolvedor precisa. Para cenários mais complexos, especialmente aqueles que tentam utilizar serviços [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] adicionais como o layout, recursos e associação de dados, um conhecimento mais detalhado de como o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] estende o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] com suporte à [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é necessário para entender seus benefícios e limitações.  
  
 Fundamentalmente, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] não transmite uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de um suplemento para um aplicativo host; em vez disso, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] passa o identificador de janela do Win32 para a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usando a interoperabilidade do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Assim, quando uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de um suplemento é transmitida ao aplicativo host, ocorre o seguinte:  
  
-   No lado do suplemento, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] adquire um identificador de janela para a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] que será exibida pelo aplicativo host. O identificador de janela é encapsulado por interno [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classe que deriva de <xref:System.Windows.Interop.HwndSource> e implementa <xref:System.AddIn.Contract.INativeHandleContract>. Uma instância dessa classe é retornada por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> e passa por marshaling do domínio de aplicativo do suplemento ao domínio de aplicativo do aplicativo host.  
  
-   No lado do aplicativo host, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] reempacota o <xref:System.Windows.Interop.HwndSource> como interno [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classe que deriva de <xref:System.Windows.Interop.HwndHost> e consome <xref:System.AddIn.Contract.INativeHandleContract>. Uma instância dessa classe é retornada por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> para o aplicativo host.  
  
 <xref:System.Windows.Interop.HwndHost> existe para exibir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], identificados por identificadores de janela, de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]. Para obter mais informações, consulte [Interoperação Win32 e WPF](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
 Em resumo, <xref:System.AddIn.Contract.INativeHandleContract>, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>, e <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> existem para permitir que o identificador de janela para um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] seja passado de um suplemento para um aplicativo de host, onde é encapsulado por um <xref:System.Windows.Interop.HwndHost> e exibido o host aplicativo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
> [!NOTE]
>  Como o aplicativo host recebe um <xref:System.Windows.Interop.HwndHost>, o aplicativo de host não é possível converter o objeto que é retornado por <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> para o tipo é implementado pelo suplemento (por exemplo, um <xref:System.Windows.Controls.UserControl>).  
  
 Por natureza, <xref:System.Windows.Interop.HwndHost> tem certas limitações que afetam como aplicativos host podem utilizá-los. No entanto, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] estende <xref:System.Windows.Interop.HwndHost> com vários recursos para cenários de suplementos. Essas limitações e benefícios são descritos abaixo.  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>Benefícios de suplementos do WPF  
 Porque [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] suplemento [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] são exibidos a partir de aplicativos host usando uma classe interna que é derivada de <xref:System.Windows.Interop.HwndHost>, aqueles [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] são restritas por recursos do <xref:System.Windows.Interop.HwndHost> com relação ao [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] serviços como o layout, renderização, associação de dados, estilos, modelos e recursos. No entanto, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aumenta interna <xref:System.Windows.Interop.HwndHost> subclasse com recursos adicionais que incluem o seguinte:  
  
-   Navegar com a tecla tab entre a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de um aplicativo host e a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de um suplemento. Observe que o "suplemento é um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" modelo de programação requer que o adaptador do lado do suplemento substituir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> para habilitar tabulações, se o suplemento é totalmente confiável ou parcialmente confiável.  
  
-   Respeitar requisitos de acessibilidade para [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de suplemento que são exibidas em [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] do aplicativo host.  
  
-   Habilitar a execução segura dos aplicativos [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] em vários cenários de domínio do aplicativo.  
  
-   Impedir o acesso a identificadores de janela da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do suplemento quando os suplementos são executados com isolamento de segurança (ou seja, uma área restrita de confiança parcial). Chamando <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> garante essa segurança:  
  
    -   Para o "suplemento retorna um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" modelo de programação, a única maneira de passar o identificador de janela para um suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] entre o isolamento de limite é chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>.  
  
    -   Para o "suplemento é um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]" programação de modelo, substituindo <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> no adaptador do lado do suplemento e chamar <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> (conforme mostrado nos exemplos anteriores) é necessária, como é chamar o adaptador do lado do suplemento `QueryContract` implementação do adaptador do host.  
  
-   Fornecer proteção contra múltiplas execuções de domínio do aplicativo. Devido a limitações com domínios do aplicativo, as exceções sem tratamento que forem lançadas em domínios do aplicativo do suplemento fazem com que todo o aplicativo falhe, mesmo com a existência do limite de isolamento. No entanto, o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e o modelo de suplemento do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oferecem uma forma simples de solucionar esse problema e melhorar a estabilidade do aplicativo. Um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] suplemento que exibe um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] cria um <xref:System.Windows.Threading.Dispatcher> para o thread em que o domínio de aplicativo é executado, se o aplicativo host é um [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplicativo. Você pode detectar sem tratamento todas as exceções que ocorrem no domínio do aplicativo ao manipular o <xref:System.Windows.Threading.Dispatcher.UnhandledException> eventos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] do suplemento <xref:System.Windows.Threading.Dispatcher>. Você pode obter o <xref:System.Windows.Threading.Dispatcher> do <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> propriedade.  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>Limitações de suplementos WPF  
 Além dos benefícios que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] adiciona os comportamentos padrão fornecidos pelo <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost>e identificadores de janela, também há limitações ao suplemento [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] que são exibidos em aplicativos de host:  
  
-   As [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de suplemento exibidas de um aplicativo host não respeitam o comportamento de recorte do aplicativo host.  
  
-   O conceito de *espaço aéreo* em cenários de interoperabilidade também se aplica a suplementos (consulte [Visão geral das regiões de tecnologia](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)).  
  
-   Os serviços de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de um aplicativo host, tais como herança de recursos, associação de dados e comandos, não estão automaticamente disponíveis para [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] de suplemento. Para fornecer esses serviços para o suplemento, você precisa atualizar o pipeline.  
  
-   Uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de suplemento não pode ser girada, dimensionada, distorcida e nem ser afetada de nenhuma outra forma por uma transformação (consulte [Visão geral de transformações](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)).  
  
-   Conteúdo dentro do suplemento [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] que é renderizado por operações de desenho a <xref:System.Drawing> namespace pode incluir combinação alfa. No entanto, tanto uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de suplemento quanto a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplicativo host que o contém devem ser 100% opacas; em outras palavras, a propriedade `Opacity` em ambas deve ser definida como 1.  
  
-   Se o <xref:System.Windows.Window.AllowsTransparency%2A> propriedade de uma janela no aplicativo host que contém um suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é definido como `true`, o suplemento está invisível. Isso será verdadeiro mesmo se a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do suplemento for 100% opaca (ou seja, se a propriedade `Opacity` tiver um valor de 1).  
  
-   Uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de suplemento deve aparecer sobre outros elementos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na mesma janela de nível superior.  
  
-   Nenhuma parte de um suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pode ser renderizado usando um <xref:System.Windows.Media.VisualBrush>. Em vez disso, o suplemento poderá tirar um instantâneo da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gerada para criar um bitmap que poderá ser passado para o aplicativo host usando métodos definidos pelo contrato.  
  
-   Arquivos de mídia não podem ser executados de um <xref:System.Windows.Controls.MediaElement> em um suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
-   Eventos do mouse gerados para a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de suplemento não são recebidos nem gerados pelo aplicativo host e a propriedade `IsMouseOver` da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do aplicativo host tem um valor de `false`.  
  
-   Quando o foco alterna entre os controles em uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de suplemento, os eventos `GotFocus` e `LostFocus` não são recebidos nem acionados pelo aplicativo host.  
  
-   A parte de um aplicativo host que contém uma [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de suplemento aparece em branco quando impressa.  
  
-   Todos os distribuidores (consulte <xref:System.Windows.Threading.Dispatcher>) criado pelo suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] deve ser desligada manualmente antes do suplemento do proprietário é descarregado se o aplicativo host continua a execução. O contrato pode implementar métodos que permitam que o aplicativo host sinalize o suplemento antes que este seja descarregado, permitindo assim que a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do suplemento desligue seus dispatchers.  
  
-   Se um suplemento [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é um <xref:System.Windows.Controls.InkCanvas> ou contém um <xref:System.Windows.Controls.InkCanvas>, não é possível descarregar o suplemento.  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>Otimização do desempenho  
 Por padrão, quando vários domínios do aplicativo são usados, os diversos assemblies do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] exigidos por cada aplicativo são todos carregados nesse domínio do aplicativo. Como resultado, o tempo necessário para criar novos domínios de aplicativo e iniciar aplicativos neles pode afetar o desempenho. No entanto, o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fornece uma maneira de reduzir os tempos de inicialização instruindo os aplicativos a compartilhar assemblies entre domínios do aplicativo se eles já estão carregados. Você pode fazer isso usando o <xref:System.LoaderOptimizationAttribute> atributo, que deve ser aplicado ao método de ponto de entrada (`Main`). Nesse caso, você deve usar apenas código para implementar sua definição de aplicativo (consulte [Visão geral de gerenciamento do aplicativo](../../../../docs/framework/wpf/app-development/application-management-overview.md)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.LoaderOptimizationAttribute>  
 [Suplementos e extensibilidade](../../../../docs/framework/add-ins/index.md)  
 [Domínios do aplicativo](../../../../docs/framework/app-domains/application-domains.md)  
 [Visão geral de comunicação remota do .NET framework](http://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [Fazendo a objetos remotos](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [Tópicos de instruções](../../../../docs/framework/wpf/app-development/how-to-topics.md)
