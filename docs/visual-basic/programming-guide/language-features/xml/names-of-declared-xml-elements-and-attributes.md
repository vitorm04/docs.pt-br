---
title: Nomes de elementos e atributos XML declarados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals [Visual Basic]
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
ms.openlocfilehash: 9b586936281bfbf2dcace7cf2892bebf305fc842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650420"
---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nomes de elementos e atributos XML declarados (Visual Basic)
Este tópico fornece diretrizes de Visual Basic para nomes de elementos XML e atributos em literais XML.  Em um literal XML, você pode especificar um nome local ou um nome qualificado. Um nome qualificado consiste de um prefixo de namespace XML, dois-pontos e um nome local. Para obter mais informações sobre prefixos de namespace XML, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Regras  
 Um nome de local de um elemento ou atributo no Visual Basic deve seguir as regras a seguir.  
  
-   Ele pode começar com um namespace. Ele deve começar com um caractere alfabético ou sublinhado (`_`).  
  
-   Ela deve conter apenas caracteres alfabéticos, dígitos decimais, sublinhados, pontos (.) e hifens (-).  
  
-   Ele não deve ter mais de 1.024 caracteres.  
  
-   Dois-pontos aparecem em nomes indicam demarcação de namespace. Portanto, você pode usar dois-pontos somente para especificar um namespace XML para um determinado nome.  
  
 Além disso, você deve seguir as diretrizes a seguir.  
  
-   A especificação XML 1.0 se reserva todos os nomes que começam com a cadeia de caracteres "xml", de qualquer variação de maiusculas e minúsculas. Portanto, não use esses nomes para o elemento e nomes de atributo.  
  
### <a name="name-length-guidelines"></a>Diretrizes para comprimento de nome  
 De forma prática, um nome deve ser tão curto quanto possível e ainda identificar claramente a natureza do elemento. Isso melhora a legibilidade do código e reduz o tamanho de arquivo de origem e de comprimento de linha.  
  
 No entanto, o nome não deve ser tão curto que ele não descreve adequadamente o elemento ou como seu código usa. Isso é importante para a legibilidade do código. Se alguém está tentando compreendê-la, ou se você mesmo o está examinando muito tempo depois que você o escreveu, nomes de elemento apropriado podem economizar tempo.  
  
## <a name="case-sensitivity-in-names"></a>Diferenciação de maiusculas e minúsculas em nomes  
 Nomes de elemento XML diferenciam maiusculas de minúsculas. Isso significa que quando o compilador do Visual Basic compara dois nomes que diferem apenas caso alfabética, ele interpreta como nomes diferentes. Por exemplo, ele interpreta `ABC` e `abc` como referência para separar elementos.  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 Ao criar um elemento XML literal, você pode especificar o prefixo de namespace XML para o nome do elemento. Para obter mais informações, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Literal do Elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
