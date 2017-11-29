---
title: Como usar chaves de fontes do sistema
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18781e3d71b9b30352323081e6d938350c6e53d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-fonts-keys"></a>Como usar chaves de fontes do sistema
Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemFonts>é uma classe que contém valores de fonte e os recursos de fonte do sistema que mapeiam para os valores — por exemplo, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> e <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>.  
  
 As métricas de fonte do sistema podem ser usadas como recursos estáticos ou dinâmicos. Use um recurso dinâmico se desejar que a métrica da fonte seja atualizada automaticamente enquanto o aplicativo é executado; caso contrário, use um recurso estático.  
  
> [!NOTE]
>  Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar recursos dinâmicos de fonte do sistema para estilizar ou personalizar um botão. Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo cria um estilo de botão que atribui <xref:System.Windows.SystemFonts> valores a um botão.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>Consulte também  
 [Pintar uma área com um pincel de sistema](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Usar SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [Usar SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
