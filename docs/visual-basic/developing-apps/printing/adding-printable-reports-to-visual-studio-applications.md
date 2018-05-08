---
title: Adicionando relatórios imprimíveis a aplicativos do Visual Studio
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 4a7275a665e0c3290c2b3cd55c1af0c7cf0504f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Adicionando relatórios imprimíveis a aplicativos do Visual Studio
O Visual Studio oferece suporte a uma variedade de soluções de relatório para ajudá-lo a adicionar dados ricos reportando para seus aplicativos Visual Basic. Você pode criar e adicionar relatórios usando controles ReportViewer, Crystal Reports ou SQL Server Reporting Services.  
  
> [!NOTE]
>  SQL Server Reporting Services é parte do SQL Server 2005 em vez do Visual Studio. O Reporting Services não é instalado em seu sistema, a menos que você instalou o SQL Server 2005.  
  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Visão geral do Microsoft Reporting tecnologia em aplicativos do Visual Basic  
 Escolha dentre as seguintes abordagens para usar uma tecnologia Microsoft de relatórios em seu aplicativo:  
  
-   Adicione uma ou mais instâncias de um controle ReportViewer a um aplicativo do Windows do Visual Basic.  
  
-   Integre o SQL Server Reporting Services programaticamente por meio de chamadas para o serviço Web do servidor de relatório.  
  
-   Use o controle ReportViewer e Microsoft SQL Server 2005 Reporting Services em conjunto, usando o controle como um visualizador de relatórios e um servidor de relatório como um processador de relatório. (Observe que você deve usar a versão do SQL Server 2005 do Reporting Services se você quiser usar um servidor de relatório e o controle ReportViewer juntos).  
  
## <a name="using-reportviewer-controls"></a>Usando controles ReportViewer  
 A maneira mais fácil para inserir a funcionalidade de relatório em um aplicativo do Windows do Visual Basic é adicionar o controle ReportViewer a um formulário em seu aplicativo. O controle adiciona recursos diretamente para seu aplicativo de processamento de relatório e fornece um designer de relatórios integrado para que você possa criar relatórios usando dados de qualquer objeto de dados do ADO.NET. Uma API completa fornece acesso programático ao controle e relatórios para que você pode configurar a funcionalidade de tempo de execução.  
  
 ReportViewer fornece processamento de relatório interno e o recurso de exibição em um controle de dados único, distribuído gratuitamente. Escolha que os controles ReportViewer se você precisar que a funcionalidade de relatório a seguir:  
  
-   Processamento de relatório no aplicativo cliente. Um relatório processado aparece na área de visualização fornecida pelo controle.  
  
-   Associação de dados para tabelas de dados ADO.NET. Você pode criar relatórios que consomem <xref:System.Data.DataTable> instâncias fornecidas para o controle. Você também pode associar diretamente a objetos de negócios.  
  
-   Controles redistribuíveis que você pode incluir em seu aplicativo.  
  
-   Funcionalidade de tempo de execução como navegação de página, impressão, pesquisa e formatos de exportação. Uma barra de ferramentas ReportViewer fornece suporte para essas operações.  
  
 Para usar o controle ReportViewer, arraste-a do **dados** seção de ferramentas do Visual Studio para um formulário em seu aplicativo do Windows do Visual Basic.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>Criando relatórios no Visual Studio para controles do ReportViewer  
 Para criar um relatório que é executado em ReportViewer, adicione um **relatório** modelo ao seu projeto. Visual Studio cria um arquivo de definição de relatório do cliente (. rdlc), adiciona o arquivo ao seu projeto e abre um designer de relatórios integrado no espaço de trabalho do Visual Studio.  
  
 O Designer de relatórios do Visual Studio integra-se com o **fontes de dados** janela. Quando você arrasta um campo a partir de **fontes de dados** janela para o relatório, o Designer de relatórios copia os metadados sobre a fonte de dados para o arquivo de definição de relatório. Esses metadados são usados pelo controle ReportViewer para gerar automaticamente o código de associação de dados.  
  
 O Designer de relatórios do Visual Studio não inclui a funcionalidade de visualização de relatório. Para visualizar o relatório, execute o aplicativo e visualize o relatório inserido nele.  
  
|Para adicionar funcionalidade básica de relatório ao seu aplicativo|  
|---|    
|1.  Arraste um controle ReportViewer do **dados** guia do **caixa de ferramentas** para seu formulário.<br />2.  No menu **Projeto**, escolha **Adicionar Novo Item**. No **Adicionar Novo Item** caixa de diálogo, selecione o **relatório** ícone e clique em **adicionar**.<br />     O Designer de relatórios é aberto no ambiente de desenvolvimento, e um arquivo de relatório (. rdlc) é adicionado ao projeto.<br />3.  Arraste itens de relatório o **caixa de ferramentas** no layout do relatório e organize-os como desejar.<br />4.  Arraste campos do **fontes de dados** janela para os itens de relatório no layout do relatório.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Usando o Reporting Services em aplicativos do Visual Basic  
 O Reporting Services é uma tecnologia de relatórios baseada em servidor que está incluída com o SQL Server. O Reporting Services inclui recursos adicionais que não são encontrados nos controles do ReportViewer. Escolha o Reporting Services se você precisar de qualquer um dos seguintes recursos:  
  
