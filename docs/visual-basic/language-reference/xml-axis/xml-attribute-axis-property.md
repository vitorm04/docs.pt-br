---
title: Propriedade de eixo de atributo XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
dev_langs:
- VB
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
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
ms.openlocfilehash: 94211f7c951976426ba17e73df214444a6c227b4
ms.lasthandoff: 03/13/2017

---
# <a name="xml-attribute-axis-property-visual-basic"></a>Propriedade de eixo do atributo XML (Visual Basic)
Fornece acesso ao valor de um atributo para um <xref:System.Xml.Linq.XElement>objeto ou para o primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Partes  
 `object`  
 Necessário. Um <xref:System.Xml.Linq.XElement>objeto ou uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement>  
  
 .@  
 Necessário. Indica o início de uma propriedade de eixo de atributo.  
  
 <  
 Opcional. Indica o início do nome do atributo quando `attribute` não é um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 `attribute`  
 Necessário. Nome do atributo para acessar, do formulário [`prefix`:]`name`.  
  
|Parte|Descrição|  
|----------|-----------------|  
|`prefix`|Opcional. Prefixo de namespace XML para o atributo. Deve ser um namespace XML global definido com um `Imports` instrução.|  
|`name`|Necessário. Nome do atributo local. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Opcional. Indica o fim do nome do atributo quando `attribute` não é um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="return-value"></a>Valor de retorno  
 Uma cadeia de caracteres que contém o valor de `attribute`. Se não existir, o nome do atributo `Nothing` é retornado.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar uma propriedade de eixo de atributo XML para acessar o valor de um atributo pelo nome de uma <xref:System.Xml.Linq.XElement>objeto ou do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement> Você pode recuperar um valor de atributo pelo nome, ou adicionar um novo atributo a um elemento, especificando um novo nome precedido de @ identificador.  
  
 Quando você se referir a um atributo XML usando o @ identificador, o valor do atributo é retornado como uma cadeia de caracteres e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A>propriedade.</xref:System.Xml.Linq.XAttribute.Value%2A>  
  
 As regras de nomeação para XML atributos diferem das regras de nomeação de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identificadores. Para acessar um atributo XML que tem um nome que não é um identificador válido Visual Basic, coloque o nome entre colchetes angulares (\< e >).  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 O nome em uma propriedade de eixo de atributo pode usar somente prefixos de namespace XML declarados globalmente usando o `Imports` instrução. Ele não é possível usar prefixos de namespace XML declarados localmente em literais de elemento XML. Para obter mais informações, consulte [instrução Imports (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter os valores dos atributos XML chamados `type` de uma coleção de elementos XML que são nomeados `phone`.  
  
 [!code-vb[VbXMLSamples&#12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar atributos para um elemento XML tanto declarativamente, como parte do XML e dinamicamente adicionando um atributo a uma instância de um <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement> O `type` atributo é criado declarativamente e o `owne`r atributo é criado dinamicamente.  
  
 [!code-vb[VbXMLSamples&#44;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 Esse código exibe o seguinte texto:  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a sintaxe de colchete angular para obter o valor de atributo XML chamado `number-type`, que não é um identificador válido no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [!code-vb[VbXMLSamples&13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `Phone type: work`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML. Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado "`ns:name`".  
  
 [!code-vb[VbXMLSamples&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
