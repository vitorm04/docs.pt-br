---
title: Como remover todos os adornos de um elemento
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
helpviewer_keywords: adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f7bb16c2cd641579706609ff14ca16cc57bd620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>Como remover todos os adornos de um elemento
Este exemplo mostra como remover todos os adornos de especificada programaticamente <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo de código detalhado remove todos os adornos na matriz de adornos retornado por <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Este exemplo acontece recupera os adornos em um <xref:System.Windows.UIElement> chamado *myTextBox*.  Se o elemento especificado na chamada para <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> sem adorners, `null` será retornado.  Esse código verifica explicitamente uma matriz nula e é mais adequado para aplicativos em que se espera uma matriz nula relativamente comum.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo de código condensada é funcionalmente equivalente ao exemplo detalhado mostrado acima. Esse código não verifica explicitamente um array nulo, portanto, é possível que um <xref:System.NullReferenceException> exceção poderá ser gerada.  Esse código é mais adequado para aplicativos em que se espera uma matriz nula rara.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de adornos](../../../../docs/framework/wpf/controls/adorners-overview.md)
