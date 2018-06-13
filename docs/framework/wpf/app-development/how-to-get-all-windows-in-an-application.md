---
title: 'Como: obter todos os Windows em um aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 476905899f5f7d573a16ba876c72f28ea34bbf9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545484"
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="98c3a-102">Como: obter todos os Windows em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="98c3a-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="98c3a-103">Este exemplo mostra como obter todos os <xref:System.Windows.Window> objetos em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98c3a-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98c3a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98c3a-104">Example</span></span>  
 <span data-ttu-id="98c3a-105">Cada instanciado <xref:System.Windows.Window> do objeto, se estiver visível ou não, é adicionado automaticamente a uma coleção de referências de janela que é gerenciado pelo <xref:System.Windows.Application>e exposta de <xref:System.Windows.Application.Windows%2A>.</span><span class="sxs-lookup"><span data-stu-id="98c3a-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="98c3a-106">Você pode enumerar <xref:System.Windows.Application.Windows%2A> para obter todas as instâncias de windows usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="98c3a-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
