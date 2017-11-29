---
title: Criando um documento de origem Office Open XML (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c573f703ea3d7550dabd994f538e28e197874715
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Criando um documento de origem Office Open XML (Visual Basic)
Este tópico mostra como criar o documento do Office Open XML WordprocessingML que os outros exemplos neste tutorial uso. Se você segue essas declarações, a saída corresponderão a saída fornecida em cada exemplo.  
  
 No entanto, os exemplos neste tutorial funcionarão com qualquer documento válido de WordprocessingML.  
  
 Para criar o documento que este tutorial usa, você precisa ter o Microsoft Office 2007 ou posterior instalado ou precisa ter o Microsoft Office 2003 com o Microsoft Office Compatibility Pack para formatos de arquivo do Word, Excel e PowerPoint 2007.  
  
## <a name="creating-the-wordprocessingml-document"></a>Criando o documento de WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Para criar o documento de WordprocessingML  
  
1.  Crie um novo documento Microsoft Word.  
  
2.  Cole o seguinte texto no novo documento:  
  
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
  
3.  Formatar a primeira linha com o estilo que dirige “1 ".  
  
4.  Selecione as linhas que contêm o código do Visual Basic. A primeira linha começa com a palavra-chave `Imports` . A última linha é "End Class". Formatar as linhas com a fonte de correio. Formatar-los com um novo estilo, e nomeie o novo estilo “código”.  
  
5.  Finalmente, selecione a linha inteira que contém a saída, e formatar-la com o estilo de `Code` .  
  
6.  Salve o documento, e denomine-o SampleDoc.docx.  
  
    > [!NOTE]
    >  Se você estiver usando o Microsoft Word 2003, selecione **Documento do Word 2007** na lista suspensa **Salvar como tipo**.  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
