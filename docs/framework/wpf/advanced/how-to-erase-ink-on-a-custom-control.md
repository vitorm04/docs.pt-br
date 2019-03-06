---
title: 'Como: Apagar tinta em um controle personalizado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 60e2af64cb0c5b313f4f1201cab70da6a88f61e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365887"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>Como: Apagar tinta em um controle personalizado
O <xref:System.Windows.Ink.IncrementalStrokeHitTester> determina se o traço desenhado atualmente intersecciona outro traço.  Isso é útil para criar um controle que permite que um usuário apagar partes de um traço, a maneira como um usuário pode em uma <xref:System.Windows.Controls.InkCanvas> quando o <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> é definido como <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um controle personalizado que permite que o usuário apagar parte de traços.  Este exemplo cria um controle que contém a tinta quando ele é inicializado.  Para criar um controle que coleta tinta, consulte [criando um controle de entrada de tinta](creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
