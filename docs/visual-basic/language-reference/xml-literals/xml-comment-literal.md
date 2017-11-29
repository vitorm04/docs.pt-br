---
title: "Literal de comentário XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36be34ac22cfe926a2eea946f5e4c4eb534de696
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-literal-visual-basic"></a>Literal de comentário XML (Visual Basic)
Um valor literal que representa um <xref:System.Xml.Linq.XComment> objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`<!--`|Necessário. Indica o início de comentário XML.|  
|`content`|Necessário. Texto a ser exibido no comentário XML. Não pode conter uma série de dois hifens (-) ou terminar com um hífen adjacente à marca de fechamento.|  
|`-->`|Necessário. Indica o fim do comentário XML.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XComment>.  
  
## <a name="remarks"></a>Comentários  
 Literais de comentário XML não contêm o conteúdo do documento; elas contêm informações sobre o documento. A seção de comentário XML termina com a sequência "-->". Isso implica que os seguintes pontos:  
  
-   Você não pode usar uma expressão inserida em um literal de comentário XML porque os delimitadores de expressão inserida são conteúdo válido de comentário XML.  
  
-   Seções de comentário XML não podem ser aninhadas, porque `content` não pode conter o valor "-->".  
  
 Você pode atribuir um literal de comentário XML para uma variável ou incluí-lo em um literal de elemento XML.  
  
> [!NOTE]
>  Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Esse recurso permite que você copiar o conteúdo de um documento XML e cole-o diretamente em um [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programa.  
  
 O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilador converte o literal de comentário XML para uma chamada para o <xref:System.Xml.Linq.XComment.%23ctor%2A> construtor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um comentário XML que contém o texto "Este é um comentário".  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XComment>  
 [Literal do Elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
