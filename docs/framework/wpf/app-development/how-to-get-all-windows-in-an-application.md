---
title: 'Como: obter todos os Windows em um aplicativo'
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
helpviewer_keywords: window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fdb1baad8b779b6ef0443a05e5f6575b552b1c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a>Como: obter todos os Windows em um aplicativo
Este exemplo mostra como obter todos os <xref:System.Windows.Window> objetos em um aplicativo.  
  
## <a name="example"></a>Exemplo  
 Cada instanciado <xref:System.Windows.Window> do objeto, se estiver visível ou não, é adicionado automaticamente a uma coleção de referências de janela que é gerenciado pelo <xref:System.Windows.Application>e exposta de <xref:System.Windows.Application.Windows%2A>.  
  
 Você pode enumerar <xref:System.Windows.Application.Windows%2A> para obter todas as instâncias de windows usando o seguinte código:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
