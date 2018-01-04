---
title: 'Como: abrir uma janela'
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
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6f3efda8257d9f7ed843438b0e9fb42e13de2c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-window"></a>Como: abrir uma janela
Este exemplo mostra como abrir uma janela.  
  
## <a name="example"></a>Exemplo  
 Uma janela é aberta instanciando <xref:System.Windows.Window> e chamar o <xref:System.Windows.Window.Show%2A> método. <xref:System.Windows.Window.Show%2A>Abre uma janela e retorna imediatamente sem esperar que a nova janela feche. Esse tipo de janela também é conhecido como um *sem janela restrita* janela e não restringe a entrada do usuário.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Criando <xref:System.Windows.Window> requer permissão para chamar métodos nativos não seguros (consulte <xref:System.Windows.Window.%23ctor%2A>).
