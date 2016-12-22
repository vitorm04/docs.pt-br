---
title: "Adicionando relat&#243;rios imprim&#237;veis a aplicativos do Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "imprimindo [Visual Studio], relatórios"
  - "relatórios, imprimindo em [Visual Studio]"
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Adicionando relat&#243;rios imprim&#237;veis a aplicativos do Visual Studio
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Studio oferece suporte a uma variedade de soluções de relatório para ajudar você a adicionar dados ricos para seus aplicativos Visual Basic.  Você pode criar e adicionar relatórios usando os controles ReportViewer, Crystal Reports ou os Serviços de relatório do SQL Server.  
  
> [!NOTE]
>  Os Serviços de relatório do SQL Server são parte do SQL Server 2005 e não do Visual Studio.  O Reporting Services não é instalado no seu sistema a menos que você tenha instalado o SQL Server 2005.  
  
## Visão geral da tecnologia do Microsoft Reporting em aplicativos do Visual Basic  
 Escolha as seguintes abordagens para usar uma tecnologia Microsoft de relatórios no seu aplicativo:  
  
-   Adicionar uma ou mais instâncias de um controle ReportViewer a um aplicativo Visual Basic para Windows.  
  
-   Integre Serviços de relatório do SQL Server programaticamente fazendo chamadas para o serviço de Web do Report Server.  
  
-   Use o controle ReportViewer e Microsoft SQL Server 2005 Reporting Services juntos, usando o controle como um visualizador de relatório e um servidor de relatório como um processador de relatório.  \(Observe que você deve usar a versão SQL Server 2005 do Reporting Services se você desejar usar um servidor de relatório e o controle ReportViewer juntos\).  
  
## Usando controles ReportViewer  
 A maneira mais fácil de incorporar a funcionalidade de relatório em um aplicativo do Windows do Visual Basic é adicionar o controle ReportViewer a um formulário em seu aplicativo.  O controle adiciona recursos de processamento de relatórios diretamente para seu aplicativo e fornece um designer de relatório integrados para que você pode criar relatórios usando dados de qualquer objeto de dados do ADO.NET.  Uma API completa fornece acesso programático ao controle e relatórios para que você possa configurar a funcionalidade em tempo de execução.  
  
 ReportViewer fornece o recurso interno de processamento e exibição de relatório em um controle de dados único,  distribuído gratuitamente.  Escolha os controles ReportViewer se você precisar da funcionalidade de relatório a seguir:  
  
-   Processamento de Relatório no aplicativo cliente.  Um relatório processado aparece na área de visualização fornecida pelo controle.  
  
-   Ligação de dados para tabelas de dados ADO.NET.  Você pode criar relatórios que consomem instâncias <xref:System.Data.DataTable> fornecidas para o controle.  Você também pode vincular diretamente a objetos de negócios.  
  
-   Controles redistribuíveis que você pode incluir em seu aplicativo.  
  
-   Funcionalidade de tempo de execução como navegação de página, impressão, pesquisar e formatos de exportação.  Uma barra de ferramentas ReportViewer fornece suporte para essas operações.  
  
 Para usar o controle ReportViewer, você pode arrastá\-la a partir da seção **Data** da Caixa de ferramentas do Visual Studio  para um formulário em seu aplicativos do Windows Visual Basic.  
  
### Criando relatórios em Visual Studio para controles do ReportViewer  
 Para criar um relatório que é executado em ReportViewer, adicione um modelo **Report** ao seu projeto.  Visual Studio cria um arquivo de definição de relatório do cliente \(.rdlc\), adiciona o arquivo ao seu projeto e abre um designer de relatório  integrado na área de trabalho do Visual Studio.  
  
 O Report Designer do Visual Studio integra\-se com a janela **Data Sources**.  Quando você arrasta um campo da janela **Data Sources** para o relatório, o Report Designer copia metadados sobre a fonte de dados para o arquivo de definição de relatório.  Esses metadados é usado pelo controle de ReportViewer para gerar código de vinculação de dados automaticamente.  
  
 O Report Designer do Visual Studio não inclui a funcionalidade de visualização de relatório.  Para visualizar o relatório, execute o aplicativo e visualize o relatório incorporado nela.  
  
||  
|-|  
|Para adicionar funcionalidade básica de relatório ao seu aplicativo|  
|1.  Arraste um controle de ReportViewer da guia **Data** do **ToolBox** para seu formulário.<br />2.  No menu **Project**, escolha **Add New Item**.  Na caixa de diálogo **Add New Item**, selecione o ícone **Report** e clique em **Add**.<br />     O Report Designer abre no ambiente de desenvolvimento, e um arquivo de relatório \(.rdlc\) é adicionado ao projeto.<br />3.  Arraste itens do relatório a partir de **ToolBox** no layout do relatório e organize\-os como você deseja.<br />4.  Arraste campos da janela  **fontes de dados**  para os itens de relatório no layout do relatório.|  
  
