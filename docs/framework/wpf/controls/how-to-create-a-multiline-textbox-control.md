---
title: Como criar um controle TextBox multilinha
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a6885a594e5fcd747f85dedf1afbd39ec644717
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Como criar um controle TextBox multilinha
Este exemplo mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle expandirá automaticamente para acomodar várias linhas de texto.  
  
## <a name="example"></a>Exemplo  
 Definindo o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributo **Wrap** fará com que o texto passe para uma nova linha quando a borda do <xref:System.Windows.Controls.TextBox> controle é alcançado, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se é necessário.  
  
 Definindo o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributo **true** faz com que uma nova linha seja inserida quando a tecla é pressionada, outra vez automaticamente expandindo o <xref:System.Windows.Controls.TextBox> para incluir espaço para uma nova linha, se necessário.  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem para o <xref:System.Windows.Controls.TextBox>, de modo que o conteúdo do <xref:System.Windows.Controls.TextBox> pode ser rolado por meio de se o <xref:System.Windows.Controls.TextBox> expande além do tamanho do quadro ou janela que inclui-lo.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.TextWrapping>  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
