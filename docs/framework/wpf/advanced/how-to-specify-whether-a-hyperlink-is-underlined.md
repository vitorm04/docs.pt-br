---
title: 'Como: Especificar se um hiperlink está sublinhado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 3199bce25d49bb471fe21735ebb919bbb7f5132c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576948"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Como: Especificar se um hiperlink está sublinhado
O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de fluxo de nível embutido que permite hospedar hiperlinks dentro do conteúdo de fluxo. Por padrão, <xref:System.Windows.Documents.Hyperlink> usa um <xref:System.Windows.TextDecoration> objeto para exibir um sublinhado. <xref:System.Windows.TextDecoration> objetos podem ser desempenho intenso para instanciar, especialmente se você tiver muitos <xref:System.Windows.Documents.Hyperlink> objetos. Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, você talvez queira considerar a mostrar um sublinhado somente ao disparar um evento, como o <xref:System.Windows.ContentElement.MouseEnter> eventos.  
  
 No exemplo a seguir, o sublinhado para o link "My MSN" é dinâmico — ele aparece somente quando o <xref:System.Windows.ContentElement.MouseEnter> evento é disparado.  
  
 ![Hiperlinks exibindo TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Hiperlinks definidos com TextDecorations  
  
## <a name="example"></a>Exemplo  
 O exemplo de marcação a seguir mostra um <xref:System.Windows.Documents.Hyperlink> definido com e sem sublinhado:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 O exemplo de código a seguir mostra como criar um sublinhado para o <xref:System.Windows.Documents.Hyperlink> no <xref:System.Windows.ContentElement.MouseEnter> evento e removê-lo no <xref:System.Windows.ContentElement.MouseLeave> eventos.  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Otimizando o desempenho do aplicativo WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)
- [Criar uma decoração de texto](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
