---
title: Propriedade de valor XML (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionValue
dev_langs:
- VB
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: 18
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
ms.openlocfilehash: 7f4d8dd3a403434fa1a3018be59be33bbd21dc26
ms.lasthandoff: 03/13/2017

---
# <a name="xml-value-property-visual-basic"></a>Propriedade do valor XML (Visual Basic)
Fornece acesso ao valor do primeiro elemento de uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement>  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.Value  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`object`|Necessário. Coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement>|  
  
## <a name="return-value"></a>Valor de retorno  
 A `String` que contém o valor do primeiro elemento da coleção, ou `Nothing` se a coleção estiver vazia.  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.Xml.Linq.XElement.Value%2A>propriedade torna mais fácil acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Value%2A> Essa propriedade primeiro verifica se a coleção contém pelo menos um objeto. Se a coleção está vazia, essa propriedade retornará `Nothing`. Caso contrário, essa propriedade retorna o valor de <xref:System.Xml.Linq.XElement.Value%2A>propriedade do primeiro elemento na coleção.</xref:System.Xml.Linq.XElement.Value%2A>  
  
> [!NOTE]
>  Quando você acessa o valor de um atributo XML usando o ' @' identificador, o valor do atributo é retornado como um `String` e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A>propriedade.</xref:System.Xml.Linq.XAttribute.Value%2A>  
  
 Para acessar outros elementos em uma coleção, você pode usar a propriedade do indexador de extensão XML. Para obter mais informações, consulte [propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Herança  
 A maioria dos usuários não precisará implementar <xref:System.Collections.Generic.IEnumerable%601>e, portanto, pode ignorar esta seção.</xref:System.Collections.Generic.IEnumerable%601>  
  
 O <xref:System.Xml.Linq.XElement.Value%2A>propriedade é uma propriedade de extensão para tipos que implementam `IEnumerable(Of XElement)`.</xref:System.Xml.Linq.XElement.Value%2A> A vinculação da propriedade extensão é como a associação de métodos de extensão: se um tipo implementa uma das interfaces e define uma propriedade que tem o nome "Valor", essa propriedade tem precedência sobre a propriedade de extensão. Em outras palavras, isso <xref:System.Xml.Linq.XElement.Value%2A>propriedade pode ser substituída ao definir uma nova propriedade em uma classe que implementa `IEnumerable(Of XElement)`.</xref:System.Xml.Linq.XElement.Value%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o <xref:System.Xml.Linq.XElement.Value%2A>propriedade para acessar o primeiro nó em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Value%2A> O exemplo usa a propriedade do eixo filho para obter a coleção de todos os nós filho chamados `phone` que estão na `contact` objeto.  
  
 [!code-vb[VbXMLSamples&#15;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de <xref:System.Xml.Linq.XAttribute>objetos.</xref:System.Xml.Linq.XAttribute> O exemplo usa a propriedade de eixo de atributo para exibir o valor da `type` atributo para todos os o `phone` elementos.  
  
 [!code-vb[VbXMLSamples n º&16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)   
 [Propriedade de eixo filho XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)   
 [Propriedade de Eixo do Atributo XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
