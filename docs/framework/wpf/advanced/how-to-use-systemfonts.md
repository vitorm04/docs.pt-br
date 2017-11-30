---
title: Como usar SystemFonts
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ce82724a4e9a547b8441628f43621f29eab6307
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemfonts"></a>Como usar SystemFonts
Este exemplo mostra como usar os recursos estáticos do <xref:System.Windows.SystemFonts> classe para definir o estilo ou personalizar um botão.  
  
## <a name="example"></a>Exemplo  
 Os recursos do sistema expõem vários valores determinados pelo sistema como recursos e propriedades para ajudar a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemFonts>é uma classe que contém os dois valores de fonte como propriedades estáticas e as propriedades que fazem referência a chaves de recurso que podem ser usadas para acessar esses valores dinamicamente em tempo de execução. Por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> é um <xref:System.Windows.SystemFonts> valor, e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> é uma chave de recurso correspondente.  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode usar os membros de <xref:System.Windows.SystemFonts> como propriedades estáticas ou referências a recursos dinâmicos (com o valor da propriedade estática como a chave). Use uma referência de recurso dinâmica se quiser que a métrica de fonte atualize automaticamente enquanto o aplicativo é executado; caso contrário, use uma referência estática ao valor.  
  
> [!NOTE]
>  As chaves de recurso têm o sufixo “Chave” anexado ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar as propriedades de <xref:System.Windows.SystemFonts> como valores estáticos para estilizar ou personalizar um botão. Este exemplo de marcação atribui <xref:System.Windows.SystemFonts> valores a um botão.  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 Para usar os valores de <xref:System.Windows.SystemFonts> no código, você não precisa usar um valor estático ou uma referência de recurso dinâmico. Em vez disso, use as propriedades não-chave do <xref:System.Windows.SystemFonts> classe. Embora as propriedades não-chave sejam aparentemente definidas como propriedades estáticas, o comportamento de tempo de execução [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como hospedado pelo sistema irá reavaliar as propriedades em tempo real e irá corretamente considerar para alterações de valores do sistema controlada pelo usuário. O exemplo a seguir mostra como especificar as configurações de fonte de um botão.  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.SystemFonts>  
 [Pintar uma área com um pincel de sistema](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Usar SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Usar chaves de fontes do sistema](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [Tópicos explicativos](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [Extensão de marcação x:Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [Recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Extensão de marcação DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
