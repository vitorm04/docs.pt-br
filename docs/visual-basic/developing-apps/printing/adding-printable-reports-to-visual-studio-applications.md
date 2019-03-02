---
title: Adicionando relatórios imprimíveis a aplicativos do Visual Studio
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 65264deea3aeff1a633ea6888b3f175031b7fba5
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212008"
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>Adicionando relatórios imprimíveis a aplicativos do Visual Studio
Visual Studio dá suporte a uma variedade de soluções de relatórios para ajudá-lo a adicionar relatórios aos seus aplicativos Visual Basic de dados avançados. Você pode criar e adicionar relatórios usando controles ReportViewer, Crystal Reports ou SQL Server Reporting Services.  

  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Visão geral dos relatórios de tecnologia em aplicativos Visual Basic da Microsoft  
 Escolha dentre as seguintes abordagens para usar uma tecnologia em seu aplicativo de relatórios da Microsoft:  
  
-   Adicione uma ou mais instâncias de um controle ReportViewer a um aplicativo do Windows do Visual Basic.  
  
-   Integre o SQL Server Reporting Services por meio de programação por meio de chamadas para o serviço Web servidor de relatório.  
  
-   Use o controle ReportViewer e o Microsoft SQL Server 2005 Reporting Services em conjunto, usando o controle como um visualizador de relatórios e um servidor de relatório como um processador de relatório. (Observe que você deve usar a versão do SQL Server 2005 do Reporting Services se você quiser usar um servidor de relatório e o controle ReportViewer juntos).  
  
## <a name="using-reportviewer-controls"></a>Usando os controles ReportViewer  
 A maneira mais fácil de incorporar funcionalidade de relatório em um aplicativo do Windows do Visual Basic é adicionar o controle ReportViewer a um formulário em seu aplicativo. O controle adiciona recursos diretamente para seu aplicativo de processamento de relatório e fornece um designer de relatórios integrado para que você possa criar relatórios usando dados de qualquer objeto de dados do ADO.NET. Uma API completa fornece acesso programático ao controle e relatórios para que você pode configurar a funcionalidade de tempo de execução.  
  
 ReportViewer fornece processamento de relatório interno e o recurso de exibição em um controle de dados único, distribuído gratuitamente. Escolha que os controles ReportViewer se você precisar da funcionalidade de relatório a seguir:  
  
-   Processamento de relatório no aplicativo cliente. Um relatório processado aparece na área de visualização fornecida pelo controle.  
  
-   Associação de dados para tabelas de dados ADO.NET. Você pode criar relatórios que consomem <xref:System.Data.DataTable> instâncias fornecidas ao controle. Você também pode associar diretamente a objetos comerciais.  
  
-   Controles redistribuíveis que você pode incluir em seu aplicativo.  
  
-   Funcionalidade de tempo de execução, como a navegação de página, impressão, pesquisa e formatos de exportação. Uma barra de ferramentas ReportViewer fornece suporte para essas operações.  
  
 Para usar o controle ReportViewer, você poderá arrastá-lo partir o **dados** seção de ferramentas do Visual Studio para um formulário em seu aplicativo do Windows do Visual Basic.  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>Criando relatórios no Visual Studio para controles do ReportViewer  
 Para criar um relatório que é executado em ReportViewer, adicione uma **relatório** modelo ao seu projeto. Visual Studio cria um arquivo de definição de relatório do cliente (. rdlc), adiciona o arquivo ao seu projeto e abre um designer de relatórios integrado no espaço de trabalho do Visual Studio.  
  
 O Report Designer do Visual Studio integra-se com o **fontes de dados** janela. Quando você arrasta um campo a partir de **fontes de dados** janela para o relatório, o Designer de relatórios copia os metadados sobre a fonte de dados para o arquivo de definição de relatório. Esses metadados são usados pelo controle ReportViewer para gerar automaticamente o código de associação de dados.  
  
 O Report Designer do Visual Studio não inclui a funcionalidade de visualização de relatório. Para visualizar o relatório, execute o aplicativo e visualize o relatório inserido nele.  
  
|Para adicionar a funcionalidade básica de relatório ao seu aplicativo|  
|---|    
|1.  Arraste um controle ReportViewer dos **dados** guia da **caixa de ferramentas** para seu formulário.<br />2.  No menu **Projeto**, escolha **Adicionar Novo Item**. No **Adicionar Novo Item** caixa de diálogo, selecione o **relatório** ícone e clique em **adicionar**.<br />     O Designer de relatórios é aberto no ambiente de desenvolvimento e um arquivo de relatório (. rdlc) é adicionado ao projeto.<br />3.  Arraste itens do relatório do **caixa de ferramentas** no layout do relatório e organize-os como desejar.<br />4.  Arraste os campos da **fontes de dados** janela para os itens de relatório no layout do relatório.|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>Usando o Reporting Services em aplicativos Visual Basic  
 O Reporting Services é uma tecnologia de relatórios baseada em servidor que está incluída com o SQL Server. O Reporting Services inclui recursos adicionais que não são encontrados nos controles do ReportViewer. Escolha o Reporting Services se você precisar de qualquer um dos seguintes recursos:  
  
