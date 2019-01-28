---
title: Criando o documento do Office Open XML de origem (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 0fe5463ae95374542482f768eee2bc694e2c5dd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635839"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="fd1e0-102">Criando o documento do Office Open XML de origem (C#)</span><span class="sxs-lookup"><span data-stu-id="fd1e0-102">Creating the Source Office Open XML Document (C#)</span></span>
<span data-ttu-id="fd1e0-103">Este tópico mostra como criar o documento do Office Open XML WordprocessingML que os outros exemplos neste tutorial uso.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="fd1e0-104">Se você segue essas declarações, a saída corresponderão a saída fornecida em cada exemplo.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="fd1e0-105">No entanto, os exemplos neste tutorial funcionarão com qualquer documento válido de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="fd1e0-106">Para criar o documento que este tutorial usa, você precisa ter o Microsoft Office 2007 ou posterior instalado ou precisa ter o Microsoft Office 2003 com o Microsoft Office Compatibility Pack para formatos de arquivo do Word, Excel e PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="fd1e0-107">Criando o documento de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="fd1e0-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="fd1e0-108">Para criar o documento de WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="fd1e0-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="fd1e0-109">Crie um novo documento Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="fd1e0-110">Cole o seguinte texto no novo documento:</span><span class="sxs-lookup"><span data-stu-id="fd1e0-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    using System;  
  
    class Program {  
        public static void Main(string[] args) {  
            Console.WriteLine("Hello World");  
        }  
    }  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="fd1e0-111">Formatar a primeira linha com o estilo que dirige “1 ".</span><span class="sxs-lookup"><span data-stu-id="fd1e0-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="fd1e0-112">Selecione as linhas que contêm o código em c.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="fd1e0-113">A primeira linha começa com a palavra-chave `using` .</span><span class="sxs-lookup"><span data-stu-id="fd1e0-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="fd1e0-114">A última linha é a chave da última.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-114">The last line is the last closing brace.</span></span> <span data-ttu-id="fd1e0-115">Formatar as linhas com a fonte de correio.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-115">Format the lines with the courier font.</span></span> <span data-ttu-id="fd1e0-116">Formatar-los com um novo estilo, e nomeie o novo estilo “código”.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="fd1e0-117">Finalmente, selecione a linha inteira que contém a saída, e formatar-la com o estilo de `Code` .</span><span class="sxs-lookup"><span data-stu-id="fd1e0-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="fd1e0-118">Salve o documento, e denomine-o SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd1e0-119">Se você estiver usando o Microsoft Word 2003, selecione **Documento do Word 2007** na lista suspensa **Salvar como tipo**.</span><span class="sxs-lookup"><span data-stu-id="fd1e0-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd1e0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd1e0-120">See also</span></span>

- [<span data-ttu-id="fd1e0-121">Tutorial: manipulando conteúdo em um documento WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="fd1e0-121">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
