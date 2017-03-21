---
title: "Propriedade do indexador de extensão (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
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
ms.openlocfilehash: 25f434a5b5f8caf013ad5f778897e4e98e3d825d
ms.lasthandoff: 03/13/2017

---
# <a name="extension-indexer-property-visual-basic"></a>Propriedade do indexador de extensão (Visual Basic)
Fornece acesso aos elementos individuais em uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object(index)  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`object`|Necessário. Uma coleção consultável. Ou seja, uma coleção que implementa <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>|  
|(|Necessário. Indica o início da propriedade do indexador.|  
|`index`|Necessário. Uma expressão de inteiro que especifica a posição de um elemento da coleção baseada em zero.|  
|)|Necessário. Indica o fim da propriedade do indexador.|  
  
## <a name="return-value"></a>Valor de retorno  
 O objeto do local especificado na coleção, ou `Nothing` se o índice está fora do intervalo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a propriedade do indexador de extensão para acessar elementos individuais em uma coleção. Esta propriedade do indexador normalmente é usada na saída das propriedades do eixo XML. O filho do XML e propriedades de eixo descendente XML retornam coleções de <xref:System.Xml.Linq.XElement>objetos ou um valor de atributo.</xref:System.Xml.Linq.XElement>  
  
 O [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador converte propriedades do indexador de extensão para chamadas para o`ElementAtOrDefault` método. Ao contrário de um indexador de matriz, o`ElementAtOrDefault` método retorna `Nothing` se o índice está fora do intervalo. Esse comportamento é útil quando você não consegue determinar o número de elementos em uma coleção.  
  
 Esta propriedade do indexador é como uma propriedade de extensão para coleções que implementam <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>: ele é usado somente se a coleção não possui um indexador ou uma propriedade padrão.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 Para acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>objetos, você pode usar o XML `Value` propriedade.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o indexador de extensão para acessar o segundo nó filho em uma coleção de <xref:System.Xml.Linq.XElement>objetos.</xref:System.Xml.Linq.XElement> A coleção é acessada usando a propriedade de eixo filho, que obtém todos os elementos filho chamados `phone` no `contact` objeto.  
  
 [!code-vb[VbXMLSamples&#24;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Esse código exibe o seguinte texto:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>   
 [Propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Propriedade do Valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
