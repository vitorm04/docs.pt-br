---
title: Como apagar tinta em um controle personalizado
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
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e05163bcbafd360e0929fe784ff1111bd0663ef3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>Como apagar tinta em um controle personalizado
O <xref:System.Windows.Ink.IncrementalStrokeHitTester> determina se o atualmente intersecta outra pincelada.  Isso é útil para criar um controle que permite que um usuário apagar partes de um traço, a maneira como um usuário pode em um <xref:System.Windows.Controls.InkCanvas> quando o <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> é definido como <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um controle personalizado que permite que o usuário apagar parte de traços.  Este exemplo cria um controle que contém tinta quando ele é inicializado.  Para criar um controle que coleta tinta, consulte [criando um controle de entrada de tinta](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
