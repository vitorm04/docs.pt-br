---
title: Propriedade de eixo descendente XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 6040401ce3e98c835677be3c4cc7698013348f37
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703772"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Propriedade de eixo descendente XML (Visual Basic)
Fornece acesso aos descendentes dos seguintes: uma <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>Partes  
 `object`  
 Necessário. Uma <xref:System.Xml.Linq.XElement> objeto, um <xref:System.Xml.Linq.XDocument> objeto, uma coleção de <xref:System.Xml.Linq.XElement> objetos ou uma coleção de <xref:System.Xml.Linq.XDocument> objetos.  
  
 ...<  
 Necessário. Indica o início de uma propriedade de eixo descendente.  
  
 `descendant`  
 Necessário. Nome de nós descendentes para acessar, do formulário [`prefix``:`]`name`.  
  
|Parte|Descrição|  
|----------|-----------------|  
|`prefix`|Opcional. Prefixo de namespace XML para o nó descendente. Deve ser um namespace XML global que é definido usando um `Imports` instrução.|  
|`name`|Necessário. Nome local do nó descendente. Ver [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Necessário. Indica o início de uma propriedade de eixo descendente.  
  
## <a name="return-value"></a>Valor de retorno  
 Uma coleção de objetos <xref:System.Xml.Linq.XElement> .  
  
## <a name="remarks"></a>Comentários  
 Você pode usar uma propriedade de eixo descendente XML para acessar nós descendentes pelo nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objetos. Use o XML `Value` propriedade para acessar o valor do primeiro nó descendente na coleção retornada. Para obter mais informações, consulte [propriedade do valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 O compilador do Visual Basic converte propriedades de eixo descendente em chamadas para o <xref:System.Xml.Linq.XContainer.Descendants%2A> método.  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 O nome em uma propriedade de eixo descendente pode usar somente namespaces XML declarados globalmente com o `Imports` instrução. Ele não é possível usar namespaces XML declarados localmente em literais de elemento XML. Para obter mais informações, consulte [instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como acessar o valor do primeiro nó descendente chamado `name` e os valores de todos os nós descendentes chamados `phone` do `contacts` objeto.  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 Esse código exibe o texto a seguir:  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML. Ele usa o prefixo de namespace para criar um literal XML e acessar o valor do primeiro nó filho com o nome qualificado `ns:name`.  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 Esse código exibe o texto a seguir:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>  
 [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/index.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
