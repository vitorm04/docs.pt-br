---
title: Propriedade de eixo descendente XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: e2c3e01808d3eeb18f6753a5fc79b8627e7f323b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582224"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Propriedade de eixo descendente XML (Visual Basic)

Fornece acesso aos descendentes dos seguintes: um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.

## <a name="syntax"></a>Sintaxe

```vb
object...<descendant>
```

## <a name="parts"></a>Partes

`object` Necessário. Um objeto <xref:System.Xml.Linq.XElement>, um objeto <xref:System.Xml.Linq.XDocument>, uma coleção de objetos <xref:System.Xml.Linq.XElement> ou uma coleção de objetos <xref:System.Xml.Linq.XDocument>.

`...<` Necessário. Denota o início de uma propriedade de eixo descendente.

`descendant` Necessário. Nome dos nós descendentes a serem acessados, no formato [`prefix:]name`.

|Parte|Descrição|
|----------|-----------------|
|`prefix`|Opcional. Prefixo do namespace XML para o nó descendente. Deve ser um namespace XML global que é definido usando uma instrução `Imports`.|
|`name`|Necessário. Nome local do nó descendente. Consulte [nomes de elementos e atributos XML declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>` Necessário. Denota o final de uma propriedade de eixo descendente.

## <a name="return-value"></a>Valor retornado

Uma coleção de objetos <xref:System.Xml.Linq.XElement> .

## <a name="remarks"></a>Comentários

Você pode usar uma propriedade de eixo descendente XML para acessar nós descendentes por nome de um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> objeto ou de uma coleção de objetos <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>. Use a propriedade XML `Value` para acessar o valor do primeiro nó descendente na coleção retornada. Para obter mais informações, consulte [propriedade de valor XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

O compilador Visual Basic converte Propriedades do eixo descendente em chamadas para o método <xref:System.Xml.Linq.XContainer.Descendants%2A>.

## <a name="xml-namespaces"></a>Namespaces XML

O nome em uma propriedade de eixo descendente pode usar somente namespaces XML declarados globalmente com a instrução `Imports`. Ele não pode usar namespaces XML declarados localmente em literais de elemento XML. Para obter mais informações, consulte [instrução Imports (namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como acessar o valor do primeiro nó descendente chamado `name` e os valores de todos os nós descendentes chamados `phone` do objeto `contacts`.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Esse código exibe o seguinte texto:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Exemplo

O exemplo a seguir declara `ns` como um prefixo de namespace XML. Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o valor do primeiro nó filho com o nome qualificado `ns:name`.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Esse código exibe o seguinte texto:

`Name: Patrick Hines`

## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement>
- [Propriedades do Eixo XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nomes de Elementos e Atributos XML Declarados](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
