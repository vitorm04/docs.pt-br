---
title: 'Como: imprimir um Windows Form'
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
ms.openlocfilehash: cd10e0a43ff37b921dc8e024d7a6a51fafbb0400
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591857"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="0d597-102">Como: imprimir um Windows Form</span><span class="sxs-lookup"><span data-stu-id="0d597-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="0d597-103">Como parte do processo de desenvolvimento, você geralmente desejará imprimir uma cópia do seu Windows Form.</span><span class="sxs-lookup"><span data-stu-id="0d597-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="0d597-104">O exemplo de código a seguir mostra como imprimir uma cópia do formulário atual, usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método.</span><span class="sxs-lookup"><span data-stu-id="0d597-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d597-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d597-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0d597-106">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="0d597-106">Robust Programming</span></span>  
 <span data-ttu-id="0d597-107">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="0d597-107">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0d597-108">Você não tem permissão para acessar a impressora.</span><span class="sxs-lookup"><span data-stu-id="0d597-108">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="0d597-109">Não há nenhuma impressora instalada.</span><span class="sxs-lookup"><span data-stu-id="0d597-109">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0d597-110">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0d597-110">.NET Framework Security</span></span>  
 <span data-ttu-id="0d597-111">Para executar este exemplo de código, você deve ter permissão para acessar a impressora que você usa com o seu computador.</span><span class="sxs-lookup"><span data-stu-id="0d597-111">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d597-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d597-112">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="0d597-113">Como: Renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="0d597-113">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="0d597-114">Como: Imprimir elementos gráficos nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d597-114">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
