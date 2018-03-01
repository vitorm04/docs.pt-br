---
title: Como usar SystemParameters
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ec333fbc30374ff6f8e2e7674ab332644ff7aad0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-systemparameters"></a>Como usar SystemParameters
Este exemplo mostra como acessar e usar as propriedades de <xref:System.Windows.SystemParameters> para estilizar ou personalizar um botão.  
  
## <a name="example"></a>Exemplo  
 Os recursos do sistema expõem várias configurações baseadas no sistema como recursos para ajudá-lo a criar recursos visuais consistentes com as configurações do sistema. <xref:System.Windows.SystemParameters>é uma classe que contém propriedades de valor de parâmetro do sistema e as chaves associadas aos valores. Por exemplo, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> é um <xref:System.Windows.SystemParameters> o valor da propriedade e <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> é a chave de recurso correspondente.  
  
 Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], você pode usar os membros de <xref:System.Windows.SystemParameters> como o uso de uma propriedade estática ou uma referência de recurso dinâmico (com o valor da propriedade estática como a chave). Use uma referência de recurso dinâmico se desejar que o valor baseado no sistema seja atualizado automaticamente enquanto o aplicativo é executado; caso contrário, use uma referência estática. Chaves de recurso têm o sufixo `Key` acrescentado ao nome da propriedade.  
  
 O exemplo a seguir mostra como acessar e usar os valores estáticos de <xref:System.Windows.SystemParameters> para estilizar ou personalizar um botão. Este exemplo de marcação dimensiona um botão aplicando <xref:System.Windows.SystemParameters> valores a um botão.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Para usar os valores de <xref:System.Windows.SystemParameters> no código, você não precisa usar referências estáticas ou referências a recursos dinâmicos. Em vez disso, use os valores de <xref:System.Windows.SystemParameters> classe. Embora as propriedades não-chave sejam aparentemente definidas como propriedades estáticas, o comportamento de tempo de execução de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como hospedado pelo sistema irá reavaliar as propriedades em tempo real e será corretamente a conta para alterações de valores do sistema controlada pelo usuário. O exemplo a seguir mostra como definir a largura e altura de um botão usando <xref:System.Windows.SystemParameters> valores.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.SystemParameters>  
 [Pintar uma área com um pincel de sistema](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Usar SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Usar chaves de parâmetros do sistema](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
