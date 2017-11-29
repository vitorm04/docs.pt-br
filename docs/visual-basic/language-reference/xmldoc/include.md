---
title: '&lt;incluir&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22eebaa8da8ef082e132cfdf8cb68498bfe16d73
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltincludegt-visual-basic"></a>&lt;incluir&gt; (Visual Basic)
Refere-se a outro arquivo que descreve os tipos e membros no código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `filename`  
 Necessário. O nome do arquivo que contém a documentação. O nome do arquivo pode ser qualificado com um caminho. Coloque `filename` entre aspas duplas ("").  
  
 `tagpath`  
 Necessário. O caminho das marcas em `filename` que leva à marca `name`. Coloque o caminho entre aspas duplas ("").  
  
 `name`  
 Necessário. O especificador de nome na marca que precede os comentários. `Name`será necessário um `id`.  
  
 `id`  
 Necessário. A ID da marca que precede os comentários. Coloque a ID entre aspas simples (' ').  
  
## <a name="remarks"></a>Comentários  
 Use o `<include>` marca Consulte comentários em outro arquivo que descrevem os tipos e membros no código-fonte. Essa é uma alternativa para inserir comentários de documentação diretamente em seu arquivo de código-fonte.  
  
 O `<include>` marca usa a recomendação do W3C XML Path Language (XPath) versão 1.0. Para obter mais informações sobre como personalizar o `<include>` uso está disponível em http://www.w3.org/TR/xpath.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<include>` marca para importar os comentários de documentação do membro de um arquivo chamado `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
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
 [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
