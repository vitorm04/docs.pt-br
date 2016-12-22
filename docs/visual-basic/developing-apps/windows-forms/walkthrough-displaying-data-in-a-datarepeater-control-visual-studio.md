---
title: "Instru&#231;&#245;es passo a passo: exibindo dados em um controle DataRepeater (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "DataRepeater, passo a passo"
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Este passo a passo fornece um cenário básico do início ao fim para exibir dados associados em uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## Pré\-requisito  
 Este passo a passo requer o banco de dados de exemplo Northwind.  
  
 Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá\-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Para obter instruções, consulte [Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md).  
  
## Visão Geral  
 A primeira parte deste passo a passo consiste em quatro tarefas principais:  
  
-   Criando uma solução.  
  
-   Adicionando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
-   Adicionando uma fonte de dados.  
  
-   Adicionando controles ligados a dados.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## Criando uma solução DataRepeater  
 Na primeira etapa, você pode criar um projeto e solução.  
  
#### Para criar uma solução DataRepeater  
  
1.  No Visual Studio **arquivo** menu, clique em **novo projeto**.  
  
2.  No **tipos de projeto** painel o **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**, e, em seguida, clique em **Windows**.  
  
3.  No **modelos** painel, clique em **Windows Forms Application**.  
  
4.  No **nome** digite `DataRepeaterApp`.  
  
5.  Clique em **OK**.  
  
     O Windows Forms Designer é aberto.  
  
6.  Selecione o formulário no Designer de formulários do Windows. No **propriedades** janela, defina o **tamanho** propriedade `800, 700`.  
  
## Adicionando um controle DataRepeater  
 Nesta etapa, você adiciona um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle ao formulário.  
  
#### Para adicionar um controle DataRepeater  
  
1.  Sobre o **exibição** menu, clique em **Toolbox**.  
  
     O **Toolbox** abre.  
  
2.  Selecione o **Visual Basic PowerPacks** guia.  
  
3.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para **Form1**.  
  
4.  Na janela Propriedades, defina o **local** propriedade `0, 25`.  
  
5.  Definir o **tamanho** propriedade `460, 600`.  
  
## Adicionando uma fonte de dados  
 Nesta etapa, você adiciona uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
#### Para adicionar uma fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources**.  
  
2.  No **fontes de dados** janela, clique em **Add New Data Source**.  
  
3.  Selecione **banco de dados** sobre o **Escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  Sobre o **Choose Your Data Connection** execute uma das seguintes etapas:  
  
    -   Se uma conexão de dados para o banco de dados de exemplo Northwind estiver disponível na lista suspensa, clique nele.  
  
         \- ou \-  
  
    -   Clique em **nova conexão** para configurar uma nova conexão de dados. Para obter mais informações, consulte [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/pt-br/360c340d-e5a6-4a7e-a569-e95d500be43d).  
  
5.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.  
  
    > [!NOTE]
    >  Se uma caixa de diálogo for exibida, clique em **Sim** para salvar o arquivo ao seu projeto.  
  
6.  Clique em **próximo** sobre o **Salvar a cadeia de conexão no arquivo de configuração do aplicativo** página.  
  
7.  Expanda o **tabelas** nó o **Choose Your Database Objects** página.  
  
8.  Marque as caixas de seleção ao lado de **clientes** e **pedidos** tabelas e clique **Concluir**.  
  
     **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e **pedidos** as tabelas aparecem no **fontes de dados** janela.  
  
## Adicionar controles ligados a dados  
 Nesta etapa, você adiciona controles ligados a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### Para adicionar controles ligados a dados  
  
1.  No **fontes de dados** janela, selecione o nó de nível superior para o **clientes** tabela.  
  
2.  Altere o tipo subjacente da tabela para **detalhes** clicando **detalhes** na lista suspensa no nó da tabela.  
  
3.  Selecione o **clientes** nó da tabela e arraste\-o para a região de modelo de item \(região superior\) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Um <xref:System.Windows.Forms.BindingNavigator> controle é adicionado ao formulário e o **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, e **CustomersBindingNavigator** componentes são adicionados à bandeja de componentes.  
  
4.  Selecione todos os campos e seus rótulos associados e posicioná\-las próximo à borda esquerda da região de modelo de item.  
  
5.  Selecione os últimos cinco campos \(**região**, **CEP**, **País**, **Phone**, e **Fax**\) e seus rótulos associados e movê\-los até e à direita dos seis primeiros campos.  
  
6.  Selecione o modelo de item \(região superior do controle\).  
  
7.  Na janela Propriedades, defina o **tamanho** propriedade `427, 170`.  
  
 Neste ponto, você tem um aplicativo funcional que exibirá uma lista de repetição de clientes. Você pode pressionar F5 para executar o aplicativo, alterar os dados e adicionar ou excluir registros de cliente.  
  
 As próximas etapas opcionais, você aprenderá a personalizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## Próximas etapas \(opcionais\)  
 Nesta parte do passo a passo consiste em quatro tarefas opcionais:  
  
-   Alterando a aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
-   Impedindo que os usuários adicionem ou excluam registros.  
  
