---
title: Usando a linha para novos registros no controle DataGridView dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4633a70f6c3d010e6cc75236778cf2fd59c0e05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Usando a linha para novos registros no controle DataGridView dos Windows Forms
Quando você usa um <xref:System.Windows.Forms.DataGridView> para editar dados em seu aplicativo, você geralmente deve dar aos usuários a capacidade de adicionar novas linhas de dados para o repositório de dados. O <xref:System.Windows.Forms.DataGridView> controle oferece suporte a essa funcionalidade, fornecendo uma linha para novos registros, que é sempre exibido como a última linha. Ela é marcada com um símbolo de asterisco (*) em seu cabeçalho de linha. As seções a seguir tratam de algumas coisas que você deve considerar quando programar com a linha de novos registros habilitada.  
  
## <a name="displaying-the-row-for-new-records"></a>Exibindo a linha de novos registros  
 Use o <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriedade para indicar se a linha para novos registros é exibida. O valor padrão dessa propriedade é `true`.  
  
 Para os dados associados caso, a linha para novos registros será mostrada se a <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriedade do controle e o <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> propriedade da fonte de dados são ambos `true`. Se uma delas for `false`, a linha não será exibida.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Preenchendo a linha de novos registros com os dados padrão  
 Quando o usuário seleciona a linha para novos registros da linha atual, o <xref:System.Windows.Forms.DataGridView> controlar gera o <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> evento.  
  
 Esse evento fornece acesso ao novo <xref:System.Windows.Forms.DataGridViewRow> e permite que você preencher a nova linha com os dados padrão. Para obter mais informações, consulte [Como especificar valores padrão para novas linhas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>A coleção de linhas  
 A linha para novos registros está contida no <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção mas tem um comportamento diferente em dois aspectos:  
  
-   Não é possível remover a linha para novos registros de <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção programaticamente. Um <xref:System.InvalidOperationException> é gerada se isso for tentado. O usuário também não pode excluir a linha de novos registros. O <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> método não remove essa linha do <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção.  
  
-   Nenhuma linha pode ser adicionada após a linha de novos registros. Um <xref:System.InvalidOperationException> é gerado se isso for tentado. Como resultado, a linha para novos registros é sempre a última linha a <xref:System.Windows.Forms.DataGridView> controle. Os métodos em <xref:System.Windows.Forms.DataGridViewRowCollection> que adicionam linhas —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, e <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— todos chamar métodos de inserção internamente quando a linha para novos registros está presente.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Personalização visual da linha de novos registros  
 Quando a linha para novos registros é criada, ele se baseia a linha especificada pelo <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriedade. Qualquer estilo de célula que não for especificado para essa linha será herdado de outras propriedades. Para obter mais informações sobre herança de estilo de célula, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Os valores iniciais exibidos por células na linha para novos registros são recuperados de cada célula <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> propriedade. Para células de tipo <xref:System.Windows.Forms.DataGridViewImageCell>, essa propriedade retorna uma imagem de espaço reservado. Caso contrário, essa propriedade retornará `null`. Você pode substituir essa propriedade para retornar um valor personalizado. No entanto, esses valores iniciais podem ser substituídos por um <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> manipulador de eventos quando o foco entra na linha para novos registros.  
  
 Os ícones padrão do cabeçalho dessa linha, que são uma seta ou um asterisco, não são expostos publicamente. Se você desejar personalizar os ícones, você precisará criar um personalizado <xref:System.Windows.Forms.DataGridViewRowHeaderCell> classe.  
  
 Usam os ícones padrão a <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> propriedade o <xref:System.Windows.Forms.DataGridViewCellStyle> em uso pela célula do cabeçalho de linha. Os ícones padrão não serão renderizados se não houver espaço suficiente para exibi-los completamente.  
  
 Se a célula do cabeçalho de linha tiver um valor de cadeia de caracteres definido e, se não houver espaço suficiente para o texto e o ícone, o ícone será descartado primeiro.  
  
## <a name="sorting"></a>Classificação  
 No modo não vinculado, os novos registros sempre serão adicionados ao final do <xref:System.Windows.Forms.DataGridView> mesmo se o usuário classificou o conteúdo a <xref:System.Windows.Forms.DataGridView>. O usuário precisará aplicar a classificação novamente para classificar a linha na posição correta; Esse comportamento é semelhante do <xref:System.Windows.Forms.ListView> controle.  
  
 Em modos virtuais ou com associação de dados, o comportamento de inserção quando uma classificação for aplicada dependerá da implementação do modelo de dados. Para [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], a linha é classificada imediatamente na posição correta.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Outras observações sobre a linha de novos registros  
 Não é possível definir o <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> propriedade desta linha para `false`. Um <xref:System.InvalidOperationException> é gerado se isso for tentado.  
  
 A linha de novos registros sempre é criada no estado desmarcado.  
  
## <a name="virtual-mode"></a>Modo virtual  
 Se estiver implementando o modo virtual, você precisará monitorar quando uma linha de novos registros é necessária no modelo de dados e o momento para reverter a adição da linha. A implementação exata dessa funcionalidade depende da implementação do modelo de dados e de sua semântica de transação, por exemplo, se o escopo de confirmação está no nível da célula ou da linha. Para obter mais informações, consulte [Modo virtual no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Entrada de Dados no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Como especificar valores padrão para novas linhas no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
