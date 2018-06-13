---
title: Como buscar um relógio de forma síncrona
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], seeking synchronously
- seeking clocks synchronously [WPF]
ms.assetid: e5b7529b-b7d0-40d2-9e1d-fa4b5e736e96
ms.openlocfilehash: d8e7b0f4bfa3a59814d87bfb6d7e8b40bd80f6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559845"
---
# <a name="how-to-seek-a-clock-synchronously"></a>Como buscar um relógio de forma síncrona
Use o <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> método para procurar um relógio para um ponto específico de forma síncrona. O exemplo a seguir demonstra ambos o <xref:System.Windows.Media.Animation.ClockController.Seek%2A> e <xref:System.Windows.Media.Animation.ClockController.SeekAlignedToLastTick%2A> métodos de um <xref:System.Windows.Media.Animation.ClockController>.  
  
 Este exemplo mostra como buscar uma <xref:System.Windows.Media.Animation.Clock>; para obter um exemplo mostrando como procurar um storyboard, consulte [seguir um Storyboard sincronamente](../../../../docs/framework/wpf/graphics-multimedia/how-to-seek-a-storyboard-synchronously.md) .  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClockController_procedural_snip/CSharp/SeekAlignedToLastTickExample.cs#clockcontrollerseekexample)]
 [!code-vb[ClockController_procedural_snip#ClockControllerSeekExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClockController_procedural_snip/visualbasic/seekalignedtolasttickexample.vb#clockcontrollerseekexample)]
