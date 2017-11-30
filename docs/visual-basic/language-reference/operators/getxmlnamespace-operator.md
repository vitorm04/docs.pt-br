---
title: Operador GetXmlNamespace (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a>Operador GetXmlNamespace (Visual Basic)
Obtém o <xref:System.Xml.Linq.XNamespace> objeto correspondente para o prefixo de namespace XML especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Partes  
 `xmlNamespacePrefix`  
 Opcional. A cadeia de caracteres que identifica o prefixo de namespace XML. Se fornecido, essa cadeia de caracteres deve ser um identificador XML válido. Para obter mais informações, consulte [nomes de declarado elementos e atributos XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Se nenhum prefixo for especificado, o namespace padrão será retornado. Se nenhum namespace padrão for especificado, o namespace vazio será retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 O <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML.  
  
## <a name="remarks"></a>Comentários  
 O `GetXmlNamespace` operador obtém o <xref:System.Xml.Linq.XNamespace> objeto que corresponde ao prefixo de namespace XML `xmlNamespacePrefix`.  
  
 Você pode usar prefixos de namespace XML diretamente em literais XML e propriedades de eixo XML. No entanto, você deve usar o `GetXmlNamespace` para converter um prefixo de namespace para um <xref:System.Xml.Linq.XNamespace> objeto antes de você pode usá-lo em seu código. Você pode acrescentar um nome de elemento não qualificado para um <xref:System.Xml.Linq.XNamespace> objeto para obter um totalmente qualificado <xref:System.Xml.Linq.XName> do objeto, que muitos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] métodos requerem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir importa `ns` como um prefixo de namespace XML. Ele usa o prefixo de namespace para criar um literal XML e acessar o primeiro nó filho que tem o nome qualificado `ns:phone`. Em seguida, passar esse nó filho para o `ShowName` sub-rotina, que constrói um nome qualificado usando o `GetXmlNamespace` operador. O `ShowName` sub-rotina, em seguida, passa o nome qualificado para o <xref:System.Xml.Linq.XNode.Ancestors%2A> método para obter o pai `ns:contact` nó.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Quando você chama `TestGetXmlNamespace.RunSample()`, ele exibe uma caixa de mensagem que contém o seguinte texto:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Imports (Namespace de XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Acessando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
