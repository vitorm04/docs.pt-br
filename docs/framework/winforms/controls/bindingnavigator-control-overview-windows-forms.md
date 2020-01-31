---
title: Visão geral do controle BindingNavigator
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: c2747a6801d4aa9cfde4227ffd5c29ca1de78d48
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744107"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>Visão geral do controle BindingNavigator (Windows Forms)
Você pode usar o controle de <xref:System.Windows.Forms.BindingNavigator> para criar um meio padronizado para os usuários pesquisarem e alterarem dados em um formulário do Windows. Você usa com frequência <xref:System.Windows.Forms.BindingNavigator> com o componente <xref:System.Windows.Forms.BindingSource> para permitir que os usuários passem por registros de dados em um formulário e interajam com os registros.  
  
## <a name="how-the-bindingnavigator-works"></a>Como o BindingNavigator funciona  

 O controle de <xref:System.Windows.Forms.BindingNavigator> é composto de uma <xref:System.Windows.Forms.ToolStrip> com uma série de objetos <xref:System.Windows.Forms.ToolStripItem> para a maioria das ações comuns relacionadas a dados: adicionar dados, excluir dados e navegar pelos dados. Por padrão, o controle de <xref:System.Windows.Forms.BindingNavigator> contém esses botões padrão. A captura de tela a seguir mostra o controle <xref:System.Windows.Forms.BindingNavigator> em um formulário:
  
 ![Captura de tela mostrando o controle BindingNavigator.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 A tabela a seguir lista os controles e descreve suas funções.  
  
|Controle|Função|  
|-------------|--------------|  
|botão de <xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A>|Insere uma nova linha na fonte de dados subjacente.|  
|botão de <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>|Exclui a linha atual da fonte de dados subjacente.|  
|botão de <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>|Move para o primeiro item da fonte de dados subjacente.|  
|botão de <xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A>|Move para o último item da fonte de dados subjacente.|  
|botão de <xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A>|Move para o próximo item da fonte de dados subjacente.|  
|botão de <xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A>|Move para o item anterior da fonte de dados subjacente.|  
|caixa de texto <xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>|Retorna a posição atual na fonte de dados subjacente.|  
|caixa de texto <xref:System.Windows.Forms.BindingNavigator.CountItem%2A>|Retorna o número total de itens na fonte de dados subjacente.|  
  
 Para cada controle nesta coleção, há um membro correspondente do componente <xref:System.Windows.Forms.BindingSource> que fornece programaticamente a mesma funcionalidade. Por exemplo, o botão de <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> corresponde ao método <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> do componente <xref:System.Windows.Forms.BindingSource>, o botão <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> corresponde ao método <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> e assim por diante.  
  
 Se os botões padrão não forem adequados ao seu aplicativo, ou se você precisar de botões adicionais para dar suporte a outros tipos de funcionalidade, você poderá fornecer seus próprios botões de <xref:System.Windows.Forms.ToolStrip>. Consulte também [Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator do Windows Forms](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
