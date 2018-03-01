---
title: Como criar um StackPanel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9226ac10e4f221cc381b7c59179b2667e20aa757
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-stackpanel"></a>Como criar um StackPanel
Este exemplo mostra como criar um <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.StackPanel> permite que a pilha de elementos em uma direção especificada. Usando propriedades que são definidas em <xref:System.Windows.Controls.StackPanel>, conteúdos podem fluir tanto verticalmente, que é a configuração padrão, ou horizontalmente.  
  
 O exemplo a seguir verticalmente pilhas cinco <xref:System.Windows.Controls.TextBlock> controla, cada um com outro <xref:System.Windows.Controls.Border> e <xref:System.Windows.Controls.Border.Background%2A>, usando <xref:System.Windows.Controls.StackPanel>. Elementos filho que não especificada têm <xref:System.Windows.FrameworkElement.Width%2A> esticada para preencher a janela pai; no entanto, os elementos filho que têm um especificado <xref:System.Windows.FrameworkElement.Width%2A>, estão centralizados na janela.  
  
 A direção da pilha padrão em um <xref:System.Windows.Controls.StackPanel> é vertical. Para o controle de fluxo de conteúdo em um <xref:System.Windows.Controls.StackPanel>, use o <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriedade. Você pode controlar o alinhamento horizontal usando o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade.  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.StackPanel>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
