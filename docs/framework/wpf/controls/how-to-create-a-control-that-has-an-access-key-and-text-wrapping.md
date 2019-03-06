---
title: 'Como: Criar um controle que tenha uma tecla de acesso e disposição do texto'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: e410b92f90f775471ef5d89365549ccd5bb7f085
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361896"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>Como: Criar um controle que tenha uma tecla de acesso e disposição do texto
Este exemplo mostra como criar um controle que tenha uma tecla de acesso e dê suporte à disposição do texto. O exemplo usa um <xref:System.Windows.Controls.Label> controle para ilustrar esses conceitos.  
  
## <a name="example"></a>Exemplo  
 **Adicionar disposição do texto ao seu rótulo**  
  
 O <xref:System.Windows.Controls.Label> controle não dá suporte a disposição do texto. Se for preciso um rótulo que se encaixe em várias linhas, será possível aninhar outro elemento que dá suporte à disposição do texto e colocar o elemento dentro do rótulo. O exemplo a seguir mostra como usar um <xref:System.Windows.Controls.TextBlock> para criar um rótulo que envolve várias linhas de texto.  
  
 [!code-xaml[LabelSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **Adicionar uma tecla de acesso e disposição do texto ao seu rótulo**  
  
 Se precisar de um <xref:System.Windows.Controls.Label> que tem uma chave de acesso (mnemonic), use o <xref:System.Windows.Controls.AccessText> elemento que está dentro do <xref:System.Windows.Controls.Label>.  
  
 Controles como <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, e <xref:System.Windows.Controls.GroupBox> têm modelos de controle padrão. Esses modelos contêm um <xref:System.Windows.Controls.ContentPresenter>. Uma das propriedades que podem ser definidos na <xref:System.Windows.Controls.ContentPresenter> é <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", que pode ser usada para especificar uma chave de acesso para o controle.  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.Label> que tem uma chave de acesso e oferece suporte a quebra automática de texto. Para habilitar a disposição do texto, o exemplo define o <xref:System.Windows.Controls.AccessText.TextWrapping%2A> propriedade e usa um caractere sublinhado para especificar a chave de acesso. (O caractere que vem imediatamente após o caractere sublinhado é a tecla de acesso.)  
  
 [!code-xaml[LabelSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>Consulte também
- [Como: Defina a propriedade de destino de um rótulo](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752101(v=vs.90))
