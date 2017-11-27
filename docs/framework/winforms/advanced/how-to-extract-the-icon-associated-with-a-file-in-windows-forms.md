---
title: "Como extrair o ícone associado a um arquivo no Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 69999e598bfc57278c1793d3cc82e0055026267d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="24b87-102">Como extrair o ícone associado a um arquivo no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24b87-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="24b87-103">Muitos arquivos têm ícones inseridos que fornecem uma representação visual do tipo de arquivo associado.</span><span class="sxs-lookup"><span data-stu-id="24b87-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="24b87-104">Por exemplo, documentos do Microsoft Word contêm um ícone que os identifica como documentos do Word.</span><span class="sxs-lookup"><span data-stu-id="24b87-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="24b87-105">Ao exibir os arquivos em um controle de lista ou um controle de tabela, talvez você queira exibir o ícone que representa o tipo de arquivo ao lado de cada nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="24b87-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="24b87-106">Você pode fazer isso facilmente usando o <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> método.</span><span class="sxs-lookup"><span data-stu-id="24b87-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b87-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24b87-107">Example</span></span>  
 <span data-ttu-id="24b87-108">O exemplo de código a seguir demonstra como extrair o ícone associado a um arquivo e exibir o nome do arquivo e o ícone associado um <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="24b87-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24b87-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="24b87-109">Compiling the Code</span></span>  
 <span data-ttu-id="24b87-110">Para compilar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="24b87-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="24b87-111">Cole o código anterior em um formulário do Windows e chame o `ExtractAssociatedIconExample` método de construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="24b87-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="24b87-112">Você precisará certificar-se de que o formulário importa o <xref:System.IO> namespace.</span><span class="sxs-lookup"><span data-stu-id="24b87-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b87-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24b87-113">See Also</span></span>  
 [<span data-ttu-id="24b87-114">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="24b87-114">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="24b87-115">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="24b87-115">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
