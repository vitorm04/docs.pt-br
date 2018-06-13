---
title: 'Como: abrir uma caixa de mensagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: dd79d69c9b1b54c5158b58ee2f1675e7d11a386a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545630"
---
# <a name="how-to-open-a-message-box"></a><span data-ttu-id="355f5-102">Como: abrir uma caixa de mensagem</span><span class="sxs-lookup"><span data-stu-id="355f5-102">How to: Open a Message Box</span></span>
<span data-ttu-id="355f5-103">Este exemplo mostra como abrir uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="355f5-103">This example shows how to open a message box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="355f5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="355f5-104">Example</span></span>  
 <span data-ttu-id="355f5-105">Uma caixa de mensagem é uma caixa de diálogo modal pré-fabricada para exibir informações aos usuários.</span><span class="sxs-lookup"><span data-stu-id="355f5-105">A message box is a prefabricated modal dialog box for displaying information to users.</span></span> <span data-ttu-id="355f5-106">Uma caixa de mensagem é aberta chamando estático <xref:System.Windows.MessageBox.Show%2A> método o <xref:System.Windows.MessageBox> classe.</span><span class="sxs-lookup"><span data-stu-id="355f5-106">A message box is opened by calling the static <xref:System.Windows.MessageBox.Show%2A> method of the <xref:System.Windows.MessageBox> class.</span></span> <span data-ttu-id="355f5-107">Quando <xref:System.Windows.MessageBox.Show%2A> é chamado, a mensagem será passada usando um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="355f5-107">When <xref:System.Windows.MessageBox.Show%2A> is called, the message is passed using a string parameter.</span></span> <span data-ttu-id="355f5-108">Várias sobrecargas de <xref:System.Windows.MessageBox.Show%2A> permitem que você configure como uma caixa de mensagem será exibida (consulte <xref:System.Windows.MessageBox>).</span><span class="sxs-lookup"><span data-stu-id="355f5-108">Several overloads of <xref:System.Windows.MessageBox.Show%2A> allow you to configure how a message box will appear (see <xref:System.Windows.MessageBox>).</span></span>  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a><span data-ttu-id="355f5-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="355f5-109">See Also</span></span>  
 [<span data-ttu-id="355f5-110">Exemplo de MessageBox</span><span class="sxs-lookup"><span data-stu-id="355f5-110">MessageBox Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160023)
