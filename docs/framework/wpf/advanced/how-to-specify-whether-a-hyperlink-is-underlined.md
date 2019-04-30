---
title: 'Como: Especificar se um hiperlink está sublinhado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 5718912e24a0697f209669b0ab4e7f4df1765ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943943"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>Como: Especificar se um hiperlink está sublinhado
O <xref:System.Windows.Documents.Hyperlink> objeto é um elemento de conteúdo de fluxo de nível embutido que permite hospedar hiperlinks dentro do conteúdo de fluxo. Por padrão, <xref:System.Windows.Documents.Hyperlink> usa um <xref:System.Windows.TextDecoration> objeto para exibir um sublinhado. <xref:System.Windows.TextDecoration> objetos podem ser desempenho intenso para instanciar, especialmente se você tiver muitos <xref:System.Windows.Documents.Hyperlink> objetos. Se você fizer uso extensivo de <xref:System.Windows.Documents.Hyperlink> elementos, você talvez queira considerar a mostrar um sublinhado somente ao disparar um evento, como o <xref:System.Windows.ContentElement.MouseEnter> eventos.  
  
 No exemplo a seguir, o sublinhado para o link "My MSN" é dinâmico, ou seja, ele aparece somente quando o <xref:System.Windows.ContentElement.MouseEnter> evento é disparado.  
  
  ![Hiperlinks exibindo TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)  

## <a name="example"></a>Exemplo  
 O exemplo de marcação a seguir mostra um <xref:System.Windows.Documents.Hyperlink> definido com e sem sublinhado:  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 O exemplo de código a seguir mostra como criar um sublinhado para o <xref:System.Windows.Documents.Hyperlink> no <xref:System.Windows.ContentElement.MouseEnter> evento e removê-lo no <xref:System.Windows.ContentElement.MouseLeave> eventos.  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [Otimizando o desempenho do aplicativo WPF](optimizing-wpf-application-performance.md)
- [Criar uma decoração de texto](how-to-create-a-text-decoration.md)