-   Implantação de expansão e processamento de relatório do lado do servidor que fornece desempenho melhorado para relatórios complexos ou demoradas e atividade de alto volume de relatório.  
  
-   Dados integrados e processamento do relatório, com suporte para controles de relatório personalizado e ricas em formatos de saída de renderização.  
  
-   Agendamento de processamento de relatório para que você pode especificar exatamente quando os relatórios são executados.  
  
-   Distribuição de relatório baseada em assinantes por email ou para locais de compartilhamento de arquivo.  
  
-   Relatórios ad hoc para que usuários empresariais podem criar relatórios, conforme necessário.  
  
-   Assinaturas controladas por dados que roteiam a saída do relatório personalizado para uma lista dinâmica de destinatários.  
  
-   Extensões personalizadas para processamento de dados, entrega de relatórios, autenticação personalizada e renderização de relatório.  
  
 O servidor de relatório é implementado como serviço Web. O código do aplicativo deve incluir chamadas para o serviço da Web para acessar relatórios e outros metadados. O serviço Web fornece acesso programático completo a uma instância de servidor de relatório.  
  
 Como o Reporting Services é uma tecnologia de relatórios baseados na Web, o visualizador padrão mostra relatórios que são renderizados em formato HTML. Se você não quiser usar HTML como o formato de apresentação de relatório padrão, você precisará escrever um visualizador de relatório personalizado para seu aplicativo.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Criando relatórios no Visual Studio para o Reporting Services  
 Para criar relatórios que são executados em um servidor de relatório, criar definição de relatório (. RDL) de arquivos no Visual Studio por meio do Business Intelligence Development Studio, que está incluído no SQL Server 2005.  
  
> [!NOTE]
>  Você deve ter o SQL Server 2005 instalado para poder usar o SQL Server Reporting Services e o Business Intelligence Development Studio.  
  
 O Business Intelligence Development Studio adiciona modelos de projeto que são específicos para componentes do SQL Server. Para criar relatórios, você pode escolher entre o **Report Server Project** ou **Report Server Project Wizard** modelos. Você pode especificar conexões de fonte de dados e consultas a uma variedade de tipos de fonte de dados, incluindo o SQL Server, Oracle, Analysis Services, XML e SQL Server Integration Services. Um **dados** guia **Layout** guia e **visualização** guia permitem que você defina os dados, criar um layout de relatório e visualize o relatório todos no mesmo espaço de trabalho.  
  
 Definições de relatório que você criou para o controle ou o servidor de relatório podem ser reutilizadas em qualquer tecnologia.  
  
|Para criar um relatório que é executado em um servidor de relatório|  
|---|    
|1.  Sobre o **arquivo** menu, escolha **novo**.<br />     A caixa de diálogo **Novo Projeto** é aberta.<br />2.  No **tipos de projeto** painel, clique em **projetos de Business Intelligence**.<br />3.  No painel de modelos, selecione **Report Server Project** ou **Report Server Project Wizard**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>Usando controles ReportViewer e SQL Server Reporting Services em conjunto  
 O SQL Server 2005 Reporting Services e controles ReportViewer podem ser usados juntos no mesmo aplicativo.  
  
-   O controle ReportViewer fornece um visualizador que é usado para exibir relatórios em seu aplicativo.  
  
-   O Reporting Services fornece os relatórios e executa todo o processamento em um servidor remoto.  
  
 O controle ReportViewer pode ser configurado para mostrar os relatórios que são armazenados e processados em um servidor de relatório do Reporting Services remoto. Esse tipo de configuração é chamado *modo de processamento remoto*. No modo de processamento remoto, o controle solicita um relatório que é armazenado em um servidor de relatório remoto. O servidor de relatório executa todos os processamento de relatório, processamento de dados e renderização de relatório. Um relatório concluído, processado é retornado para o controle e exibido na área de exibição.  
  
 Relatórios que executam um adicional de suporte do servidor de relatório de formatos de exportação, ter uma implementação de parametrização de relatório diferente, use os tipos de fonte de dados que têm suporte pelo servidor de relatório e são acessados por meio do modelo de autorização baseada em função do servidor de relatório.  
  
 Para usar o modo de processamento remoto, especifique a URL e o caminho para um relatório do servidor ao configurar o controle ReportViewer.
