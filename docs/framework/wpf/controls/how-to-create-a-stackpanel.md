---
title: 'Como: Criar um StackPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
ms.openlocfilehash: bcf6decff2fbc012b5f8b62794f0d7b2cd9f29fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121804"
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="b7ac5-102">Como: Criar um StackPanel</span><span class="sxs-lookup"><span data-stu-id="b7ac5-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="b7ac5-103">Este exemplo mostra como criar um <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7ac5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7ac5-104">Example</span></span>  
 <span data-ttu-id="b7ac5-105">Um <xref:System.Windows.Controls.StackPanel> permite empilhar elementos em uma direção especificada.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="b7ac5-106">Usando as propriedades que são definidas em <xref:System.Windows.Controls.StackPanel>, o conteúdo pode fluir tanto verticalmente, que é a configuração padrão, ou horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="b7ac5-107">O exemplo a seguir verticalmente pilhas cinco <xref:System.Windows.Controls.TextBlock> controles, cada um com outro <xref:System.Windows.Controls.Border> e <xref:System.Windows.Controls.Border.Background%2A>, usando <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="b7ac5-108">Os elementos filho que não têm nenhum especificada <xref:System.Windows.FrameworkElement.Width%2A> ser esticada para preencher a janela pai; no entanto, os elementos filho que têm um especificado <xref:System.Windows.FrameworkElement.Width%2A>, são centralizadas dentro da janela.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="b7ac5-109">A direção da pilha padrão em um <xref:System.Windows.Controls.StackPanel> é vertical.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="b7ac5-110">Para o controle de fluxo de conteúdo em um <xref:System.Windows.Controls.StackPanel>, use o <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="b7ac5-111">Você pode controlar o alinhamento horizontal usando o <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b7ac5-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7ac5-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7ac5-112">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- [<span data-ttu-id="b7ac5-113">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="b7ac5-113">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="b7ac5-114">Tópicos explicativos </span><span class="sxs-lookup"><span data-stu-id="b7ac5-114">How-to Topics</span></span>](stackpanel-how-to-topics.md)
