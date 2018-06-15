---
title: 'Instruções passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231497"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>Instruções passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)
Este passo a passo fornece um cenário básico do início ao fim para exibir dados associados em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## <a name="prerequisite"></a>Pré-requisito  
 Este passo a passo requer o banco de dados de exemplo Northwind.  
  
 Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center. Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="overview"></a>Visão geral  
 A primeira parte deste passo a passo consiste em quatro tarefas principais:  
  
-   Criando uma solução.  
  
-   Adicionando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
-   Adicionando uma fonte de dados.  
  
-   Adicionando controles associados a dados.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>Criando uma solução DataRepeater  
 Na primeira etapa, você pode criar um projeto e solução.  
  
#### <a name="to-create-a-datarepeater-solution"></a>Para criar uma solução DataRepeater  
  
1.  No Visual Studio **arquivo** menu, clique em **novo projeto**.  
  
2.  No **tipos de projeto** painel o **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**e, em seguida, clique em **Windows**.  
  
3.  No **modelos** painel, clique em **aplicativo do Windows Forms**.  
  
4.  Na caixa **Nome**, digite `DataRepeaterApp`.  
  
5.  Clique em **OK**.  
  
     O Designer de Formulários do Windows é aberto.  
  
6.  Selecione o formulário no Designer de formulários do Windows. No **propriedades** janela, defina o **tamanho** propriedade `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>Adicionando um controle DataRepeater  
 Nesta etapa, você adiciona um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle no formulário.  
  
#### <a name="to-add-a-datarepeater-control"></a>Para adicionar um controle DataRepeater  
  
1.  Sobre o **exibição** menu, clique em **caixa de ferramentas**.  
  
     O **caixa de ferramentas** é aberto.  
  
2.  Selecione o **Visual Basic PowerPacks** guia.  
  
3.  Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para **Form1**.  
  
4.  Na janela Propriedades, defina o **local** propriedade `0, 25`.  
  
5.  Definir o **tamanho** propriedade `460, 600`.  
  
## <a name="adding-a-data-source"></a>Adicionando uma fonte de dados  
 Nesta etapa, você adiciona uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
#### <a name="to-add-a-data-source"></a>Para adicionar uma fonte de dados  
  
1.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.  
  
2.  No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.  
  
3.  Selecione **banco de dados** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.  
  
4.  Sobre o **escolha sua Conexão de dados** página, execute uma das seguintes etapas:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, clique nela.  
  
         -ou-  
  
    -   Clique em **nova Conexão** para configurar uma nova conexão de dados. Para obter mais informações, consulte [adicionar novas conexões](/visualstudio/data-tools/add-new-connections).  
  
5.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.  
  
    > [!NOTE]
    >  Se uma caixa de diálogo for exibida, clique em **Sim** para salvar o arquivo ao seu projeto.  
  
6.  Clique em **próximo** no **Salvar cadeia de caracteres de Conexão para o arquivo de configuração de aplicativo** página.  
  
7.  Expanda o **tabelas** nó sob o **escolher seus objetos de banco de dados** página.  
  
8.  Marque as caixas de seleção ao lado de **clientes** e **pedidos** tabelas e depois clique em **concluir**.  
  
     **NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e **pedidos** as tabelas aparecem no **fontes de dados** janela.  
  
## <a name="adding-data-bound-controls"></a>Adicionando controles associados a dados  
 Nesta etapa, você adicionar controles associados a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### <a name="to-add-data-bound-controls"></a>Para adicionar controles de associação de dados  
  
1.  No **fontes de dados** janela, selecione o nó de nível superior para o **clientes** tabela.  
  
2.  Altere o tipo subjacente da tabela para **detalhes** clicando **detalhes** na lista suspensa no nó da tabela.  
  
3.  Selecione o **clientes** nó da tabela e arraste-o para a região de modelo de item (região superior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Um <xref:System.Windows.Forms.BindingNavigator> controle é adicionado ao formulário e o **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, e **CustomersBindingNavigator** componentes são adicionados à bandeja de componentes.  
  
4.  Selecione todos os campos e seus rótulos associados e posicioná-los próximo à borda esquerda da região de modelo de item.  
  
5.  Selecione os últimos cinco campos (**região**, **CEP**, **país**, **Phone**, e **Fax**) e os rótulos associados e movê-los até e à direita dos seis primeiros campos.  
  
6.  Selecione o modelo de item (região superior do controle).  
  
7.  Na janela Propriedades, defina o **tamanho** propriedade `427, 170`.  
  
 Neste ponto, você tem um aplicativo de trabalho que será exibida uma lista de repetição de clientes. Você pode pressionar F5 para executar o aplicativo, alterar os dados e adicionar ou excluir registros de clientes.  
  
 As próximas etapas opcionais, você aprenderá a personalizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## <a name="next-steps-optional"></a>Próximas etapas (opcionais)  
 Esta parte do passo a passo consiste em quatro tarefas opcionais:  
  
-   Alterando a aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
-   Impedindo que os usuários adicionem ou excluam registros.  
  
-   Adicionando funcionalidade de pesquisa para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
-   Adicionando uma tabela mestre e de detalhes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>Alterando a aparência do controle DataRepeater  
 Nesta etapa opcional, você deve alterar o `BackColor` do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de design. Você também adicionar código para exibir linhas alternando as cores e para alterar um rótulo `ForeColor` condicionalmente.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Para alterar a aparência do controle  
  
1.  No Designer de formulários do Windows, selecione a região principal (inferior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Propriedades, defina o `BackColor` propriedade em branco.  
  
3.  Clique duas vezes o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> para abrir o Editor de código.  
  
4.  No Editor de códigos, lista suspensa de eventos, clique em **DrawItem**.  
  
5.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o seguinte código para alternar o `BackColor`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o código a seguir para alterar o `ForeColor` de um rótulo, dependendo de uma condição:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Pressione F5 para executar o aplicativo e ver as personalizações.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Impedindo que os usuários adicionem ou excluam registros  
 Nesta etapa opcional, você adiciona o código que impede que os usuários adicionem ou excluam registros de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Para impedir que os usuários adicionando e excluindo registros  
  
1.  No Designer de formulários do Windows, clique duas vezes no formulário para abrir o Editor de códigos.  
  
2.  Adicione o seguinte código para o `Form_Load` evento:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Na lista suspensa Nome da classe, clique em **BindingNavigatorDeleteItem**. Na lista suspensa o nome do método, clique em **EnabledChanged**.  
  
4.  Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> habilitará o **DeleteItem** botão toda vez que o registro atual é alterado.  
  
5.  Pressione F5 para executar o aplicativo. Observe que o **DeleteItem** botão será desabilitado e você não pode excluir itens, pressionando a tecla DELETE.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>Adicionando funcionalidade de pesquisa ao controle DataRepeater  
 Nesta etapa opcional, você implementar a capacidade de pesquisar para um valor de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Se a cadeia de caracteres for encontrada, o controle seleciona o item que contém o valor e o item é movido para a exibição.  
  
#### <a name="to-add-search-capability"></a>Para adicionar a funcionalidade de pesquisa  
  
1.  Arraste um <xref:System.Windows.Forms.TextBox> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
2.  Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.  
  
3.  Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle. Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
4.  Na janela Propriedades, altere o **nome** propriedade **SearchButton**. Alterar o **texto** propriedade **pesquisa**.  
  
5.  Clique duas vezes o <xref:System.Windows.Forms.Button> de controle para abrir o Editor de código e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Pressione F5 para executar o aplicativo. Digite uma ID de cliente **SearchTextBox** e clique no **pesquisa** botão.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Adicionando um mestre e a tabela de detalhes para DataRepeater  
 Nesta etapa opcional, você pode adicionar um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para exibir os pedidos relacionados para cada cliente.  
  
#### <a name="to-add-a-master-and-detail-table"></a>Para adicionar uma tabela mestre e de detalhes  
  
1.  Arraste uma segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** para o formulário.  
  
2.  Na janela Propriedades, defina o **local** propriedade `465, 25`.  
  
3.  Definir o **tamanho** propriedade `315, 600`.  
  
4.  No **fontes de dados** janela, expanda o **clientes** nó de tabela e selecione o nó de detalhe para o **pedidos** tabela.  
  
5.  Altere o tipo subjacente desse **pedidos** tabela detalhes clicando **detalhes** na lista suspensa no nó da tabela.  
  
6.  Arraste esta **pedidos** nó de tabela para a área do modelo de item (região superior) do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
     Um **OrdersBindingSource** componente e um **OrdersTableAdapter** componente são adicionados à bandeja de componentes.  
  
7.  Pressione F5 para executar o aplicativo. Quando você seleciona cada cliente na primeira <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar os pedidos de cliente são exibidas na segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao Controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Como exibir dados associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Como exibir controles não associados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Como alterar o layout de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Como exibir cabeçalhos de item em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Como pesquisar dados em um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Como: criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Como alterar a aparência de um controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Como desabilitar a adição e a exclusão de itens DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [Solução de problemas do controle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
