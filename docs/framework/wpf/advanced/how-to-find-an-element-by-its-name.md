---
title: Como localizar um elemento pelo nome
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
helpviewer_keywords: elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 62e5cc9c65afe9da9c77d06c103e99d3ff8d995a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a>Como localizar um elemento pelo nome
Este exemplo descreve como usar o <xref:System.Windows.FrameworkElement.FindName%2A> método para encontrar um elemento por seu <xref:System.Windows.FrameworkElement.Name%2A> valor.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, o método para localizar um elemento específico por seu nome é gravada como o manipulador de eventos de um botão. `stackPanel`é o <xref:System.Windows.FrameworkElement.Name%2A> da raiz <xref:System.Windows.FrameworkElement> está sendo pesquisada, e o método exemplo então visualmente indica o elemento encontrado convertendo-o como <xref:System.Windows.Controls.TextBlock> e alterar um do <xref:System.Windows.Controls.TextBlock> visível [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] propriedades.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
