---
title: Nomes de elementos XML declarados e atributos (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declarations [XML in Visual Basic]
- element names [XML in Visual Basic]
- names in XML literals
- attribute names [XML in Visual Basic]
- XML literals [Visual Basic], element names
ms.assetid: cc110118-b6cf-4ff9-a4e4-6233c90c9fbf
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ed8ecf69170acf9745a4038975e7e3421722d52d
ms.lasthandoff: 03/13/2017

---
# <a name="names-of-declared-xml-elements-and-attributes-visual-basic"></a>Nomes de elementos e atributos XML declarados (Visual Basic)
Este tópico fornece [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] diretrizes para nomear elementos XML e atributos em literais XML.  Em um literal XML, você pode especificar um nome local ou um nome qualificado. Um nome qualificado consiste de um prefixo de namespace XML, um vírgula e um nome local. Para obter mais informações sobre prefixos de namespace XML, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="rules"></a>Regras  
 Um nome de um elemento ou atributo no local [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] devem seguir as regras a seguir.  
  
-   Ele pode começar com um namespace. Ele deve começar com um caractere alfabético ou sublinhado (`_`).  
  
-   Ele deve conter apenas caracteres alfabéticos, dígitos, sublinhados, pontos (.) e hifens (-).  
  
-   Ele não deve ter mais de 1.024 caracteres.  
  
-   Vírgula, que aparecem em nomes indica demarcação de namespace. Portanto, você pode usar dois pontos somente para especificar um namespace XML para um determinado nome.  
  
 Além disso, você deve seguir as seguintes diretrizes.  
  
-   A especificação XML 1.0 se reserva todos os nomes que começam com a cadeia de caracteres "xml", de qualquer variação de maiusculas e minúsculas. Portanto, não use esses nomes para o elemento e nomes de atributo.  
  
### <a name="name-length-guidelines"></a>Diretrizes para comprimento de nome  
 De forma prática, um nome deve ser tão curto quanto possível e ainda identificar claramente a natureza do elemento. Isso melhora a legibilidade do código e reduz o tamanho de arquivo de origem e de comprimento de linha.  
  
 No entanto, o nome não deve ser tão curto que ele não descreve adequadamente o elemento ou como o código o usa. Isso é importante para a legibilidade do código. Se alguém está tentando compreendê-la, ou se você mesmo o está examinando muito tempo depois que você o escreveu, nomes de elemento apropriado podem economizar tempo.  
  
## <a name="case-sensitivity-in-names"></a>Diferenciação de maiusculas e minúsculas em nomes  
 Nomes de elemento XML diferenciam maiusculas de minúsculas. Isso significa que quando o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador compara dois nomes que diferem apenas caso alfabética, ele interpreta como diferentes nomes. Por exemplo, ele interpreta `ABC` e `abc` como referência para separar elementos.  
  
## <a name="xml-namespaces"></a>Namespaces XML  
 Ao criar um elemento XML literal, você pode especificar o prefixo de namespace XML para o nome do elemento. Para obter mais informações, consulte [o Literal de elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Literal do Elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
