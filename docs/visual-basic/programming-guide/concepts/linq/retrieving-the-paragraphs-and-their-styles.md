---
title: "Recuperando os parágrafos e seus estilos (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bb6d68296a720a796a319502c4cb2f0319727459
ms.lasthandoff: 03/13/2017


---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a>Recuperando os parágrafos e seus estilos (Visual Basic)
Nesse exemplo, nós escrevemos uma consulta que recupera os nós de parágrafo de um documento de WordprocessingML. Também identifica o estilo de cada parágrafo.  
  
 Esta consulta compila na consulta no exemplo anterior, [localizando o estilo de parágrafo padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), que recupera o estilo padrão da lista de estilos. Essa informação é necessária de modo que a consulta pode identificar o estilo dos parágrafos que não têm um estilo definir explicitamente. Os estilos de parágrafo são definidos por meio do elemento de `w:pPr` ; se um parágrafo não contém esse elemento, é formatado com o estilo padrão.  
  
 Este tópico explica o significado de algumas partes de consulta, então mostra a consulta como parte de um exemplo completo, que funciona.  
  
## <a name="example"></a>Exemplo  
 A fonte da consulta para recuperar todos os parágrafos em um documento e seus estilos é a seguinte:  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 Esta expressão é semelhante à fonte da consulta no exemplo anterior, [localizando o estilo de parágrafo padrão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md). A principal diferença é que ele usa o <xref:System.Xml.Linq.XContainer.Descendants%2A>eixo em vez do <xref:System.Xml.Linq.XContainer.Elements%2A>eixo.</xref:System.Xml.Linq.XContainer.Elements%2A> </xref:System.Xml.Linq.XContainer.Descendants%2A> A consulta usa o <xref:System.Xml.Linq.XContainer.Descendants%2A>eixo porque em documentos que têm seções, os parágrafos não serão os filhos diretos do elemento body; em vez disso, os parágrafos serão dois níveis abaixo na hierarquia.</xref:System.Xml.Linq.XContainer.Descendants%2A> Usando o <xref:System.Xml.Linq.XContainer.Descendants%2A>eixo, o código funcionará se o documento usa seções.</xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
## <a name="example"></a>Exemplo  
 A consulta usa uma cláusula de `Let` para determinar o elemento que contém o nó de estilo. Se não houver nenhum elemento, então `styleNode` é definido como `Nothing`:  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 O `Let` cláusula primeiro usa o <xref:System.Xml.Linq.XContainer.Elements%2A>eixo para localizar todos os elementos chamados `pPr`, usa o <xref:System.Xml.Linq.Extensions.Elements%2A>método de extensão para localizar todos os elementos filho chamados `pStyle`e finalmente usa o <xref:System.Linq.Enumerable.FirstOrDefault%2A>operador de consulta padrão para converter a coleção em um singleton.</xref:System.Linq.Enumerable.FirstOrDefault%2A> </xref:System.Xml.Linq.Extensions.Elements%2A> </xref:System.Xml.Linq.XContainer.Elements%2A> Se a coleção estiver vazia, `styleNode` é definido como `Nothing`. Este é um idioma útil para procurar o nó descendente de `pStyle` . Observe que se o nó filho de `pPr` não existir, o código faz ou falhas lançando uma exceção; em vez disso, `styleNode` é definido como `Nothing`, que é o comportamento desejado desta cláusula de `Let` .  
  
 A consulta em uma coleção de um tipo anônimo com dois membros, `StyleName` e `ParagraphNode`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo processa um documento de WordprocessingML, recuperando os nós de parágrafo de um documento de WordprocessingML. Também identifica o estilo de cada parágrafo. Este exemplo cria nos exemplos anteriores neste tutorial. A nova consulta é chamada nos comentários no código a seguir.  
  
 Você pode encontrar instruções para criar o documento de origem para este exemplo em [criando o Office Open XML documento de origem (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
 Este exemplo usa as classes encontradas no assembly WindowsBase. Ele usa tipos no <xref:System.IO.Packaging?displayProperty=fullName>namespace.</xref:System.IO.Packaging?displayProperty=fullName>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 Este exemplo produz a seguinte saída quando aplicado ao documento descrito em [criando o Office Open XML documento de origem (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a>Próximas etapas  
 No próximo tópico, [recuperando o texto dos parágrafos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), você criará uma consulta para recuperar o texto dos parágrafos.  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: Manipulando conteúdo em um documento de WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
