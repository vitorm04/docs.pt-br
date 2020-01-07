---
title: Como usar SystemFonts
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 157565ceb9057049aef8b2bf274847d58c6b8dc8
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559957"
---
# <a name="how-to-use-systemfonts"></a>Como usar SystemFonts
Este exemplo mostra como usar os recursos estáticos da classe <xref:System.Windows.SystemFonts> para estilizar ou personalizar um botão.  
  
## <a name="example"></a>Exemplo  
 Os recursos do sistema expõem vários valores determinados pelo sistema como recursos e propriedades para ajudar a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemFonts> é uma classe que contém ambos os valores de fonte do sistema como propriedades estáticas e propriedades que fazem referência a chaves de recurso que podem ser usadas para acessar esses valores dinamicamente em tempo de execução. Por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> é um valor de <xref:System.Windows.SystemFonts> e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> é uma chave de recurso correspondente.  
  
 No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode usar os membros de <xref:System.Windows.SystemFonts> como propriedades estáticas ou referências de recursos dinâmicos (com o valor da propriedade estática como a chave). Use uma referência de recurso dinâmica se quiser que a métrica de fonte atualize automaticamente enquanto o aplicativo é executado; caso contrário, use uma referência estática ao valor.  
  
> [!NOTE]
> As chaves de recurso têm o sufixo “Chave” anexado ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar as propriedades de <xref:System.Windows.SystemFonts> como valores estáticos para estilizar ou personalizar um botão. Este exemplo de marcação atribui valores de <xref:System.Windows.SystemFonts> a um botão.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Para usar os valores de <xref:System.Windows.SystemFonts> no código, você não precisa usar um valor estático ou uma referência de recurso dinâmico. Em vez disso, use as propriedades não chave da classe <xref:System.Windows.SystemFonts>. Embora as propriedades não chave sejam, aparentemente, definidas como propriedades estáticas, o comportamento de tempo de execução de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como hospedado pelo sistema reavaliará as propriedades em tempo real e contará adequadamente com as alterações controladas pelo usuário nos valores do sistema. O exemplo a seguir mostra como especificar as configurações de fonte de um botão.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.SystemFonts>
- [Pintar uma área com um pincel de sistema](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Usar SystemParameters](how-to-use-systemparameters.md)
- [Usar chaves de fontes do sistema](how-to-use-system-fonts-keys.md)
- [Tópicos de instruções](resources-how-to-topics.md)
- [Extensão de marcação x:Static](../../../desktop-wpf/xaml-services/xstatic-markup-extension.md)
- [Recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Extensão de marcação DynamicResource](dynamicresource-markup-extension.md)
