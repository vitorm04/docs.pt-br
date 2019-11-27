---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348455"
---
# <a name="include-visual-basic"></a>\<incluir > (Visual Basic)
Refere-se a outro arquivo que descreve os tipos e membros em seu código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parâmetros  
 `filename`  
 Necessária. O nome do arquivo que contém a documentação. O nome do arquivo pode ser qualificado com um caminho. Coloque `filename` entre aspas duplas ("").  
  
 `tagpath`  
 Necessária. O caminho das marcas em `filename` que leva à marca `name`. Coloque o caminho entre aspas duplas ("").  
  
 `name`  
 Necessária. O especificador de nome na marca que precede os comentários. `Name` terá um `id`.  
  
 `id`  
 Necessária. A ID da marca que precede os comentários. Coloque a ID entre aspas simples (' ').  
  
## <a name="remarks"></a>Comentários  
 Use a marca `<include>` para fazer referência a comentários em outro arquivo que descreva os tipos e membros em seu código-fonte. Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.  
  
 A marca de `<include>` usa a recomendação do W3C XML Path Language (XPath) versão 1,0. Para obter mais informações sobre maneiras de personalizar o uso de `<include>`, consulte <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<include>` para importar comentários de documentação de membro de um arquivo chamado `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 O formato da `commentFile.xml` é o seguinte.  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
