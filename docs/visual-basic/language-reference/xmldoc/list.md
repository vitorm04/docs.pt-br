---
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352315"
---
# <a name="list-visual-basic"></a>> da lista de \<(Visual Basic)
Define uma lista ou tabela.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `type`  
 O tipo da lista. Deve ser um "Bullet" para uma lista com marcadores, "Number" para uma lista numerada ou "Table" para uma tabela de duas colunas.  
  
 `term`  
 Usado somente quando `type` é "Table". Um termo a definir, que é definido na marca de descrição.  
  
 `description`  
 Quando `type` é "Bullet" ou "Number", `description` é um item na lista quando `type` é "Table", `description` é a definição de `term`.  
  
## <a name="remarks"></a>Comentários  
 O bloco `<listheader>` define o cabeçalho de uma tabela ou de uma lista de definições. Ao definir uma tabela, você só precisa fornecer uma entrada para `term` no título.  
  
 Cada item na lista é especificado com um bloco de `<item>`. Ao criar uma lista de definições, você deve especificar `term` e `description`. No entanto, para uma tabela, lista com marcadores ou lista numerada, você só precisa fornecer uma entrada para `description`.  
  
 Uma lista ou tabela pode ter tantos blocos de `<item>` quantos forem necessários.  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca de `<list>` para definir uma lista com marcadores na seção de comentários.  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
