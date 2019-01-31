---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 476b3f4f6b85908897e15f73bc23d2b060e337c3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283641"
---
# <a name="param-visual-basic"></a>\<param > (Visual Basic)
Define um nome de parâmetro e uma descrição.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro de um método. Coloque o nome entre aspas duplas (" ").  
  
 `description`  
 Uma descrição do parâmetro.  
  
## <a name="remarks"></a>Comentários  
 O `<param>` marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método.  
  
 O texto para o `<param>` marca será exibida nos seguintes locais:  
  
-   Informações do parâmetro do IntelliSense. Para obter mais informações, veja [Usando o IntelliSense](/visualstudio/ide/using-intellisense).  
  
-   Pesquisador de objetos. Para obter mais informações, consulte [Exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `<param>` marca para descrever o `id` parâmetro.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
