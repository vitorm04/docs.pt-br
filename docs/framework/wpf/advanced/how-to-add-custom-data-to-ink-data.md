---
title: 'Como: Adicionar dados personalizados aos dados de tinta'
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: 7c59a205df5358daec101339cc6a308c8e38a9d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640864"
---
# <a name="how-to-add-custom-data-to-ink-data"></a><span data-ttu-id="11417-102">Como: Adicionar dados personalizados aos dados de tinta</span><span class="sxs-lookup"><span data-stu-id="11417-102">How to: Add Custom Data to Ink Data</span></span>
<span data-ttu-id="11417-103">Você pode adicionar dados personalizados à tinta que serão salvos quando a tinta for salva no formato de tinta serializada (ISF).</span><span class="sxs-lookup"><span data-stu-id="11417-103">You can add custom data to ink that will be saved when the ink is saved as ink serialized format (ISF).</span></span>  <span data-ttu-id="11417-104">Você pode salvar os dados personalizados para o <xref:System.Windows.Ink.DrawingAttributes>, o <xref:System.Windows.Ink.StrokeCollection>, ou o <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="11417-104">You can save the custom data to the <xref:System.Windows.Ink.DrawingAttributes>, the <xref:System.Windows.Ink.StrokeCollection>, or the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="11417-105">Ser capaz de salvar os dados personalizados em três objetos lhe permite decidir o melhor local para salvá-los.</span><span class="sxs-lookup"><span data-stu-id="11417-105">Being able to save custom data on three objects gives you the ability to decide the best place to save the data.</span></span>  <span data-ttu-id="11417-106">Todas as três classes usam métodos similares para armazenar e acessar dados personalizados.</span><span class="sxs-lookup"><span data-stu-id="11417-106">All three classes use similar methods to store and access custom data.</span></span>  
  
 <span data-ttu-id="11417-107">Somente os seguintes tipos podem ser salvos como dados personalizados:</span><span class="sxs-lookup"><span data-stu-id="11417-107">Only the following types can be saved as custom data:</span></span>  
  
- <xref:System.Boolean>  
  
- <span data-ttu-id="11417-108"><xref:System.Boolean>[]</span><span class="sxs-lookup"><span data-stu-id="11417-108"><xref:System.Boolean>[]</span></span>  
  
- <xref:System.Byte>  
  
- <span data-ttu-id="11417-109"><xref:System.Byte>[]</span><span class="sxs-lookup"><span data-stu-id="11417-109"><xref:System.Byte>[]</span></span>  
  
- <xref:System.Char>  
  
- <span data-ttu-id="11417-110"><xref:System.Char>[]</span><span class="sxs-lookup"><span data-stu-id="11417-110"><xref:System.Char>[]</span></span>  
  
- <xref:System.DateTime>  
  
- <span data-ttu-id="11417-111"><xref:System.DateTime>[]</span><span class="sxs-lookup"><span data-stu-id="11417-111"><xref:System.DateTime>[]</span></span>  
  
- <xref:System.Decimal>  
  
- <span data-ttu-id="11417-112"><xref:System.Decimal>[]</span><span class="sxs-lookup"><span data-stu-id="11417-112"><xref:System.Decimal>[]</span></span>  
  
- <xref:System.Double>  
  
- <span data-ttu-id="11417-113"><xref:System.Double>[]</span><span class="sxs-lookup"><span data-stu-id="11417-113"><xref:System.Double>[]</span></span>  
  
- <xref:System.Int16>  
  
- <span data-ttu-id="11417-114"><xref:System.Int16>[]</span><span class="sxs-lookup"><span data-stu-id="11417-114"><xref:System.Int16>[]</span></span>  
  
- <xref:System.Int32>  
  
- <span data-ttu-id="11417-115"><xref:System.Int32>[]</span><span class="sxs-lookup"><span data-stu-id="11417-115"><xref:System.Int32>[]</span></span>  
  
- <xref:System.Int64>  
  
- <span data-ttu-id="11417-116"><xref:System.Int64>[]</span><span class="sxs-lookup"><span data-stu-id="11417-116"><xref:System.Int64>[]</span></span>  
  
- <xref:System.Single>  
  
- <span data-ttu-id="11417-117"><xref:System.Single>[]</span><span class="sxs-lookup"><span data-stu-id="11417-117"><xref:System.Single>[]</span></span>  
  
- <xref:System.String>  
  
- <xref:System.UInt16>  
  
- <span data-ttu-id="11417-118"><xref:System.UInt16>[]</span><span class="sxs-lookup"><span data-stu-id="11417-118"><xref:System.UInt16>[]</span></span>  
  
- <xref:System.UInt32>  
  
- <span data-ttu-id="11417-119"><xref:System.UInt32>[]</span><span class="sxs-lookup"><span data-stu-id="11417-119"><xref:System.UInt32>[]</span></span>  
  
- <xref:System.UInt64>  
  
- <span data-ttu-id="11417-120"><xref:System.UInt64>[]</span><span class="sxs-lookup"><span data-stu-id="11417-120"><xref:System.UInt64>[]</span></span>  
  
## <a name="example"></a><span data-ttu-id="11417-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="11417-121">Example</span></span>  
 <span data-ttu-id="11417-122">O exemplo a seguir demonstra como adicionar e recuperar dados personalizados de um <xref:System.Windows.Ink.StrokeCollection>.</span><span class="sxs-lookup"><span data-stu-id="11417-122">The following example demonstrates how to add and retrieve custom data from a <xref:System.Windows.Ink.StrokeCollection>.</span></span>  
  
 [!code-csharp[HowToAddCustomDataToInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 <span data-ttu-id="11417-123">O exemplo a seguir cria um aplicativo que exibe um <xref:System.Windows.Controls.InkCanvas> e dois botões.</span><span class="sxs-lookup"><span data-stu-id="11417-123">The following example creates an application that displays an <xref:System.Windows.Controls.InkCanvas> and two buttons.</span></span>  <span data-ttu-id="11417-124">O botão, `switchAuthor`, permite que duas canetas sejam usadas por dois autores diferentes.</span><span class="sxs-lookup"><span data-stu-id="11417-124">The button, `switchAuthor`, enables two pens to be used by two different authors.</span></span>  <span data-ttu-id="11417-125">O botão `changePenColors` altera a cor de cada traço no <xref:System.Windows.Controls.InkCanvas> acordo com o autor.</span><span class="sxs-lookup"><span data-stu-id="11417-125">The button `changePenColors` changes the color of each stroke on the <xref:System.Windows.Controls.InkCanvas> according to the author.</span></span>  <span data-ttu-id="11417-126">O aplicativo define dois <xref:System.Windows.Ink.DrawingAttributes> objetos e adiciona uma propriedade personalizada para cada um que indica qual autor criou o <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="11417-126">The application defines two <xref:System.Windows.Ink.DrawingAttributes> objects and adds a custom property to each one that indicates which author drew the <xref:System.Windows.Ink.Stroke>.</span></span>  <span data-ttu-id="11417-127">Quando o usuário clica em `changePenColors`, o aplicativo altera a aparência do traço de acordo com o valor da propriedade personalizada.</span><span class="sxs-lookup"><span data-stu-id="11417-127">When the user clicks `changePenColors`, the application changes the appearance of the stroke according to the value of the custom property.</span></span>  
  
 [!code-xaml[HowToAddCustomDataToInk#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
