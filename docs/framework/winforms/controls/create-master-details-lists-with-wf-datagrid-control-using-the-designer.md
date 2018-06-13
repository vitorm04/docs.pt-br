---
title: Como criar listas mestre/detalhes com o controle DataGrid dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 20a6f059efab5469879d3c3a45f4005020414316
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529971"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Como criar listas mestre/detalhes com o controle DataGrid dos Windows Forms usando o designer
> [!NOTE]
>  O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado. Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Se seu <xref:System.Data.DataSet> contém uma série de tabelas relacionadas, você pode usar dois <xref:System.Windows.Forms.DataGrid> controles para exibir os dados em um formato de detalhes mestre. Um <xref:System.Windows.Forms.DataGrid> é designado como a grade principal, e o segundo é designado como a grade de detalhes. Quando você seleciona uma entrada na lista mestra, todas as entradas filho relacionados são mostradas na lista de detalhes. Por exemplo, se seu <xref:System.Data.DataSet> contém uma tabela clientes e uma tabela relacionada Orders, você deve especificar a tabela de clientes para a grade principal e a tabela de pedidos para a grade de detalhes. Quando um cliente é selecionado na grade principal, todos os pedidos associados a ele na tabela Pedidos serão exibidos na grade de detalhes.  
  
 O procedimento a seguir requer um projeto de **Aplicativos do Windows**. Para obter informações sobre como configurar um projeto desse tipo, confira [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-master-details-list-in-the-designer"></a>Criar uma lista mestre/detalhes no designer  
  
1.  Adicionar dois <xref:System.Windows.Forms.DataGrid> controles ao formulário. Para mais informações, consulte [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Em [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], o <xref:System.Windows.Forms.DataGrid> controle não está no **caixa de ferramentas** por padrão. Para obter mais informações, consulte [Como adicionar itens à Caixa de ferramentas](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
    > [!NOTE]
    >  As etapas a seguir não são aplicáveis a [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], que usa a janela **Fontes de Dados** para associação de dados no tempo de design. Para obter mais informações, consulte [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) e [Como exibir dados relacionados em um Aplicativo do Windows Forms](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
2.  Arraste duas ou mais tabelas de **Gerenciador de Servidores** ao formulário.  
  
3.  No menu **Dados**, selecione **Gerar conjunto de dados**.  
  
4.  Defina as relações entre as tabelas usando o XML Designer. Para ver mais detalhes, consulte “Como criar relacionamentos um para muitos em esquemas XML e conjuntos de dados” no MSDN.  
  
5.  Salve os relacionamentos selecionando **Salvar tudo** do menu **Arquivo**.  
  
6.  Configurar o <xref:System.Windows.Forms.DataGrid> controle que você deseja designar a grade principal, da seguinte maneira:  
  
    1.  Selecione o <xref:System.Data.DataSet> da lista suspensa no <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriedade.  
  
    2.  Selecione a tabela mestre (por exemplo, "clientes") da lista suspensa no <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedade.  
  
7.  Configurar o <xref:System.Windows.Forms.DataGrid> controle que você deseja designar a grade de detalhes, da seguinte maneira:  
  
    1.  Selecione o <xref:System.Data.DataSet> da lista suspensa no <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriedade.  
  
    2.  Selecione a relação (por exemplo, "Customers.CustOrd") entre as tabelas mestre e de detalhes da lista suspensa no <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriedade. Para ver a relação, expanda o nó clicando no sinal de mais (**+**) ao lado da tabela mestre na lista suspensa.  
  
## <a name="see-also"></a>Consulte também  
 [Controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Visão geral do controle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Como associar o controle DataGrid dos Windows Forms a uma fonte de dados](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Associar controles a dados no Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
