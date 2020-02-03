---
title: Criar listas mestras-detalhes com controle DataGrid usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 0dea3dd88a8c6c2aceb894789ace8ef3b5c83632
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743392"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Como criar listas mestre/detalhes com o controle DataGrid dos Windows Forms usando o designer

> [!NOTE]
> O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Se sua <xref:System.Data.DataSet> contiver uma série de tabelas relacionadas, você poderá usar dois controles <xref:System.Windows.Forms.DataGrid> para exibir os dados em um formato mestre-de-detalhes. Uma <xref:System.Windows.Forms.DataGrid> é designada para ser a grade mestre e a segunda é designada para ser a grade de detalhes. Quando você seleciona uma entrada na lista mestra, todas as entradas filho relacionados são mostradas na lista de detalhes. Por exemplo, se sua <xref:System.Data.DataSet> contiver uma tabela Customers e uma tabela Orders relacionadas, você deverá especificar a tabela Customers como a grade mestre e a tabela Orders como a grade details. Quando um cliente é selecionado na grade principal, todos os pedidos associados a ele na tabela Pedidos serão exibidos na grade de detalhes.

 O procedimento a seguir requer um projeto de **aplicativo do Windows** (**arquivo** > **novo** > **projeto** > **Visual C#**  ou **Visual Basic** > **área de trabalho clássica** > Windows Forms **aplicativo**).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Criar uma lista mestre/detalhes no designer

1. Adicione dois controles de <xref:System.Windows.Forms.DataGrid> ao formulário. Para mais informações, consulte [Como adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md). No Visual Studio 2005, o controle <xref:System.Windows.Forms.DataGrid> não está na **caixa de ferramentas** por padrão. Para obter mais informações, consulte [Como adicionar itens à Caixa de ferramentas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

    > [!NOTE]
    > As etapas a seguir não são aplicáveis ao Visual Studio 2005, que usa a janela **fontes de dados** para a associação de dados de tempo de design. Para obter mais informações, consulte [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) e [Como exibir dados relacionados em um Aplicativo do Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

2. Arraste duas ou mais tabelas de **Gerenciador de Servidores** ao formulário.

3. No menu **Dados**, selecione **Gerar conjunto de dados**.

4. Defina as relações entre as tabelas usando o XML Designer. Para ver mais detalhes, consulte “Como criar relacionamentos um para muitos em esquemas XML e conjuntos de dados” no MSDN.

5. Salve os relacionamentos selecionando **Salvar tudo** do menu **Arquivo**.

6. Configure o controle de <xref:System.Windows.Forms.DataGrid> que você deseja designar a grade mestra, da seguinte maneira:

    1. Selecione o <xref:System.Data.DataSet> na lista suspensa na propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A>.

    2. Selecione a tabela mestra (por exemplo, "clientes") na lista suspensa na propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A>.

7. Configure o controle de <xref:System.Windows.Forms.DataGrid> que você deseja designar a grade de detalhes, da seguinte maneira:

    1. Selecione o <xref:System.Data.DataSet> na lista suspensa na propriedade <xref:System.Windows.Forms.DataGrid.DataSource%2A>.

    2. Selecione a relação (por exemplo, "Customers. CustOrd") entre as tabelas mestre e de detalhes da lista suspensa na propriedade <xref:System.Windows.Forms.DataGrid.DataMember%2A>. Para ver a relação, expanda o nó clicando no sinal de mais ( **+** ) ao lado da tabela mestre na lista suspensa.

## <a name="see-also"></a>Consulte também

- [Controle DataGrid](datagrid-control-windows-forms.md)
- [Visão geral do controle DataGrid](datagrid-control-overview-windows-forms.md)
- [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