-   Adicionando recursos de pesquisa para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
-   Adicionando uma tabela mestre e de detalhes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## Alterando a aparência do controle DataRepeater  
 Esta etapa opcional, você altera o `BackColor` do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de design. Você também adicionar código para exibir linhas em cores alternadas e alterar um rótulo `ForeColor` condicionalmente.  
  
#### Para alterar a aparência do controle  
  
1.  No Windows Forms Designer, selecione a região principal \(inferior\) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Propriedades, defina o `BackColor` propriedade em branco.  
  
3.  Clique duas vezes o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> para abrir o Editor de código.  
  
4.  No Editor de código, lista suspensa de eventos, clique em **DrawItem**.  
  
5.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o código a seguir para alternar o `BackColor`:  
  
     [!CODE [VbPowerPacksDataRepeaterWalkthrough#1](../CodeSnippet/VS_Snippets_VBCSharp/VbPowerPacksDataRepeaterWalkthrough#1)]  
  
6.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o seguinte código para alterar o `ForeColor` de um rótulo, dependendo de uma condição:  
  
     [!CODE [VbPowerPacksDataRepeaterWalkthrough#2](../CodeSnippet/VS_Snippets_VBCSharp/VbPowerPacksDataRepeaterWalkthrough#2)]  
  
7.  Pressione F5 para executar o aplicativo e ver as personalizações.  
  
## Impedindo que os usuários adicionem ou excluam registros  
 Esta etapa opcional, você adiciona código que impede que os usuários adicionem ou excluam registros de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
#### Para impedir que usuários adicionando e excluindo registros  
  
1.  No Windows Forms Designer, clique duas vezes no formulário para abrir o Editor de códigos.  
  
2.  Adicione o seguinte código para o `Form_Load` evento:  
  
     [!CODE [VbPowerPacksDataRepeaterWalkthrough#3](../CodeSnippet/VS_Snippets_VBCSharp/VbPowerPacksDataRepeaterWalkthrough#3)]  
  
3.  Na lista suspensa Nome da classe, clique em **BindingNavigatorDeleteItem**. Na lista suspensa Nome do método, clique em **EnabledChanged**.  
  
4.  Adicione o seguinte código para o `BindingNavigatorDeleteItem_EnabledChanged` manipulador de eventos:  
  
     [!CODE [VbPowerPacksDataRepeaterWalkthrough#4](../CodeSnippet/VS_Snippets_VBCSharp/VbPowerPacksDataRepeaterWalkthrough#4)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> permitirá que o **DeleteItem** botão toda vez que o registro atual é alterado.  
  
5.  Pressione F5 para executar o aplicativo. Observe que o **DeleteItem** botão está desabilitado e você não pode excluir itens, pressionando a tecla DELETE.  
  
## Adicionando funcionalidade de pesquisa ao controle DataRepeater  
 Nesta etapa opcional, você implementa a capacidade de pesquisar um valor na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Se a cadeia de caracteres for encontrada, o controle seleciona o item que contém o valor e o item é movido para a exibição.  
  
#### Para adicionar o recurso de pesquisa  
  
1.  Arraste um <xref:System.Windows.Forms.TextBox> de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Posicione\-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.  
  
3.  Arraste um <xref:System.Windows.Forms.Button> de controle do **Toolbox** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Posicione\-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
4.  Na janela Propriedades, altere o **nome** propriedade **SearchButton**. Alteração de **texto** propriedade **pesquisa**.  
  
5.  Clique duas vezes o <xref:System.Windows.Forms.Button> de controle para abrir o Editor de códigos e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.  
  
     [!CODE [VbPowerPacksDataRepeaterWalkthrough#5](../CodeSnippet/VS_Snippets_VBCSharp/VbPowerPacksDataRepeaterWalkthrough#5)]  
  
6.  Pressione F5 para executar o aplicativo. Digite uma ID de cliente em **SearchTextBox** e clique no **pesquisa** botão.  
  
## Adicionando um mestre e a tabela de detalhes para DataRepeater  
 Nesta etapa opcional, você adicionar um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para exibir os pedidos relacionados para cada cliente.  
  
#### Para adicionar uma tabela mestre e de detalhes  
  
1.  Arraste uma segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle de **Visual Basic PowerPacks** guia o **ferramentas** para o formulário.  
  
2.  Na janela Propriedades, defina o **local** propriedade `465, 25`.  
  
3.  Definir o **tamanho** propriedade `315, 600`.  
  
4.  No **fontes de dados** janela, expanda o **clientes** nó e selecione o nó de detalhe para o **pedidos** tabela.  
  
5.  Altere o tipo subjacente desse **pedidos** tabela detalhes clicando em **detalhes** na lista suspensa no nó da tabela.  
  
6.  Arraste esta **pedidos** nó de tabela para a região de modelo de item \(região superior\) do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Um **OrdersBindingSource** componente e um **OrdersTableAdapter** componentes são adicionados à bandeja de componentes.  
  
7.  Pressione F5 para executar o aplicativo. Quando você seleciona cada cliente na primeira <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar os pedidos para aquele cliente são exibidos na segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## Consulte também  
 [Introdução ao controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [Como exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [Como alterar o layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Como exibir cabeçalhos de item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [Como pesquisar dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [Como criar um formulário mestre\/detalhado usando dois controles DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Como desabilitar a adição e a exclusão de itens DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [Solucionando problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)