---
title: "Regiões no GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0525e7b58353909d41e5367aa52a17aa56bcd77c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="regions-in-gdi"></a>Regiões no GDI+
Uma região é uma parte da área de exibição de um dispositivo de saída. Regiões podem ser simples (um único retângulo) ou complexas (uma combinação de polígonos e curvas fechadas). A ilustração a seguir mostra duas regiões: uma construída com base em um retângulo e outra construída com base em um demarcador.  
  
 ![Regiões](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>Usando regiões  
 Regiões geralmente são usadas para recortes e testes de clique. Recorte significa restringir o desenho a uma determinada região da área de exibição, geralmente a parte que precisa ser atualizada. Testes de cliques significam verificar para determinar se o cursor está em uma determinada região da tela quando um botão do mouse é pressionado.  
  
 Você pode construir uma região com base em um retângulo ou um demarcador. Você também pode criar regiões complexas combinando regiões existentes. O <xref:System.Drawing.Region> classe fornece os seguintes métodos para a combinação de regiões: <xref:System.Drawing.Region.Intersect%2A>, <xref:System.Drawing.Region.Union%2A>, <xref:System.Drawing.Region.Xor%2A>, <xref:System.Drawing.Region.Exclude%2A>, e <xref:System.Drawing.Region.Complement%2A>.  
  
 A interseção de duas regiões é o conjunto de todos os pontos que pertencem a ambas as regiões. A união é o conjunto de todos os pontos que pertencem a uma, outra ou ambas as regiões. O complemento de uma região é o conjunto de todos os pontos que não estão na região. A ilustração a seguir mostra a interseção e união das duas regiões mostradas na ilustração anterior.  
  
 ![Regiões](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 O <xref:System.Drawing.Region.Xor%2A> método, aplicado a um par de regiões, gera uma região que contém todos os pontos que pertencem a uma região ou o outro, mas não ambos. O <xref:System.Drawing.Region.Exclude%2A> método, aplicado a um par de regiões, gera uma região que contém todos os pontos na primeira região que não estão na segunda região. A ilustração a seguir mostra as regiões resultantes da aplicação de <xref:System.Drawing.Region.Xor%2A> e <xref:System.Drawing.Region.Exclude%2A> métodos para duas regiões mostrados no início deste tópico.  
  
 ![Regiões](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 Para preencher uma região, é necessário um <xref:System.Drawing.Graphics> objeto, um <xref:System.Drawing.Brush> objeto e um <xref:System.Drawing.Region> objeto. O <xref:System.Drawing.Graphics> objeto fornece o <xref:System.Drawing.Graphics.FillRegion%2A> método e o <xref:System.Drawing.Brush> objeto armazena atributos de preenchimento, como cor ou o padrão. O exemplo a seguir preenche uma região com uma cor sólida.  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Linhas, Curvas e Formas](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Usando regiões](../../../../docs/framework/winforms/advanced/using-regions.md)
