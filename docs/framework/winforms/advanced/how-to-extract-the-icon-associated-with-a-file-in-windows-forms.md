---
title: 'Como: extrair o ícone associado a um arquivo no Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: d754dc5e8a57b3c4e2e5439bb2524a22d44813c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112548"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="e62cb-102">Como: extrair o ícone associado a um arquivo no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e62cb-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="e62cb-103">Muitos arquivos têm ícones inseridos que fornecem uma representação visual do tipo de arquivo associado.</span><span class="sxs-lookup"><span data-stu-id="e62cb-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="e62cb-104">Por exemplo, documentos do Microsoft Word contêm um ícone que os identifica como documentos do Word.</span><span class="sxs-lookup"><span data-stu-id="e62cb-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="e62cb-105">Ao exibir os arquivos em um controle de lista ou um controle de tabela, talvez você queira exibir o ícone que representa o tipo de arquivo ao lado de cada nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="e62cb-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="e62cb-106">Você pode fazer isso facilmente usando o <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> método.</span><span class="sxs-lookup"><span data-stu-id="e62cb-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e62cb-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e62cb-107">Example</span></span>  
 <span data-ttu-id="e62cb-108">O exemplo de código a seguir demonstra como extrair o ícone associado a um arquivo e exibir o nome do arquivo e seu ícone associado em um <xref:System.Windows.Forms.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="e62cb-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e62cb-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e62cb-109">Compiling the Code</span></span>  
 <span data-ttu-id="e62cb-110">Para compilar o exemplo:</span><span class="sxs-lookup"><span data-stu-id="e62cb-110">To compile the example:</span></span>  
  
-   <span data-ttu-id="e62cb-111">Cole o código anterior em um formulário do Windows e chamar o `ExtractAssociatedIconExample` método de construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="e62cb-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="e62cb-112">Você precisará certificar-se de que seu formulário importa o <xref:System.IO> namespace.</span><span class="sxs-lookup"><span data-stu-id="e62cb-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e62cb-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e62cb-113">See also</span></span>

- [<span data-ttu-id="e62cb-114">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="e62cb-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="e62cb-115">Controle ListView</span><span class="sxs-lookup"><span data-stu-id="e62cb-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