-   Implantação de expansão e processamento de relatório do lado do servidor que fornece desempenho aprimorado para relatórios complexos ou de execução longa e atividade de alto volume de relatório.  
  
-   Dados integrados e processamento de relatório, com suporte para controles de relatório personalizado e avançados de renderização de formatos de saída.  
  
-   Agendado para que você possa especificar exatamente quando os relatórios são executados de processamento de relatório.  
  
-   Distribuição de relatório com base no assinante por meio de email ou para locais de compartilhamento de arquivo.  
  
-   Relatórios ad hoc para que os usuários empresariais podem criar relatórios conforme necessário.  
  
-   Assinaturas controladas por dados que roteiam a saída do relatório personalizado para uma lista dinâmica de destinatários.  
  
-   Extensões personalizadas para processamento de dados, entrega de relatório, autenticação personalizada e renderização de relatório.  
  
 O servidor de relatório é implementado como um serviço Web. O código do aplicativo deve incluir chamadas para o serviço Web para acessar relatórios e outros metadados. O serviço Web fornece acesso programático completo a uma instância de servidor de relatório.  
  
 Porque o Reporting Services é uma tecnologia de relatórios baseado na Web, o visualizador padrão mostra relatórios que são renderizados em formato HTML. Se você não quiser usar o HTML como o formato de apresentação de relatório padrão, você precisará escrever um visualizador de relatório personalizado para seu aplicativo.  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>Criando relatórios no Visual Studio para o Reporting Services  
 Para criar relatórios que são executados em um servidor de relatório, criar definição de relatório (. RDL) de arquivos no Visual Studio por meio do Business Intelligence Development Studio, que é incluído com o SQL Server 2005.  
  
 O Business Intelligence Development Studio adiciona modelos de projeto que são específicos para componentes do SQL Server. Para criar relatórios, você pode escolher dentre os **Report Server Project** ou **Assistente de projeto do servidor de relatório** modelos. Você pode especificar conexões de fonte de dados e consultas a uma variedade de tipos de fonte de dados, incluindo o SQL Server, Oracle, Analysis Services, XML e SQL Server Integration Services. Um **dados** guia **Layout** guia, e **visualização** guia permitem que você defina os dados, criar um layout de relatório e visualizar o relatório todos no mesmo espaço de trabalho.  
  
 As definições de relatório que você cria para o controle ou o servidor de relatório podem ser reutilizadas em qualquer tecnologia.  
  
|Para criar um relatório que é executado em um servidor de relatório|  
|---|    
|1.  Sobre o **arquivo** menu, escolha **New**.<br />     A caixa de diálogo **Novo Projeto** é aberta.<br />2.  No **tipos de projeto** painel, clique em **projetos do Business Intelligence**.<br />3.  No painel modelos, selecione **Report Server Project** ou **Assistente de projeto do servidor de relatório**.|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>Usando os controles ReportViewer e o SQL Server Reporting Services em conjunto  
 Os controles ReportViewer e o SQL Server 2005 Reporting Services podem ser usados juntos no mesmo aplicativo.  
  
-   O controle ReportViewer fornece um visualizador que é usado para exibir relatórios em seu aplicativo.  
  
-   O Reporting Services fornece os relatórios e executa todo o processamento em um servidor remoto.  
  
 O controle ReportViewer pode ser configurado para mostrar os relatórios que são armazenados e processados em um servidor de relatório do Reporting Services remoto. Esse tipo de configuração é chamado *modo de processamento remoto*. No modo de processamento remoto, o controle solicita um relatório que é armazenado em um servidor de relatório remoto. O servidor de relatório executa todos os processamento de relatório, processamento de dados e processamento de relatório. Um relatório concluído, processado é retornado para o controle e exibido na área de exibição.  
  
 Relatórios executados sob um adicional de suporte do servidor de relatório, formatos de exportação têm uma implementação de parametrização de relatório diferente, use os tipos de fonte de dados que são compatíveis com o servidor de relatório e são acessados por meio do modelo de autorização baseada em função no servidor de relatório.  
  
 Para usar o modo de processamento remoto, especifique a URL e o caminho para um servidor de relatório ao configurar o controle ReportViewer.
