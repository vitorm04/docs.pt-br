---
title: Literal de Comentário XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349395"
---
# <a name="xml-comment-literal-visual-basic"></a>Literal de comentário XML (Visual Basic)
Um literal que representa um objeto <xref:System.Xml.Linq.XComment>.  
  
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
  
## <a name="return-value"></a>Valor retornado  
 Um objeto <xref:System.Xml.Linq.XComment>.  
  
## <a name="remarks"></a>Comentários  
 Literais de comentário XML não contêm conteúdo de documento; Eles contêm informações sobre o documento. A seção de comentário XML termina com a sequência "-->". Isso implica nos seguintes pontos:  
  
- Você não pode usar uma expressão inserida em um literal de comentário XML porque os delimitadores de expressão inseridos são conteúdo de comentário XML válido.  
  
- As seções de comentário XML não podem ser aninhadas porque `content` não pode conter o valor "-->".  
  
 Você pode atribuir um literal de comentário XML a uma variável ou pode incluí-lo em um literal de elemento XML.  
  
> [!NOTE]
> Um literal XML pode abranger várias linhas sem usar caracteres de continuação de linha. Esse recurso permite que você copie o conteúdo de um documento XML e cole-o diretamente em um programa Visual Basic.  
  
 O compilador Visual Basic converte o literal de comentário XML em uma chamada para o Construtor <xref:System.Xml.Linq.XComment.%23ctor%2A>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um comentário XML que contém o texto "Este é um comentário".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XComment>
- [Literal do Elemento XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literais XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Criando XML no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
