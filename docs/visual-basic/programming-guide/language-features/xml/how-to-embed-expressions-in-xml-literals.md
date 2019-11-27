---
title: Como inserir expressões em literais XML
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332937"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>Como inserir expressões em literais XML (Visual Basic)
Você pode combinar literais XML com expressões inseridas para criar um documento XML, fragmento ou elemento que contém o conteúdo criado em tempo de execução. Os exemplos a seguir demonstram como usar expressões inseridas para popular o conteúdo do elemento, os atributos e os nomes de elementos em tempo de execução.  
  
 A sintaxe de uma expressão inserida é `<%=` `exp` `%>`, que é a mesma sintaxe que o ASP.NET usa. Para obter mais informações, consulte [expressões inseridas em XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Você também pode usar as APIs de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos. Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.  
  
## <a name="procedures"></a>Procedimentos  
  
#### <a name="to-insert-text-as-element-content"></a>Para inserir texto como conteúdo do elemento  
  
- O exemplo a seguir mostra como inserir o texto contido na variável `contactName` entre os elementos de nome de abertura e fechamento.  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     Este exemplo gera a seguinte saída:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>Para inserir texto como um valor de atributo  
  
- O exemplo a seguir mostra como inserir o texto contido na variável `phoneType` como o valor do atributo `type`.  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     Este exemplo gera a seguinte saída:  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>Para inserir texto para um nome de elemento  
  
- O exemplo a seguir mostra como inserir o texto contido na variável `elementName` como o nome de um elemento.  
  
     Ao criar elementos usando essa técnica, você deve fechá-los com a marca \</>.  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     Este exemplo gera a seguinte saída:  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Como criar literais XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [Expressões Inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
