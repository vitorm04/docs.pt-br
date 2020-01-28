---
title: Modo virtual no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 0d82f0fc9946e5b61ea171f2f5d2ab5690db0c71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745439"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Modo virtual no controle DataGridView dos Windows Forms
Com o modo virtual, você pode gerenciar a interação entre o controle de <xref:System.Windows.Forms.DataGridView> e um cache de dados personalizado. Para implementar o modo virtual, defina a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> como `true` e manipule um ou mais dos eventos descritos neste tópico. Você normalmente manipulará pelo menos o evento `CellValueNeeded`, que permite os valores de consulta do controle no cache de dados.  
  
## <a name="bound-mode-and-virtual-mode"></a>Modo associado e modo virtual  
 O modo virtual é necessário somente quando você precisar suplementar ou substituir o modo associado. No modo ligado, você define a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A> e o controle carrega automaticamente os dados da origem especificada e envia as alterações do usuário de volta para ele. Você pode controlar quais colunas associadas são exibidas e a fonte de dados que geralmente lida com operações como classificação.  
  
## <a name="supplementing-bound-mode"></a>Complementando o modo associado  
 Você pode complementar o modo associado exibindo colunas não associadas junto com as colunas associadas. Isso, às vezes, é chamado de "modo misto" e é útil para exibir coisas como controles de interface do usuário ou valores calculados.  
  
 Como as colunas não associadas estão fora da fonte de dados, elas são ignoradas por operações de classificação da fonte de dados. Portanto, ao habilitar a classificação no modo misto, você deve gerenciar os dados desvinculados em um cache local e implementar o modo virtual para permitir que o controle de <xref:System.Windows.Forms.DataGridView> interaja com ele.  
  
 Para obter mais informações sobre como usar o modo virtual para manter os valores em colunas desassociadas, consulte os exemplos na propriedade <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> tópicos de referência de classe.  
  
## <a name="replacing-bound-mode"></a>Substituindo o modo associado  
 Se o modo associado não atender às suas necessidades de desempenho, você poderá gerenciar todos os seus dados em um cache personalizado por meio de manipuladores de eventos de modo virtual. Por exemplo, você pode usar o modo virtual para implementar um mecanismo de carregamento de dados Just-In-Time que recupera apenas os dados necessários de um banco de dados para desempenho ideal. Esse cenário é particularmente útil ao trabalhar com grandes quantidades de dados em uma conexão de rede lenta ou com computadores cliente que têm uma quantidade limitada de RAM ou espaço de armazenamento.  
  
 Para obter mais informações sobre como usar o modo virtual em um cenário Just-In-Time, consulte [Implementando o modo virtual com o carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Eventos de modo virtual  
 Se seus dados são somente leitura, o evento `CellValueNeeded` pode ser o único com o qual você precisará lidar. Eventos adicionais de modo virtual permitem que você habilite uma funcionalidade específica como edições do usuário, adição de linha e exclusão e transações de nível de linha.  
  
 Alguns eventos de <xref:System.Windows.Forms.DataGridView> padrão (como eventos que ocorrem quando os usuários adicionam ou excluem linhas, ou quando os valores de células são editados, analisados, validados ou formatados) também são úteis no modo virtual. Você também pode manipular eventos que lhe permitam manter valores que geralmente não são armazenados em uma fonte de dados associada, como o texto de dica de ferramenta da célula, texto de erro de linha e célula, célula e dados de menu de atalho da linha e dados de altura de linha.  
  
 Para mais informações sobre como implementar o modo virtual para gerenciar os dados de leitura/gravação com um escopo de confirmação de nível de linha, consulte [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
 Para obter um exemplo que implementa o modo virtual com um escopo de confirmação em nível de célula, consulte o tópico referência de propriedade de <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
 Os eventos a seguir ocorrem somente quando a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é definida como `true`.  
  
|Event|Descrição|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Usado pelo controle para recuperar um valor de célula do cache de dados para exibição. Esse evento ocorre somente para células em colunas não associadas.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Usado pelo controle para confirmar a entrada do usuário de uma célula para o cache de dados. Esse evento ocorre somente para células em colunas não associadas.<br /><br /> Chame o método <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> ao alterar um valor em cache fora de um manipulador de eventos <xref:System.Windows.Forms.DataGridView.CellValuePushed> para garantir que o valor atual seja exibido no controle e aplique todos os modos de dimensionamento automático atualmente em vigor.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Usado pelo controle para indicar a necessidade de uma nova linha no cache de dados.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Usado pelo controle para determinar se uma linha tem alterações não confirmadas.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Usado pelo controle para indicar que uma linha deve ser revertida para seus valores armazenados em cache.|  
  
 Os eventos a seguir são úteis no modo virtual, mas podem ser usados independentemente da configuração da propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
|Events|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Usado pelo controle para indicar quando as linhas são excluídas ou adicionadas, permitindo a atualização do cache de dados adequadamente.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Usado pelo controle para formatar valores de célula para exibição e para analisar e validar a entrada do usuário.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Usado pelo controle para recuperar texto de dica de ferramenta de célula quando a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A> é definida ou a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é `true`.<br /><br /> Dicas de ferramenta de célula são exibidas somente quando o valor da propriedade <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> é `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Usado pelo controle para recuperar texto de erro de célula ou de linha quando a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A> é definida ou a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é `true`.<br /><br /> Chame o método <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> ou o método <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> ao alterar o texto de erro de célula ou de linha para garantir que o valor atual seja exibido no controle.<br /><br /> Os glifos de erro de célula e de linha são exibidos quando os valores de propriedade <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> e <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> são `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Usado pelo controle para recuperar uma célula ou linha <xref:System.Windows.Forms.ContextMenuStrip> quando a propriedade de <xref:System.Windows.Forms.DataGridView.DataSource%2A> de controle é definida ou a propriedade <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> é `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Usado pelo controle para recuperar ou armazenar informações de altura de linha no cache de dados. Chame o método <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> ao alterar as informações de altura de linha em cache fora de um manipulador de eventos <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> para garantir que o valor atual seja usado na exibição do controle.|  
  
## <a name="best-practices-in-virtual-mode"></a>Melhores práticas para o modo virtual  
 Se estiver implementando o modo virtual para trabalhar com eficiência com grandes quantidades de dados, você também desejará garantir que esteja trabalhando com eficiência com o próprio controle de <xref:System.Windows.Forms.DataGridView>. Para mais informações sobre o uso eficiente dos estilos de célula, dimensionamento automático, seleções e compartilhamento de linhas, consulte [Melhores práticas para dimensionamento do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Ajuste de desempenho no controle DataGridView dos Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Passo a passo: implementando o modo virtual no controle DataGridView dos Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Implementando o modo virtual com carregamento de dados Just-In-Time no controle DataGridView dos Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
