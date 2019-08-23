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
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942987"
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
 Uma `String` que contém o valor do primeiro elemento da coleção ou `Nothing` se a coleção estiver vazia.  
  
## <a name="remarks"></a>Comentários  
 A <xref:System.Xml.Linq.XElement.Value%2A> Propriedade facilita o acesso ao valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> objetos. Essa propriedade verifica primeiro se a coleção contém pelo menos um objeto. Se a coleção estiver vazia, essa propriedade retornará `Nothing`. Caso contrário, essa propriedade retornará o valor da <xref:System.Xml.Linq.XElement.Value%2A> Propriedade do primeiro elemento na coleção.  
  
> [!NOTE]
> Quando você acessa o valor de um atributo XML usando o identificador\@' ', o valor do atributo é retornado como `String` um e você não precisa especificar explicitamente a <xref:System.Xml.Linq.XAttribute.Value%2A> propriedade.  
  
 Para acessar outros elementos em uma coleção, você pode usar a propriedade do indexador de extensão XML. Para obter mais informações, consulte Propriedade do indexador de [extensão](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Herança  
 A maioria dos usuários não precisará <xref:System.Collections.Generic.IEnumerable%601>implementar e, portanto, pode ignorar esta seção.  
  
 A <xref:System.Xml.Linq.XElement.Value%2A> propriedade é uma propriedade de extensão para tipos que `IEnumerable(Of XElement)`implementam. A associação dessa propriedade de extensão é como a associação de métodos de extensão: se um tipo implementar uma das interfaces e definir uma propriedade com o nome "valor", essa propriedade terá precedência sobre a propriedade de extensão. Em outras palavras, essa <xref:System.Xml.Linq.XElement.Value%2A> propriedade pode ser substituída definindo-se uma nova propriedade em uma classe `IEnumerable(Of XElement)`que implementa.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a <xref:System.Xml.Linq.XElement.Value%2A> propriedade para acessar o primeiro nó em uma coleção de <xref:System.Xml.Linq.XElement> objetos. O exemplo usa a propriedade do eixo filho para obter a coleção de todos os nós `phone` filho chamados que estão `contact` no objeto.  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 Esse código exibe o seguinte texto:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter o valor de um atributo XML de uma coleção de <xref:System.Xml.Linq.XAttribute> objetos. O exemplo usa a Propriedade Axis do atributo para exibir o valor do `type` atributo para todos `phone` os elementos.  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 Esse código exibe o seguinte texto:  
  
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
