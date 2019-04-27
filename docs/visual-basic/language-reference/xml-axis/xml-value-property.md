---
title: Propriedade do valor XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 1c7aa1cc32bc1c5ef637f7a606db7e695f1dfaee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799158"
---
# <a name="xml-value-property-visual-basic"></a>Propriedade do valor XML (Visual Basic)
Fornece acesso ao valor do primeiro elemento de uma coleção de <xref:System.Xml.Linq.XElement> objetos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`object`|Necessário. Coleção de objetos <xref:System.Xml.Linq.XElement>.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um `String` que contém o valor do primeiro elemento da coleção, ou `Nothing` se a coleção está vazia.  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.Xml.Linq.XElement.Value%2A> propriedade torna mais fácil acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos. Essa propriedade primeiro verifica se a coleção contém pelo menos um objeto. Se a coleção está vazia, essa propriedade retornará `Nothing`. Caso contrário, essa propriedade retorna o valor da <xref:System.Xml.Linq.XElement.Value%2A> propriedade do primeiro elemento na coleção.  
  
> [!NOTE]
>  Quando você acessa o valor de um atributo XML usando o '\@' identificador, o valor do atributo é retornado como um `String` e você não precisa especificar explicitamente o <xref:System.Xml.Linq.XAttribute.Value%2A> propriedade.  
  
 Para acessar outros elementos em uma coleção, você pode usar a propriedade do indexador de extensão XML. Para obter mais informações, consulte [propriedade do indexador de extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Herança  
 A maioria dos usuários não precisará implementar <xref:System.Collections.Generic.IEnumerable%601>e, portanto, pode ignorar esta seção.  
  
 O <xref:System.Xml.Linq.XElement.Value%2A> propriedade é uma propriedade de extensão para tipos que implementam `IEnumerable(Of XElement)`. A associação dessa propriedade de extensão é como a associação de métodos de extensão: se um tipo implementa uma das interfaces e define uma propriedade que tem o nome "Valor", essa propriedade tem precedência sobre a propriedade de extensão. Em outras palavras, isso <xref:System.Xml.Linq.XElement.Value%2A> propriedade pode ser substituída, definindo uma nova propriedade em uma classe que implementa `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o <xref:System.Xml.Linq.XElement.Value%2A> propriedade para acessar o primeiro nó em uma coleção de <xref:System.Xml.Linq.XElement> objetos. O exemplo usa a propriedade de eixo filho para obter a coleção de todos os nós filho denominado `phone` que estão no `contact` objeto.  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 Esse código exibe o texto a seguir:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de <xref:System.Xml.Linq.XAttribute> objetos. O exemplo usa a propriedade de eixo de atributo para exibir o valor da `type` atributo para todos os `phone` elementos.  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 Esse código exibe o texto a seguir:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Propriedade do Indexador de Extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [Propriedade do Eixo Filho XML](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [Propriedade de Eixo do Atributo XML](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
