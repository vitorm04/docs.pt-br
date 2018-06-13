---
title: Como adicionar dados personalizados aos dados de tinta
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: 40d883f3d3e1d504c8757c31325aa72a03da37e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544505"
---
# <a name="how-to-add-custom-data-to-ink-data"></a>Como adicionar dados personalizados aos dados de tinta
Você pode adicionar dados personalizados à tinta que serão salvos quando a tinta for salva no formato de tinta serializada (ISF).  Você pode salvar os dados personalizados para o <xref:System.Windows.Ink.DrawingAttributes>, o <xref:System.Windows.Ink.StrokeCollection>, ou o <xref:System.Windows.Ink.Stroke>.  Ser capaz de salvar os dados personalizados em três objetos lhe permite decidir o melhor local para salvá-los.  Todas as três classes usam métodos similares para armazenar e acessar dados personalizados.  
  
 Somente os seguintes tipos podem ser salvos como dados personalizados:  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>[]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>[]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>[]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>[]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>[]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>[]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>[]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>[]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>[]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>[]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>[]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>[]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>[]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como adicionar e recuperar dados personalizados de um <xref:System.Windows.Ink.StrokeCollection>.  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 O exemplo a seguir cria um aplicativo que exibe um <xref:System.Windows.Controls.InkCanvas> e dois botões.  O botão, `switchAuthor`, permite que duas canetas sejam usadas por dois autores diferentes.  Botão `changePenColors` altera a cor de cada traço no <xref:System.Windows.Controls.InkCanvas> acordo com o autor.  O aplicativo define dois <xref:System.Windows.Ink.DrawingAttributes> objetos e adiciona uma propriedade personalizada para cada um que indica qual o autor desenhou o <xref:System.Windows.Ink.Stroke>.  Quando o usuário clica em `changePenColors`, o aplicativo altera a aparência do traço de acordo com o valor da propriedade personalizada.  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
