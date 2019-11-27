---
title: Operador GetXmlNamespace
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353187"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>Operador GetXmlNamespace (Visual Basic)
Obtém o objeto de <xref:System.Xml.Linq.XNamespace> que corresponde ao prefixo de namespace XML especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Partes  
 `xmlNamespacePrefix`  
 Opcional. A cadeia de caracteres que identifica o prefixo do namespace XML. Se fornecido, essa cadeia de caracteres deve ser um identificador XML válido. Para obter mais informações, consulte [nomes de elementos XML declarados e atributos](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Se nenhum prefixo for especificado, o namespace padrão será retornado. Se nenhum namespace padrão for especificado, o namespace vazio será retornado.  
  
## <a name="return-value"></a>Valor retornado  
 O objeto <xref:System.Xml.Linq.XNamespace> que corresponde ao prefixo de namespace XML.  
  
## <a name="remarks"></a>Comentários  
 O operador `GetXmlNamespace` Obtém o objeto <xref:System.Xml.Linq.XNamespace> que corresponde ao prefixo do namespace XML `xmlNamespacePrefix`.  
  
 Você pode usar prefixos de namespace XML diretamente em literais XML e propriedades de eixo XML. No entanto, você deve usar o operador `GetXmlNamespace` para converter um prefixo de namespace em um objeto <xref:System.Xml.Linq.XNamespace> antes de poder usá-lo em seu código. Você pode acrescentar um nome de elemento não qualificado a um objeto <xref:System.Xml.Linq.XNamespace> para obter um objeto <xref:System.Xml.Linq.XName> totalmente qualificado, que muitos métodos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] exigem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir importa `ns` como um prefixo de namespace XML. Em seguida, ele usa o prefixo do namespace para criar um literal XML e acessar o primeiro nó filho que tem o nome qualificado `ns:phone`. Em seguida, ele passa esse nó filho para a sub-rotina `ShowName`, que constrói um nome qualificado usando o operador `GetXmlNamespace`. Em seguida, a sub-rotina `ShowName` passa o nome qualificado para o método <xref:System.Xml.Linq.XNode.Ancestors%2A> para obter o nó pai `ns:contact`.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Quando você chama `TestGetXmlNamespace.RunSample()`, ele exibe uma caixa de mensagem que contém o seguinte texto:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Consulte também

- [Instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Acessando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
