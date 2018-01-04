---
title: "Como obter uma coleção de linhas a partir de um TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12d32266bb901f6ce47d19d92d6f0785277aa7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Como obter uma coleção de linhas a partir de um TextBox
Este exemplo mostra como obter um conjunto de linhas de texto de um <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um método simple que usa um <xref:System.Windows.Controls.TextBox> como o argumento e retorna um <xref:System.Collections.Specialized.StringCollection> contendo as linhas do texto no **caixa de texto**.  O <xref:System.Windows.Controls.TextBox.LineCount%2A> propriedade é usada para determinar quantas linhas estão atualmente no **TextBox**e o <xref:System.Windows.Controls.TextBox.GetLineText%2A> método é usado para extrair cada linha e adicioná-lo à coleção de linhas.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
