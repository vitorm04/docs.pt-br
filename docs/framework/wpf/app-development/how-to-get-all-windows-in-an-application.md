---
title: 'Como: Obter todas as janelas em um aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 34316f0c6f81b960a8e00131a30b9a237b9ca938
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947765"
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="ca11c-102">Como: Obter todas as janelas em um aplicativo</span><span class="sxs-lookup"><span data-stu-id="ca11c-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="ca11c-103">Este exemplo mostra como obter todos os <xref:System.Windows.Window> objetos em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca11c-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca11c-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ca11c-104">Example</span></span>  
 <span data-ttu-id="ca11c-105">Cada instanciados <xref:System.Windows.Window> do objeto, se estiver visível ou não, é adicionado automaticamente a uma coleção de referências de janela que é gerenciado pelo <xref:System.Windows.Application>e exposta do <xref:System.Windows.Application.Windows%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca11c-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="ca11c-106">Você pode enumerar <xref:System.Windows.Application.Windows%2A> para obter todas as instâncias de windows usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="ca11c-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
