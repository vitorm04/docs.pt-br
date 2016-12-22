---
title: "Como: transmitir fragmentos XML de um XmlReader (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: transmitir fragmentos XML de um XmlReader (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você precisa processar grandes arquivos XML, não é possível carregar a árvore inteira XML na memória. Este tópico mostra como transmitir fragmentos usando um <xref:System.Xml.XmlReader>.  
  
 Uma das maneiras mais eficazes para usar um <xref:System.Xml.XmlReader> ler <xref:System.Xml.Linq.XElement> objetos é escrever seu próprio método personalizado do eixo. Um método do eixo normalmente retorna uma coleção, como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, conforme mostrado no exemplo neste tópico. No método personalizado do eixo, depois de criar o fragmento XML chamando o <xref:System.Xml.Linq.XNode.ReadFrom%2A> método, retornar a coleção usando `yield return`. Isso fornece a semântica de execução adiada ao método personalizado do eixo.  
  
 Quando você cria uma árvore XML de uma <xref:System.Xml.XmlReader> objeto, o <xref:System.Xml.XmlReader> deve ser posicionado em um elemento. O <xref:System.Xml.Linq.XNode.ReadFrom%2A> método não retorna até que ele tenha lido a marca de fechamento do elemento.  
  
 Se você quiser criar uma árvore parcial, você pode instanciar um <xref:System.Xml.XmlReader>, posicione o leitor no nó que você deseja converter em um <xref:System.Xml.Linq.XElement> de árvore e, em seguida, crie o <xref:System.Xml.Linq.XElement> objeto.  
  
 O tópico [Como: transmitir fragmentos XML com acesso a informações de cabeçalho \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contém informações e um exemplo de como passar um documento mais complexo.  
  
 O tópico [Como: executar o Streaming de transformação de grandes documentos XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contém um exemplo de como usar LINQ to XML para transformar documentos XML muito grandes, mantendo uma pegada pequena de memória.  
  
## Exemplo  
 Este exemplo cria um método personalizado do eixo. Você pode consultá\-lo usando um [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consulta. O método personalizado do eixo, `StreamRootChildDoc`, é um método que foi projetado especificamente para ler um documento que tem uma repetição `Child` elemento.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Este exemplo produz a seguinte saída:  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Neste exemplo, o documento de origem é muito pequeno. No entanto, mesmo se houvesse milhões de `Child` elementos, este exemplo ainda teria uma pegada pequena de memória.  
  
## Consulte também  
 [Instruções passo a passo: implementando IEnumerable\(Of T\) no Visual Basic](../../../../visual-basic/programming-guide/language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)   
 [Análise de XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)