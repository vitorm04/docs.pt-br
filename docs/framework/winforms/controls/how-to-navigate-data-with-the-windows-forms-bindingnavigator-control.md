---
title: 'Como: Navegar em dados com o controle BindingNavigator do Windows Forms'
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
ms.openlocfilehash: 0c2fdf820b9b42a592c422cf77362598c5e5eed7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338885"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Como: Navegar em dados com o controle BindingNavigator do Windows Forms
O advento do <xref:System.Windows.Forms.BindingNavigator> controle no Windows Forms permite aos desenvolvedores fornecer aos usuários finais com um simples de dados de navegação e manipulação de interface do usuário em formulários que criam.  
  
 O <xref:System.Windows.Forms.BindingNavigator> controle é um <xref:System.Windows.Forms.ToolStrip> controle com botões pré-configurados para navegação para a primeira, por último, próximo e anterior registro em um conjunto de dados, bem como os botões para adicionar e excluir registros. Adicionando botões para o <xref:System.Windows.Forms.BindingNavigator> controle é fácil, porque ele é um <xref:System.Windows.Forms.ToolStrip> controle. Para ver mais exemplos, veja [Como: Adicione carga, salvar, e botões de cancelamento para o Windows Forms controle BindingNavigator](load-save-and-cancel-bindingnavigator.md).  
  
 Para cada botão de <xref:System.Windows.Forms.BindingNavigator> de controle, há um membro correspondente do <xref:System.Windows.Forms.BindingSource> componente que permite programaticamente a mesma funcionalidade. Por exemplo, o <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> método da <xref:System.Windows.Forms.BindingSource> componente, o <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> método e assim por diante. Como resultado, permitindo que o <xref:System.Windows.Forms.BindingNavigator> controle naveguem nos registros de dados é tão simples como a configuração de seu <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade ao apropriado <xref:System.Windows.Forms.BindingSource> componente no formulário.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Configurar o controle BindingNavigator  
  
1. Adicionar um <xref:System.Windows.Forms.BindingSource> componente denominado `bindingSource1` e duas <xref:System.Windows.Forms.TextBox> controles denominados `textBox1` e `textBox2`.  
  
2. Associe `bindingSource1` a dados e os controles da caixa de texto a `bindingSource1`. Para fazer isso, cole o código a seguir no formulário e chame `LoadData` do construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. Adicionar um <xref:System.Windows.Forms.BindingNavigator> controle chamado `bindingNavigator1` ao seu formulário.  
  
4. Defina as <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade para `bindingNavigator1` para `bindingSource1`. É possível fazer isso com o designer ou em código.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir é o exemplo completo para as etapas listadas anteriormente.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.  
  
 Para obter informações sobre como compilar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [compilando da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.BindingNavigator>
- [Controle BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
