---
title: Navegar pelos dados com o controle BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736003"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Como navegar em dados com o controle BindingNavigator dos Windows Forms
O advento do controle de <xref:System.Windows.Forms.BindingNavigator> no Windows Forms permite aos desenvolvedores fornecer aos usuários finais uma interface de usuário de navegação e manipulação de dados simples nos formulários que criam.  
  
 O controle de <xref:System.Windows.Forms.BindingNavigator> é um controle de <xref:System.Windows.Forms.ToolStrip> com botões pré-configurados para navegação no primeiro, último, próximo e registro anterior em um conjunto de dados, bem como botões para adicionar e excluir registros. Adicionar botões ao controle de <xref:System.Windows.Forms.BindingNavigator> é fácil, pois é um controle de <xref:System.Windows.Forms.ToolStrip>. Para obter exemplos, consulte [como: adicionar botões carregar, salvar e cancelar ao controle do Windows Forms BindingNavigator](load-save-and-cancel-bindingnavigator.md).  
  
 Para cada botão no controle de <xref:System.Windows.Forms.BindingNavigator>, há um membro correspondente do componente <xref:System.Windows.Forms.BindingSource> que permite programaticamente a mesma funcionalidade. Por exemplo, o botão de <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> corresponde ao método <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> do componente <xref:System.Windows.Forms.BindingSource>, o botão <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> corresponde ao método <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> e assim por diante. Como resultado, a habilitação do controle de <xref:System.Windows.Forms.BindingNavigator> para navegar pelos registros de dados é simples como definir sua propriedade <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> para o componente de <xref:System.Windows.Forms.BindingSource> apropriado no formulário.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Configurar o controle BindingNavigator  
  
1. Adicione um componente de <xref:System.Windows.Forms.BindingSource> chamado `bindingSource1` e dois controles de <xref:System.Windows.Forms.TextBox> chamados `textBox1` e `textBox2`.  
  
2. Associe `bindingSource1` a dados e os controles da caixa de texto a `bindingSource1`. Para fazer isso, Cole o código a seguir em seu formulário e chame `LoadData` no construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método de manipulação de eventos.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. Adicione um controle de <xref:System.Windows.Forms.BindingNavigator> chamado `bindingNavigator1` ao formulário.  
  
4. Defina a propriedade <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> para `bindingNavigator1` como `bindingSource1`. É possível fazer isso com o designer ou em código.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 O exemplo de código a seguir é o exemplo completo para as etapas listadas anteriormente.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o Código  
 Este exemplo requer:  
  
- Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
