---
title: Propriedade do eixo filho XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dadb21f4985497a90cc62f98c5fb2abdd7cc2781
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-child-axis-property-visual-basic"></a>Propriedade do eixo filho XML (Visual Basic)
Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
object.<child>  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`object`|Necessário. Um <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.|  
|.<|Necessário. Indica o início de uma propriedade de eixo filho.|  
|`child`|Necessário. Nome de nós filho para acessar, no formato [`prefix``:`]`name`.<br /><br /> -   `Prefix` -Opcional. Prefixo de namespace XML para o nó filho. Deve ser um namespace XML global definido com um `Imports` instrução.<br />-   `Name` -Necessário. Nome do nó filho local. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Necessário. Indica o início de uma propriedade de eixo filho.|  
  
## <a name="return-value"></a>Valor de retorno  
 Uma coleção de objetos <xref:System.Xml.Linq.XElement> .  
  
## <a name="remarks"></a>Comentários  
 Você pode usar uma propriedade de eixo filho XML para acessar os nós filho por nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objetos. Use o XML `Value` propriedade para acessar o valor do primeiro nó filho na coleção retornada. Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 O compilador do Visual Basic converte propriedades de eixo filho em chamadas para o <xref:System.Xml.Linq.XContainer.Elements%2A> método.  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 O nome em uma propriedade de eixo filho pode usar somente prefixos de namespace XML declarados globalmente com a `Imports` instrução. Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML. Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como acessar os nós filho chamados `phone` do `contact` objeto.  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 Este código exibe o seguinte texto:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pelo `contact` propriedade de eixo filho do `contacts` objeto.  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 Este código exibe o seguinte texto:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML. Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 Este código exibe o seguinte texto:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>  
 [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
