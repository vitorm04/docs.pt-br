---
title: Visão geral do controle BindingNavigator (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: ad63f622aae55cb4175eddc93ab5e086965a8fe8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109103"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>Visão geral do controle BindingNavigator (Windows Forms)
Você pode usar o <xref:System.Windows.Forms.BindingNavigator> controle para criar um meio padronizado para que os usuários a pesquisar e alterar dados em um formulário do Windows. Você usa frequentemente <xref:System.Windows.Forms.BindingNavigator> com o <xref:System.Windows.Forms.BindingSource> para permitir aos usuários percorrer os registros de dados em um formulário e interagir com os registros.  
  
## <a name="how-the-bindingnavigator-works"></a>Como o BindingNavigator funciona  

 O <xref:System.Windows.Forms.BindingNavigator> controle é composto de um <xref:System.Windows.Forms.ToolStrip> com uma série de <xref:System.Windows.Forms.ToolStripItem> objetos para a maioria das ações comuns relacionadas a dados: adição de dados, exclusão de dados e navegar pelos dados. Por padrão, o <xref:System.Windows.Forms.BindingNavigator> controle contém esses botões padrão. A captura de tela a seguir mostra o <xref:System.Windows.Forms.BindingNavigator> controle em um formulário:
  
 ![Captura de tela mostrando o controle BindingNavigator.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 A tabela a seguir lista os controles e descreve suas funções.  
  
|Controle|Função|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Botão|Insere uma nova linha na fonte de dados subjacente.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Botão|Exclui a linha atual da fonte de dados subjacente.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Botão|Move para o primeiro item da fonte de dados subjacente.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Botão|Move para o último item da fonte de dados subjacente.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Botão|Move para o próximo item da fonte de dados subjacente.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Botão|Move para o item anterior da fonte de dados subjacente.|  
|<xref:System.Windows.Forms.BindingNavigator.PositionItem%2A> Caixa de texto|Retorna a posição atual na fonte de dados subjacente.|  
|<xref:System.Windows.Forms.BindingNavigator.CountItem%2A> Caixa de texto|Retorna o número total de itens na fonte de dados subjacente.|  
  
 Para cada controle nessa coleção, há um membro correspondente do <xref:System.Windows.Forms.BindingSource> componente que fornece programaticamente a mesma funcionalidade. Por exemplo, o <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> método da <xref:System.Windows.Forms.BindingSource> componente, o <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> método e assim por diante.  
  
 Se os botões padrão não são adequados para seu aplicativo, ou se você precisar de botões adicionais para dar suporte a outros tipos de funcionalidade, você pode fornecer seu próprio <xref:System.Windows.Forms.ToolStrip> botões. Consulte também [como: Adicione carga, salvar, e botões de cancelamento para o Windows Forms controle BindingNavigator](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
