---
title: "Criando o documento do código-fonte Office Open XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 23511c4f083dca41c7d1b1302d11dc8b75f974cb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017


---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="ccb29-102">Criando o documento do código-fonte Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccb29-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="ccb29-103">Este tópico mostra como criar o documento do Office Open XML WordprocessingML que os outros exemplos neste tutorial uso.</span><span class="sxs-lookup"><span data-stu-id="ccb29-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="ccb29-104">Se você segue essas declarações, a saída corresponderão a saída fornecida em cada exemplo.</span><span class="sxs-lookup"><span data-stu-id="ccb29-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="ccb29-105">No entanto, os exemplos neste tutorial funcionarão com qualquer documento válido de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="ccb29-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="ccb29-106">Para criar o documento que usa este tutorial, você deve ter o Microsoft Office 2007 ou posterior instalado, ou você deve ter o Microsoft Office 2003 com o pacote de compatibilidade do Microsoft Office para Word, Excel e PowerPoint 2007 File Formats.</span><span class="sxs-lookup"><span data-stu-id="ccb29-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="ccb29-107">Criando o documento de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ccb29-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="ccb29-108">Para criar o documento de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="ccb29-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="ccb29-109">Crie um novo documento Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="ccb29-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="ccb29-110">Cole o seguinte texto no novo documento:</span><span class="sxs-lookup"><span data-stu-id="ccb29-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="ccb29-111">Formatar a primeira linha com o estilo que dirige “1 ".</span><span class="sxs-lookup"><span data-stu-id="ccb29-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="ccb29-112">Selecione as linhas que contêm o código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ccb29-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="ccb29-113">A primeira linha começa com a palavra-chave `Imports` .</span><span class="sxs-lookup"><span data-stu-id="ccb29-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="ccb29-114">A última linha é "End Class".</span><span class="sxs-lookup"><span data-stu-id="ccb29-114">The last line is "End Class".</span></span> <span data-ttu-id="ccb29-115">Formatar as linhas com a fonte de correio.</span><span class="sxs-lookup"><span data-stu-id="ccb29-115">Format the lines with the courier font.</span></span> <span data-ttu-id="ccb29-116">Formatar-los com um novo estilo, e nomeie o novo estilo “código”.</span><span class="sxs-lookup"><span data-stu-id="ccb29-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="ccb29-117">Finalmente, selecione a linha inteira que contém a saída, e formatar-la com o estilo de `Code` .</span><span class="sxs-lookup"><span data-stu-id="ccb29-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="ccb29-118">Salve o documento, e denomine-o SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="ccb29-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ccb29-119">Se você estiver usando o Microsoft Word 2003, selecione **documento do Word 2007** no **Salvar como tipo** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="ccb29-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb29-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccb29-120">See Also</span></span>  
 [<span data-ttu-id="ccb29-121">Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccb29-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
