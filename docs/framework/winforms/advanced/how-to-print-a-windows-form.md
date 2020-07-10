---
title: Como imprimir um formulário do Windows Forms
description: Saiba como imprimir programaticamente uma cópia do Windows Form atual usando o método CopyFromScreen.
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
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174686"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="35278-103">Como imprimir um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35278-103">How to: Print a Windows Form</span></span>
<span data-ttu-id="35278-104">Como parte do processo de desenvolvimento, você normalmente desejará imprimir uma cópia do seu Windows Form.</span><span class="sxs-lookup"><span data-stu-id="35278-104">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="35278-105">O exemplo de código a seguir mostra como imprimir uma cópia do formulário atual usando o <xref:System.Drawing.Graphics.CopyFromScreen%2A> método.</span><span class="sxs-lookup"><span data-stu-id="35278-105">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35278-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35278-106">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="35278-107">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="35278-107">Robust Programming</span></span>  
 <span data-ttu-id="35278-108">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="35278-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="35278-109">Você não tem permissão para acessar a impressora.</span><span class="sxs-lookup"><span data-stu-id="35278-109">You do not have permission to access the printer.</span></span>  
  
- <span data-ttu-id="35278-110">Não há impressora instalada.</span><span class="sxs-lookup"><span data-stu-id="35278-110">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="35278-111">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="35278-111">.NET Framework Security</span></span>  
 <span data-ttu-id="35278-112">Para executar este exemplo de código, você deve ter permissão para acessar a impressora que você usa com seu computador.</span><span class="sxs-lookup"><span data-stu-id="35278-112">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35278-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="35278-113">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="35278-114">Como renderizar imagens com o GDI+</span><span class="sxs-lookup"><span data-stu-id="35278-114">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="35278-115">Como imprimir elementos gráficos no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35278-115">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
