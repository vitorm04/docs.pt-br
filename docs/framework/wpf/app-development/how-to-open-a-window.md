---
title: 'Como: abrir uma janela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 23dc74666d8f47a0fb735d96ad22ed56c96bdbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-a-window"></a><span data-ttu-id="45c4d-102">Como: abrir uma janela</span><span class="sxs-lookup"><span data-stu-id="45c4d-102">How to: Open a Window</span></span>
<span data-ttu-id="45c4d-103">Este exemplo mostra como abrir uma janela.</span><span class="sxs-lookup"><span data-stu-id="45c4d-103">This example shows how to open a window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45c4d-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45c4d-104">Example</span></span>  
 <span data-ttu-id="45c4d-105">Uma janela é aberta instanciando <xref:System.Windows.Window> e chamar o <xref:System.Windows.Window.Show%2A> método.</span><span class="sxs-lookup"><span data-stu-id="45c4d-105">A window is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.Show%2A> method.</span></span> <span data-ttu-id="45c4d-106"><xref:System.Windows.Window.Show%2A> Abre uma janela e retorna imediatamente sem esperar que a nova janela feche.</span><span class="sxs-lookup"><span data-stu-id="45c4d-106"><xref:System.Windows.Window.Show%2A> opens a window and returns immediately without waiting for the new window to close.</span></span> <span data-ttu-id="45c4d-107">Esse tipo de janela também é conhecido como um *sem janela restrita* janela e não restringe a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="45c4d-107">This type of window is also known as a *modeless* window, and doesn't restrict user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="45c4d-108">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="45c4d-108">.NET Framework Security</span></span>  
 <span data-ttu-id="45c4d-109">Criando <xref:System.Windows.Window> requer permissão para chamar métodos nativos não seguros (consulte <xref:System.Windows.Window.%23ctor%2A>).</span><span class="sxs-lookup"><span data-stu-id="45c4d-109">Instantiating <xref:System.Windows.Window> requires permission to call unsafe native methods (see <xref:System.Windows.Window.%23ctor%2A>).</span></span>
