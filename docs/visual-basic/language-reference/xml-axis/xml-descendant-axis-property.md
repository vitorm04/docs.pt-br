---
title: Propriedade de eixo descendente XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 434dc90c643381bdc27b2da54a7418e39bf15e98
ms.lasthandoff: 03/13/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a>Propriedade de eixo descendente XML (Visual Basic)
Fornece acesso aos descendentes dos seguintes: um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto, uma coleção de <xref:System.Xml.Linq.XElement>objetos ou uma coleção de <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a>Partes  
 `object`  
 Necessário. Um <xref:System.Xml.Linq.XElement>objeto, um <xref:System.Xml.Linq.XDocument>objeto, uma coleção de <xref:System.Xml.Linq.XElement>objetos ou uma coleção de <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement>  
  
 ...<  
 Necessário. Indica o início de uma propriedade de eixo descendente.  
  
 `descendant`  
 Necessário. Nome de nós descendentes a serem acessados, do formulário [`prefix``:`]`name`.  
  
|Parte|Descrição|  
|----------|-----------------|  
|`prefix`|Opcional. Prefixo de namespace XML para o nó descendente. Deve ser um namespace XML global que é definido usando um `Imports` instrução.|  
|`name`|Necessário. Nome local do nó descendente. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Necessário. Indica o início de uma propriedade de eixo descendente.  
  
## <a name="return-value"></a>Valor de retorno  
 Uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement>  
  
## <a name="remarks"></a>Comentários  
 Você pode usar uma propriedade de eixo descendente XML para acessar nós descendentes pelo nome de uma <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objeto, ou de uma coleção de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objetos.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Usar o XML `Value` propriedade para acessar o valor do primeiro nó descendente na coleção retornada. Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte as propriedades de eixo descendente em chamadas para o <xref:System.Xml.Linq.XContainer.Descendants%2A>método.</xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 O nome em uma propriedade de eixo descendente pode usar somente namespaces XML declarados globalmente com a `Imports` instrução. Ele não pode usar namespaces XML declarados localmente em literais de elemento XML. Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como acessar o valor do primeiro nó descendente chamado `name` e os valores de todos os nós descendentes chamados `phone` do `contacts` objeto.  
  
 [!code-vb[25 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML. Ele usa o prefixo de namespace para criar um literal XML e acessar o valor do primeiro nó filho com o nome qualificado `ns:name`.  
  
 [!code-vb[VbXMLSamples&#26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
