---
title: Como tornar um controle TextBox somente leitura
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d3acf1e5065633f9f4c75f24780230525b01ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Como tornar um controle TextBox somente leitura
Este exemplo mostra como configurar um <xref:System.Windows.Controls.TextBox> controle por não permitir a entrada do usuário ou modificação.  
  
## <a name="example"></a>Exemplo  
 Para impedir que usuários modifiquem o conteúdo de um <xref:System.Windows.Controls.TextBox> controlar, defina o <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo **true**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo afeta somente a entrada do usuário; ele não afeta o texto definido no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] descrição de um <xref:System.Windows.Controls.TextBox> controle ou definir programaticamente por meio de texto a <xref:System.Windows.Controls.TextBox.Text%2A> propriedade.  
  
 O valor padrão de <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> é **false**.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
