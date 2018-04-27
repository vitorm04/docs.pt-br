---
title: Literal CDATA XML (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8dfc091409e060e20970b0b6d6bc19b4fc2aeea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-cdata-literal-visual-basic"></a>Literal CDATA XML (Visual Basic)
Um valor literal que representa um <xref:System.Xml.Linq.XCData> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Partes  
 `<![CDATA[`  
 Necessário. Indica o início da seção CDATA do XML.  
  
 `content`  
 Necessário. Conteúdo de texto seja exibido na seção CDATA do XML.  
  
 `]]>`  
 Necessário. Indica o fim da seção.  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XCData>.  
  
## <a name="remarks"></a>Comentários  
 Seções XML CDATA contêm texto não processado que deve ser incluído, mas não analisado, com o XML que o contém. Uma seção CDATA XML pode conter qualquer texto. Isso inclui caracteres XML reservados. Seção XML CDATA termina com a sequência "]] >". Isso implica que os seguintes pontos:  
  
-   Você não pode usar uma expressão inserida em um literal XML CDATA porque os delimitadores de expressão inserida são conteúdo XML CDATA válido.  
  
-   Seções XML CDATA não podem ser aninhadas, porque `content` não pode conter o valor "]] >".  
  
 Você pode atribuir um literal XML CDATA a uma variável ou incluí-lo em um literal de elemento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas, mas não usa caracteres de continuação de linha. Isso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.  
  
 O compilador do Visual Basic converte o literal XML CDATA para uma chamada para o <xref:System.Xml.Linq.XCData.%23ctor%2A> construtor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma seção CDATA que contém o texto "pode conter literal \<XML > marcas".  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XCData>  
 [Literal do Elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
