---
title: 'Como: Criar um StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: 46b037e3f1626e77a61dca787b705a63ccd28ba0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360428"
---
# <a name="how-to-create-a-stackpanel"></a>Como: Criar um StackPanel
Este exemplo mostra como criar um <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Exemplo  
 Um <xref:System.Windows.Controls.StackPanel> permite empilhar elementos em uma direção especificada. Usando as propriedades que são definidas em <xref:System.Windows.Controls.StackPanel>, o conteúdo pode fluir tanto verticalmente, que é a configuração padrão, ou horizontalmente.  
  
 O exemplo a seguir verticalmente pilhas cinco <xref:System.Windows.Controls.TextBlock> controles, cada um com outro <xref:System.Windows.Controls.Border> e <xref:System.Windows.Controls.Border.Background%2A>, usando <xref:System.Windows.Controls.StackPanel>. Os elementos filho que não têm nenhum especificada <xref:System.Windows.FrameworkElement.Width%2A> ser esticada para preencher a janela pai; no entanto, os elementos filho que têm um especificado <xref:System.Windows.FrameworkElement.Width%2A>, são centralizadas dentro da janela.  
  
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
- <xref:System.Windows.Controls.StackPanel>
- [Visão geral de painéis](panels-overview.md)
- [Tópicos de instruções](stackpanel-how-to-topics.md)
