---
title: 'Como: transmitir fragmentos XML de um XmlReader (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c9c60bb4730ef6569390f76f63c40a2cbd1c9524
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a>Como: transmitir fragmentos XML de um XmlReader (Visual Basic)
Quando você tem que processa grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória. Este tópico mostra como transmitir fragmentos usando um <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>  
  
 Uma das maneiras mais eficazes para usar um <xref:System.Xml.XmlReader>ler <xref:System.Xml.Linq.XElement>objetos é escrever seu próprio método personalizado do eixo.</xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader> Um método do eixo normalmente retorna uma coleção, como <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>, conforme mostrado no exemplo neste tópico.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> No método personalizado do eixo, depois de criar o fragmento XML chamando o <xref:System.Xml.Linq.XNode.ReadFrom%2A>método, retornar a coleção usando `yield return`.</xref:System.Xml.Linq.XNode.ReadFrom%2A> Isso fornece a semântica de execução adiada ao método personalizado do eixo.  
  
 Quando você cria uma árvore XML de uma <xref:System.Xml.XmlReader>objeto, o <xref:System.Xml.XmlReader>deve ser posicionado em um elemento.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> O <xref:System.Xml.Linq.XNode.ReadFrom%2A>método não retorna até que ele tenha lido a marca de fechamento do elemento.</xref:System.Xml.Linq.XNode.ReadFrom%2A>  
  
 Se você quiser criar uma árvore parcial, você pode instanciar um <xref:System.Xml.XmlReader>, posicione o leitor no nó que você deseja converter em um <xref:System.Xml.Linq.XElement>de árvore e, em seguida, crie o <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> </xref:System.Xml.XmlReader>  
  
 O tópico [como: transmitir fragmentos XML com acesso a informações de cabeçalho (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contém informações e um exemplo de como passar um documento mais complexo.  
  
 O tópico [como: realizar Streaming de transformação de documentos XML extensos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contém um exemplo de como usar LINQ to XML para transformar documentos XML muito grandes, mantendo uma pegada pequena de memória.  
  
## <a name="example"></a>Exemplo  
 Este exemplo cria um método personalizado do eixo. Você pode consultá-lo usando um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta. O método personalizado do eixo, `StreamRootChildDoc`, é um método que foi projetado especificamente para ler um documento que tem uma repetição `Child` elemento.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Este exemplo gera a seguinte saída:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Nesse exemplo, o documento de origem é muito pequeno. No entanto, mesmo se houver milhões de elementos de `Child` , este exemplo ainda terá uma pegada pequena de memória.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Implementando IEnumerable(Of T) no Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)   
 [Análise de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
