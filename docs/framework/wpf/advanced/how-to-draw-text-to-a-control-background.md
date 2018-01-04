---
title: Como desenhar texto para a tela de fundo de um controle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 091be80e055279685c9dba33dd6b6635e64eaff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-to-a-control39s-background"></a>Como desenhar texto para a tela de fundo de um controle
Você pode desenhar texto diretamente para o plano de fundo de um controle ao converter uma cadeia de caracteres de texto para um <xref:System.Windows.Media.FormattedText> de objeto e, em seguida, o objeto de desenho para o controle <xref:System.Windows.Media.DrawingContext>. Você também pode usar essa técnica para desenhar o plano de fundo dos objetos derivados da <xref:System.Windows.Controls.Panel>, como <xref:System.Windows.Controls.Canvas> e <xref:System.Windows.Controls.StackPanel>.  
  
 ![Exibindo texto como plano de fundo de controles](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")  
Exemplo de controles com telas de fundo de texto personalizado  
  
## <a name="example"></a>Exemplo  
 Para desenhar o plano de fundo de um controle, crie um novo <xref:System.Windows.Media.DrawingBrush> de objeto e desenhar o texto convertido para o objeto <xref:System.Windows.Media.DrawingContext>. Em seguida, atribua o novo <xref:System.Windows.Media.DrawingBrush> a propriedade de plano de fundo do controle.  
  
 O exemplo de código a seguir mostra como criar um <xref:System.Windows.Media.FormattedText> de objeto e desenhar o plano de fundo de um <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.Button> objeto.  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.FormattedText>  
 [Desenhando texto formatado](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
