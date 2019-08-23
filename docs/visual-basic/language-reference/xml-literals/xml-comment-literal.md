---
title: Literal de comentário XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965408"
---
# <a name="xml-comment-literal-visual-basic"></a>Literal de comentário XML (Visual Basic)
Um literal que representa <xref:System.Xml.Linq.XComment> um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`<!--`|Necessário. Denota o início do comentário XML.|  
|`content`|Necessário. Texto a ser exibido no comentário XML. Não pode conter uma série de dois hifens (--) ou terminar com um hífen adjacente à marca de fechamento.|  
|`-->`|Necessário. Denota o final do comentário XML.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto <xref:System.Xml.Linq.XComment>.  
  
## <a name="remarks"></a>Comentários  
 Literais de comentário XML não contêm conteúdo de documento; Eles contêm informações sobre o documento. A seção de comentário XML termina com a sequência "-->". Isso implica nos seguintes pontos:  
  
- Você não pode usar uma expressão inserida em um literal de comentário XML porque os delimitadores de expressão inseridos são conteúdo de comentário XML válido.  
  
- As seções de comentário XML não podem ser `content` aninhadas porque não podem conter o valor "-->".  
  
 Você pode atribuir um literal de comentário XML a uma variável ou pode incluí-lo em um literal de elemento XML.  
  
> [!NOTE]
> Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Esse recurso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.  
  
 O compilador Visual Basic converte o literal de comentário XML em uma chamada para <xref:System.Xml.Linq.XComment.%23ctor%2A> o construtor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um comentário XML que contém o texto "Este é um comentário".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XComment>
- [Literal do Elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
