---
title: 'Como: Alterar a tipografia de texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting Typography attributes [WPF]
- Typography attribute [WPF], setting
ms.assetid: 19a3b49b-60a2-4c11-a786-e26b4c965588
ms.openlocfilehash: f04c873e542ad02c1d2a20b770ded4464af7a6d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645399"
---
# <a name="how-to-alter-the-typography-of-text"></a>Como: Alterar a tipografia de texto
O exemplo a seguir mostra como definir a <xref:System.Windows.Documents.TextElement.Typography%2A> de atributo, usando <xref:System.Windows.Documents.Paragraph> como o elemento de exemplo.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 A figura a seguir mostra como esse exemplo é renderizado.  
  
 ![Captura de tela: Texto com tipografia alterada](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Em comparação, a figura a seguir mostra como um exemplo semelhante com propriedades tipográficas padrão é renderizado.  
  
 ![Captura de tela: Texto com tipografia alterada](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o <xref:System.Windows.Controls.TextBox.Typography%2A> propriedade programaticamente.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral do documento de fluxo](../../../../docs/framework/wpf/advanced/flow-document-overview.md)
