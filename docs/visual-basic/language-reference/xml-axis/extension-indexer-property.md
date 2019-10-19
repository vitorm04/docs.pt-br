---
title: Propriedade do indexador de extensão (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 660cebadc78d260350f2849f7f4926f9cef7c8d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582191"
---
# <a name="extension-indexer-property-visual-basic"></a>Propriedade do indexador de extensão (Visual Basic)
Fornece acesso aos elementos individuais em uma coleção.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`object`|Necessário. Uma coleção passível de consulta. Ou seja, uma coleção que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.|  
|(|Necessário. Denota o início da Propriedade do indexador.|  
|`index`|Necessário. Uma expressão de inteiro que especifica a posição de base zero de um elemento da coleção.|  
|)|Necessário. Denota o final da Propriedade do indexador.|  
  
## <a name="return-value"></a>Valor retornado  
 O objeto do local especificado na coleção ou `Nothing` se o índice está fora do intervalo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a propriedade do indexador de extensão para acessar elementos individuais em uma coleção. Essa propriedade do indexador normalmente é usada na saída das propriedades do eixo XML. As propriedades do eixo XML filho e do XML descendente retornam coleções de objetos <xref:System.Xml.Linq.XElement> ou um valor de atributo.  
  
 O compilador Visual Basic converte Propriedades do indexador de extensão em chamadas para o método `ElementAtOrDefault`. Ao contrário de um indexador de matriz, o método `ElementAtOrDefault` retornará `Nothing` se o índice estiver fora do intervalo. Esse comportamento é útil quando você não pode determinar facilmente o número de elementos em uma coleção.  
  
 Essa propriedade do indexador é como uma propriedade de extensão para coleções que implementam <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>: ela será usada somente se a coleção não tiver um indexador ou uma propriedade padrão.  
  
 Para acessar o valor do primeiro elemento em uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, você pode usar a propriedade XML `Value`. Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o indexador de extensão para acessar o segundo nó filho em uma coleção de objetos de <xref:System.Xml.Linq.XElement>. A coleção é acessada usando a propriedade do eixo filho, que obtém todos os elementos filho chamados `phone` no objeto `contact`.  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Esse código exibe o seguinte texto:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement>
- [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Propriedade do Valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
