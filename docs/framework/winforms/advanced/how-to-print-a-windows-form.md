---
title: 'Como: Imprimir um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 5e672f40797a90111daefed0be74c941d4cc37b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628125"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="906f6-102">Como: Imprimir um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="906f6-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="906f6-103">Como parte do processo de desenvolvimento, você geralmente desejará imprimir uma cópia do seu Windows Form.</span><span class="sxs-lookup"><span data-stu-id="906f6-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="906f6-104">O exemplo de código a seguir mostra como imprimir uma cópia do formulário atual, usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método.</span><span class="sxs-lookup"><span data-stu-id="906f6-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="906f6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="906f6-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="906f6-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="906f6-106">Compiling the Code</span></span>  
 <span data-ttu-id="906f6-107">Este é um exemplo de código completo que contém um `Main` método.</span><span class="sxs-lookup"><span data-stu-id="906f6-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="906f6-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="906f6-108">Robust Programming</span></span>  
 <span data-ttu-id="906f6-109">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="906f6-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="906f6-110">Você não tem permissão para acessar a impressora.</span><span class="sxs-lookup"><span data-stu-id="906f6-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="906f6-111">Não há nenhuma impressora instalada.</span><span class="sxs-lookup"><span data-stu-id="906f6-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="906f6-112">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="906f6-112">.NET Framework Security</span></span>  
 <span data-ttu-id="906f6-113">Para executar este exemplo de código, você deve ter permissão para acessar a impressora que você usa com o seu computador.</span><span class="sxs-lookup"><span data-stu-id="906f6-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906f6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="906f6-114">See also</span></span>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="906f6-115">Como: Renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="906f6-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
- [<span data-ttu-id="906f6-116">Como: Imprimir elementos gráficos nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="906f6-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
