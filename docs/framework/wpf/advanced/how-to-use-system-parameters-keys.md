---
title: "Como usar chaves de parâmetros do sistema"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b2a7352540456b459428dd87f6c60be0b8bc08b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-system-parameters-keys"></a>Como usar chaves de parâmetros do sistema
Os recursos do sistema expõem inúmeras métricas do sistema como recursos para ajudar os desenvolvedores a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemParameters>é uma classe que contém os valores de parâmetros de sistema e as chaves associadas aos valores — por exemplo, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> e <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Métricas de parâmetros de sistema podem ser usadas como recursos estáticos ou dinâmicos. Use um recurso dinâmico se você quiser que a métrica de parâmetro para atualizar automaticamente enquanto o aplicativo é executado; Caso contrário, use um recurso estático.  
  
> [!NOTE]
>  Recursos dinâmicos têm a palavra-chave *chave* acrescentado ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar recursos dinâmicos de parâmetros de sistema para estilizar ou personalizar um botão. Isso [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemplo dimensiona um botão atribuindo <xref:System.Windows.SystemParameters> valores para a largura e a altura do botão.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Consulte também  
 [Pintar uma área com um pincel de sistema](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Usar SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Usar SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
