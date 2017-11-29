---
title: "Propriedade do indexador de extensão (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
|`object`|Necessário. Uma coleção passível de consulta. Ou seja, uma coleção que implementa <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.|  
|(|Necessário. Indica o início da propriedade do indexador.|  
|`index`|Necessário. Uma expressão de inteiro que especifica a posição de base zero de um elemento da coleção.|  
|)|Necessário. Indica o fim da propriedade do indexador.|  
  
## <a name="return-value"></a>Valor de retorno  
 O objeto do local especificado na coleção, ou `Nothing` se o índice está fora do intervalo.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a propriedade do indexador de extensão para acessar elementos individuais em uma coleção. Esta propriedade do indexador normalmente é usada na saída das propriedades do eixo XML. O filho do XML e propriedades de eixo descendente XML retornam coleções de <xref:System.Xml.Linq.XElement> objetos ou um valor de atributo.  
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte propriedades do indexador de extensão para chamadas para o `ElementAtOrDefault` método. Ao contrário de um indexador de matriz, o `ElementAtOrDefault` método retorna `Nothing` se o índice está fora do intervalo. Esse comportamento é útil quando você não consegue determinar o número de elementos em uma coleção.  
  
 Esta propriedade do indexador é como uma propriedade de extensão para coleções que implementam <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>: ele é usado somente se a coleção não possui um indexador ou uma propriedade padrão.  
  
 Para acessar o valor do primeiro elemento em uma coleção de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> objetos, você pode usar o XML `Value` propriedade. Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o indexador de extensão para acessar o segundo nó filho em uma coleção de <xref:System.Xml.Linq.XElement> objetos. A coleção é acessada usando a propriedade de eixo filho, que obtém todos os elementos filho denominados `phone` no `contact` objeto.  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Este código exibe o seguinte texto:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XElement>  
 [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Propriedade do Valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
