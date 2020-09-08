---
title: Criar o documento Office Open XML de origem-LINQ to XML
description: Saiba como criar o documento do Office Open XML WordprocessingML usado pelos outros exemplos neste tutorial.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: b3401d7309879661dcfc7062418ee75430dccf35
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551829"
---
# <a name="create-the-source-office-open-xml-document-linq-to-xml"></a><span data-ttu-id="f0c81-103">Criar o documento Office Open XML de origem (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f0c81-103">Create the source Office Open XML document (LINQ to XML)</span></span>

<span data-ttu-id="f0c81-104">Este artigo mostra como criar o documento do Office Open XML WordprocessingML usado pelos outros exemplos neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="f0c81-104">This article shows how to create the Office Open XML WordprocessingML document used by the other examples in this tutorial.</span></span> <span data-ttu-id="f0c81-105">Se você segue essas declarações, a saída corresponderão a saída fornecida em cada exemplo.</span><span class="sxs-lookup"><span data-stu-id="f0c81-105">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="f0c81-106">No entanto, os exemplos neste tutorial funcionarão com qualquer documento válido de WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="f0c81-106">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="f0c81-107">Para criar o documento que este tutorial usa, você precisa ter o Microsoft Office 2007 ou posterior instalado ou precisa ter o Microsoft Office 2003 com o Microsoft Office Compatibility Pack para formatos de arquivo do Word, Excel e PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="f0c81-107">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="create-the-wordprocessingml-document"></a><span data-ttu-id="f0c81-108">Criar o documento do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="f0c81-108">Create the WordprocessingML document</span></span>

<span data-ttu-id="f0c81-109">Use as seguintes etapas para criar o documento do WordprocessingML:</span><span class="sxs-lookup"><span data-stu-id="f0c81-109">Use the following steps to create the WordprocessingML document:</span></span>

1. <span data-ttu-id="f0c81-110">Crie um novo documento Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="f0c81-110">Create a new Microsoft Word document.</span></span>
1. <span data-ttu-id="f0c81-111">Cole o texto a seguir no novo documento.</span><span class="sxs-lookup"><span data-stu-id="f0c81-111">Paste the following text into the new document.</span></span>
   1. <span data-ttu-id="f0c81-112">Para o C#, use este texto:</span><span class="sxs-lookup"><span data-stu-id="f0c81-112">For C#, use this text:</span></span>

         ```text
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

   1. <span data-ttu-id="f0c81-113">Para Visual Basic, use este texto:</span><span class="sxs-lookup"><span data-stu-id="f0c81-113">For Visual Basic, use this text:</span></span>

      ```text
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

1. <span data-ttu-id="f0c81-114">Formatar a primeira linha com o estilo que dirige “1 ".</span><span class="sxs-lookup"><span data-stu-id="f0c81-114">Format the first line with the style "Heading 1".</span></span>
1. <span data-ttu-id="f0c81-115">Para C#, selecione as linhas que contêm o código C#.</span><span class="sxs-lookup"><span data-stu-id="f0c81-115">For C#, select the lines that contain the C# code.</span></span> <span data-ttu-id="f0c81-116">A primeira linha começa com a palavra-chave `using` .</span><span class="sxs-lookup"><span data-stu-id="f0c81-116">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="f0c81-117">A última linha é a chave da última.</span><span class="sxs-lookup"><span data-stu-id="f0c81-117">The last line is the last closing brace.</span></span> <span data-ttu-id="f0c81-118">Formatar as linhas com a fonte de correio.</span><span class="sxs-lookup"><span data-stu-id="f0c81-118">Format the lines with the courier font.</span></span> <span data-ttu-id="f0c81-119">Formatar-los com um novo estilo, e nomeie o novo estilo “código”.</span><span class="sxs-lookup"><span data-stu-id="f0c81-119">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="f0c81-120">Para Visual Basic, selecione as linhas que contêm o código de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f0c81-120">For Visual Basic, select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="f0c81-121">A primeira linha começa com a palavra-chave `Imports` .</span><span class="sxs-lookup"><span data-stu-id="f0c81-121">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="f0c81-122">A última linha é "End Class".</span><span class="sxs-lookup"><span data-stu-id="f0c81-122">The last line is "End Class".</span></span> <span data-ttu-id="f0c81-123">Formatar as linhas com a fonte de correio.</span><span class="sxs-lookup"><span data-stu-id="f0c81-123">Format the lines with the courier font.</span></span> <span data-ttu-id="f0c81-124">Formatar-los com um novo estilo, e nomeie o novo estilo “código”.</span><span class="sxs-lookup"><span data-stu-id="f0c81-124">Format them with a new style, and name the new style "Code".</span></span>
1. <span data-ttu-id="f0c81-125">Finalmente, selecione a linha inteira que contém a saída, e formatar-la com o estilo de `Code` .</span><span class="sxs-lookup"><span data-stu-id="f0c81-125">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>
1. <span data-ttu-id="f0c81-126">Salve o documento, e denomine-o SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="f0c81-126">Save the document, and name it SampleDoc.docx.</span></span>

> [!NOTE]
> <span data-ttu-id="f0c81-127">Se você estiver usando o Microsoft Word 2003, selecione **documento do word 2007** na lista suspensa **salvar como tipo** .</span><span class="sxs-lookup"><span data-stu-id="f0c81-127">If you're using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0c81-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0c81-128">See also</span></span>

- [<span data-ttu-id="f0c81-129">Tutorial: manipular conteúdo em um documento do WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="f0c81-129">Tutorial: Manipulate content in a WordprocessingML document</span></span>](xml-shape-wordprocessingml-documents.md)
