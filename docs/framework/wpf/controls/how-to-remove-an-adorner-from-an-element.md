---
title: Como remover um adorno de um elemento
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
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe11dc8df1a29518ba05792877bd26670f96b29d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Como remover um adorno de um elemento
Este exemplo mostra como remover programaticamente um adorno de um <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo de código detalhado remove o primeiro adorno na matriz de adornos retornado por <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Este exemplo acontece recupera os adornos em um <xref:System.Windows.UIElement> chamado *myTextBox*.  Se o elemento especificado na chamada para <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> sem adorners, `null` será retornado.  Esse código verifica explicitamente uma matriz nula e é mais adequado para aplicativos em que se espera uma matriz nula relativamente comum.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo de código condensada é funcionalmente equivalente ao exemplo detalhado mostrado acima. Esse código não verifica explicitamente um array nulo, portanto, é possível que um <xref:System.NullReferenceException> exceção poderá ser gerada.  Esse código é mais adequado para aplicativos em que se espera uma matriz nula rara.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de adornos](../../../../docs/framework/wpf/controls/adorners-overview.md)
