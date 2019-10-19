---
title: Propriedade do eixo filho XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 88d0b1f315bc1bb9dc474604d222a8ebcc1e40aa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582237"
---
# <a name="xml-child-axis-property-visual-basic"></a>Propriedade do eixo filho XML (Visual Basic)
Fornece acesso aos descendentes de um dos seguintes: um objeto de <xref:System.Xml.Linq.XElement> , um objeto de <xref:System.Xml.Linq.XDocument> , uma coleção de objetos <xref:System.Xml.Linq.XElement> , ou uma coleção de <xref:System.Xml.Linq.XDocument> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`object`|Necessário. Um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.|  
|. <|Necessário. Denota o início de uma propriedade de eixo filho.|  
|`child`|Necessário. Nome dos nós filho a serem acessados, no formato [`prefix:]name`.<br /><br /> -    `Prefix`-opcional. Prefixo do namespace XML para o nó filho. Deve ser um namespace XML global definido com uma instrução `Imports`.<br />-    `Name`-obrigatório. Nome do nó filho local. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Necessário. Denota o final de uma propriedade do eixo filho.|  
  
## <a name="return-value"></a>Valor retornado  
 Uma coleção de objetos <xref:System.Xml.Linq.XElement> .  
  
## <a name="remarks"></a>Comentários  
 Você pode usar uma propriedade de eixo filho XML para acessar nós filho pelo nome de um objeto <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> ou de uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>. Use a propriedade XML `Value` para acessar o valor do primeiro nó filho na coleção retornada. Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 O compilador Visual Basic converte Propriedades de eixo filho em chamadas para o método <xref:System.Xml.Linq.XContainer.Elements%2A>.  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 O nome em uma propriedade de eixo filho pode usar somente os prefixos de namespace XML declarados globalmente com a instrução `Imports`. Ele não pode usar prefixos de namespace XML declarados localmente em literais de elemento XML. Para obter mais informações, consulte [instrução Imports (namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como acessar os nós filho chamados `phone` do objeto `contact`.  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Esse código exibe o seguinte texto:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como acessar os nós filho chamados `phone` da coleção retornada pela propriedade eixo filho `contact` do objeto `contacts`.  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Esse código exibe o seguinte texto:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara `ns` como um prefixo de namespace XML. Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho com o nome qualificado `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Esse código exibe o seguinte texto:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement>
- [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
