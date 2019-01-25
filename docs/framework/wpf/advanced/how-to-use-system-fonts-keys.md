---
title: 'Como: Usar chaves de fontes do sistema'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: aec3ba8b84836d068b7efcfe53b34b126334b8de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628702"
---
# <a name="how-to-use-system-fonts-keys"></a>Como: Usar chaves de fontes do sistema
Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemFonts> é uma classe que contém valores de fonte e recursos de fonte de sistema que se associam aos valores — por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 As métricas de fonte do sistema podem ser usadas como recursos estáticos ou dinâmicos. Use um recurso dinâmico se desejar que a métrica da fonte seja atualizada automaticamente enquanto o aplicativo é executado; caso contrário, use um recurso estático.  
  
> [!NOTE]
>  Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar recursos dinâmicos de fonte do sistema para estilizar ou personalizar um botão. Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo cria um estilo de botão que atribui <xref:System.Windows.SystemFonts> valores a um botão.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Consulte também
- [Pintar uma área com um pincel de sistema](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Usar SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
- [Usar SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
