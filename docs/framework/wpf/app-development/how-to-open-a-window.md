---
title: 'Como: Abrir uma janela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947667"
---
# <a name="how-to-open-a-window"></a>Como: Abrir uma janela
Este exemplo mostra como abrir uma janela.  
  
## <a name="example"></a>Exemplo  
 Uma janela é aberta pela instanciação <xref:System.Windows.Window> e chamar o <xref:System.Windows.Window.Show%2A> método. <xref:System.Windows.Window.Show%2A> Abre uma janela e retorna imediatamente sem esperar que a nova janela seja fechada. Esse tipo de janela também é conhecido como um *sem janela restrita* janela e não restringe a entrada do usuário.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Criando uma instância de <xref:System.Windows.Window> requer a permissão para chamar métodos nativos não seguros (consulte <xref:System.Windows.Window.%23ctor%2A>).
