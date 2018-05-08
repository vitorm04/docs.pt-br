---
title: Como associar dados ao controle DataGridView dos Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: abed528c9421b878f49817ca60f554cbe3d68a0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Como associar dados ao controle DataGridView dos Windows Forms usando o designer
Você pode usar o designer para conectar-se um <xref:System.Windows.Forms.DataGridView> controle a fontes de dados de vários tipos diferentes, como bancos de dados, objetos de negócios ou serviços da Web. Quando você associa o controle a uma fonte de dados usando o designer, o controle é automaticamente vinculado a um <xref:System.Windows.Forms.BindingSource> componente que representa a fonte de dados. Além disso, as colunas são automaticamente geradas no controle para coincidir com as informações de esquema fornecidas pela fonte de dados.  
  
 Depois que as colunas tiverem sido geradas, você poderá modificá-las para atender às suas necessidades. Por exemplo, você pode remover ou ocultar colunas que você não queira exibir, pode reorganizar as colunas ou pode modificar os tipos de coluna. Para obter mais informações sobre como modificar colunas, consulte os tópicos listados na seção Consulte também.  
  
 Você também pode associar vários <xref:System.Windows.Forms.DataGridView> controles tabelas relacionadas para criar relações de detalhes/mestre. Nessa configuração, um controle exibe uma tabela pai e outro controle exibe somente as linhas de uma tabela filho que estão relacionadas à linha atual na tabela pai. Para obter mais informações, consulte [Como exibir dados relacionados em um aplicativo dos Windows Forms](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.DataGridView> dois controles para uma relação mestre/detalhes. Para obter informações sobre como iniciar um projeto desse tipo, confira [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles aos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>Para associar o controle a uma fonte de dados  
  
1.  Clique na marca inteligente (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) no canto superior direito do <xref:System.Windows.Forms.DataGridView> controle.  
  
2.  Clique na seta suspensa para a opção **Escolher Fonte de Dados**.  
  
3.  Se seu projeto ainda não tiver uma fonte de dados, clique em **Adicionar Fonte de Dados do Projeto** e siga as etapas indicadas pelo assistente.  
  
     Para obter mais informações, consulte [Assistente de Configuração da Fonte de Dados](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). A nova fonte de dados aparecerá na janela suspensa **Escolher Fonte de Dados**. Se a nova fonte de dados contiver apenas um membro, como uma única tabela de banco de dados, o controle será associado automaticamente a esse membro. Do contrário, continue para a próxima etapa.  
  
4.  Expanda os nós **Outras Fontes de Dados** e **Fontes de Dados do Projeto** se eles ainda não tiverem sido expandidos e, em seguida, selecione a fonte de dados à qual associar o controle.  
  
5.  Se sua fonte de dados contém mais de um membro, como se você criou um <xref:System.Data.DataSet?displayProperty=nameWithType> que contém várias tabelas, expanda a fonte de dados e, em seguida, selecione o membro específico para associar a.  
  
6.  Para criar uma relação mestre/detalhes, no **Escolher fonte de dados** janela suspensa por um segundo <xref:System.Windows.Forms.DataGridView> controlar, expanda o <xref:System.Windows.Forms.BindingSource> criado para a tabela pai e, em seguida, selecione a tabela filho relacionada na lista mostrado.  
  
    > [!NOTE]
    >  Se o projeto já tiver uma fonte de dados, você também poderá usar a janela **Fontes de Dados** para criar um formulário de dados. Para obter mais informações, consulte [Janela de Fontes de Dados](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 [Como conectar-se a dados em um banco de dados](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)  
 [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Como alterar a ordem das colunas no controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 [Como alterar o tipo de uma coluna DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 [Como congelar colunas no controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [Como ocultar colunas no controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 [Como tornar as colunas somente leitura no controle DataGridView dos Windows Forms usando o designer](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 [Como: criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Janela Fontes de Dados](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)  
 [Como exibir dados relacionados em um Aplicativo do Windows Forms](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
