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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 928a3c34836464e7603c485b64c9c426913ae7b2
ms.lasthandoff: 03/13/2017


---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Criando o documento do código-fonte Office Open XML (Visual Basic)
Este tópico mostra como criar o documento do Office Open XML WordprocessingML que os outros exemplos neste tutorial uso. Se você segue essas declarações, a saída corresponderão a saída fornecida em cada exemplo.  
  
 No entanto, os exemplos neste tutorial funcionarão com qualquer documento válido de WordprocessingML.  
  
 Para criar o documento que usa este tutorial, você deve ter o Microsoft Office 2007 ou posterior instalado, ou você deve ter o Microsoft Office 2003 com o pacote de compatibilidade do Microsoft Office para Word, Excel e PowerPoint 2007 File Formats.  
  
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
    >  Se você estiver usando o Microsoft Word 2003, selecione **documento do Word 2007** no **Salvar como tipo** lista suspensa.  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
