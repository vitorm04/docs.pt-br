---
title: Como navegar em dados com o controle BindingNavigator dos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5b49d84f98213e95c83c5476007297149adc16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Como navegar em dados com o controle BindingNavigator dos Windows Forms
O surgimento do <xref:System.Windows.Forms.BindingNavigator> controle em formulários do Windows permite que os desenvolvedores fornecer aos usuários finais com dados simples navegação e manipulação de interface do usuário em formulários de criar.  
  
 O <xref:System.Windows.Forms.BindingNavigator> controle é um <xref:System.Windows.Forms.ToolStrip> controle com botões pré-configurado para a navegação para a primeira, última, registro próximo e anterior em um conjunto de dados, bem como os botões para adicionar e excluir registros. Adicionando botões para o <xref:System.Windows.Forms.BindingNavigator> controle é fácil, porque é um <xref:System.Windows.Forms.ToolStrip> controle.  Consulte também [Como adicionar botões Carregar, Salvar e Cancelar ao controle BindingNavigator do Windows Forms](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).  
  
 Para cada botão de <xref:System.Windows.Forms.BindingNavigator> controlar, existe um membro correspondente do <xref:System.Windows.Forms.BindingSource> componente que programaticamente permite que a mesma funcionalidade. Por exemplo, o <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> método do <xref:System.Windows.Forms.BindingSource> componente, o <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> botão corresponde à <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> método e assim por diante. Como resultado, habilitando o <xref:System.Windows.Forms.BindingNavigator> controle para navegar pelos registros de dados é um simples como configuração de seu <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade apropriada <xref:System.Windows.Forms.BindingSource> componente no formulário.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Configurar o controle BindingNavigator  
  
1.  Adicionar um <xref:System.Windows.Forms.BindingSource> componente denominado `bindingSource1` e dois <xref:System.Windows.Forms.TextBox> controles denominados `textBox1` e `textBox2`.  
  
2.  Associe `bindingSource1` a dados e os controles da caixa de texto a `bindingSource1`. Para fazer isso, cole o código a seguir no seu formulário e chamada `LoadData` do construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Adicionar um <xref:System.Windows.Forms.BindingNavigator> controle chamado `bindingNavigator1` ao formulário.  
  
4.  Definir o <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriedade `bindingNavigator1` para `bindingSource1`. É possível fazer isso com o designer ou em código.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir é o exemplo completo para as etapas listadas anteriormente.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referência aos conjuntos System, System.Data, System.Drawing, System.Windows.Forms e System.Xml.  
  
 Para obter informações sobre como compilar este exemplo na linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line (Compilando na linha de comando)](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Compilando pela linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Controle BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