## Usando o Reporting Services em aplicativos do Visual Basic  
 O Reporting Services é uma tecnologia de relatório com base no servidor que está incluída no SQL Server.  O Reporting Services inclui recursos adicionais que não são encontrados nos controles ReportViewer.  Escolha o Reporting Services se você precisar de qualquer um dos seguintes recursos:  
  
-   Escalar implantação e processamento  de relatório do lado do servidor que fornecem melhor desempenho para relatórios complexos ou de execução demorada e para relatório de alto volume de atividade.  
  
-   Formatos integrados e processamento de relatório, com suporte para controles de relatório personalizadas e processamento de formatos ricos de saída.  
  
-   Processamentos de relatório agendados para que você possa especificar exatamente quando os relatórios são executados.  
  
-   Distribuição de  relatório baseada em assinantes por email ou para compartilhamento de arquivo locais.  
  
-   Relatórios ad hoc para que usuários comerciais possam criar relatórios, conforme necessário.  
  
-   Inscrições orientado a dados que roteiam relatório personalizados de saída para uma lista dinâmica de destinatários.  
  
-   Extensões personalizadas para processamento de dados, entrega de relatórios, autenticação personalizada e processamento de relatório.  
  
 O servidor de relatório é implementado como serviço Web.  O código do seu aplicativo deve incluir chamadas para o serviço Web para acessar relatórios e outros metadados.  O serviço Web fornece acesso através de programação completo a uma instância de servidor de relatório.  
  
 Como serviços de relatórios são uma tecnologia de relatórios baseados na Web, o visualizador padrão mostra relatórios que são processados no formato MTML.  Se você não desejar usar MTML como o formato de apresentação padrão de relatório, você precisará escrever um visualizador de relatórios personalizados para seu aplicativo.  
  
### Criando relatórios em Visual Studio para o Reporting Services  
 Para criar relatórios que executam em um servidor de relatório, você cria arquivos de definição de relatório \(.rdl\) no Visual Studio por meio do Business Intelligence Development Studio, que está incluído no SQL Server 2005.  
  
> [!NOTE]
>  Você deve ter o SQL Server 2005 instalado para usar os serviços de relatórios do SQL Server e o Business Intelligence Development Studio.  
  
 O Business Intelligence Development Studio adiciona modelos de projeto que são específicos para componentes SQL Server.  Para criar relatórios, você pode escolher o modelos **Report Server Project** ou **Report Server Project Wizard**.  Você pode especificar conexões de fonte de dados e consultas a uma variedade de tipos fonte de dados, incluindo SQL Server, Oracle, o Analysis Services, XML e SQL Server o Integration Services.  Uma guia **Data**, uma guia **Layout** e uma guia **Preview** permitem que você defina os dados, crie um layout de relatório e visualize o relatório todos no mesmo espaço de trabalho.  
  
 Definições de relatório que você criou para o controle ou o servidor de relatório podem ser reutilizados em qualquer tecnologia.  
  
||  
|-|  
|Para criar um relatório que é executado em um servidor de relatório|  
|1.  No menu **File**, escolha  **New**.<br />     A Caixa de diálogo **New Project** é aberta.<br />2.  No painel **Project types**, clique em **Business Intelligence Projects**.<br />3.  No painel de Modelos, selecione **Report Server Project** ou  **Report Server Project Wizard** .|  
  
## Usando controles ReportViewer e Serviços de relatório do SQL Server juntos  
 Os controles ReportViewer e SQL Server 2005 do Reporting Services podem ser usados juntos no mesmo aplicativo.  
  
-   O controle ReportViewer fornece um visualizador que é usado para exibir relatórios no seu aplicativo.  
  
-   O Reporting Services fornece os relatórios e executa todo o processamento em um servidor remoto.  
  
 O controle ReportViewer pode ser configurado para mostrar os relatórios que são armazenados e processados em um servidor de relatório de Reporting Services remoto.  Esse tipo de configuração é chamado *remote processing mode*.  No modo de processamento remoto, o controle solicita um relatório que é armazenado em um servidor de relatório remoto.  O servidor de relatório executa todo o processamento dos relatórios, processamento de dados, e renderização de relatório.  Um relatório concluído, processado é retornado para o controle e exibido na área de exibição.  
  
 Relatórios executados em um servidor de relatório oferecer suporte aos formatos de exportação adicional, têm uma implementação de parametrização de um relatório diferente, usam os tipos que recebem suporte pelo servidor de relatório e são acessados através do modelo de autorização baseado em regras do modelo do servidor.  
  
 Para usar modo de processamento remoto, especifique a URL e o caminho para um relatório do servidor ao configurar o controle ReportViewer.