---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c62eab6b1fb1ba1cc7de83c12d7205cf0bbe46fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524726"
---
# <a name="param-visual-basic"></a>> de \<param (Visual Basic)
Define um nome de parâmetro e uma descrição.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro de um método. Coloque o nome entre aspas duplas (" ").  
  
 `description`  
 Uma descrição do parâmetro.  
  
## <a name="remarks"></a>Comentários  
 A marca de `<param>` deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros para o método.  
  
 O texto da marca de `<param>` aparecerá nos seguintes locais:  
  
- Informações de parâmetro do IntelliSense. Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).  
  
- Pesquisador de objetos. Para obter mais informações, consulte [Exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<param>` para descrever o parâmetro `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
