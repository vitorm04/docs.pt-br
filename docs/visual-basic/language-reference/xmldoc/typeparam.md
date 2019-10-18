---
title: <typeparam> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: dbd99997fed33c192a2160fb45a739addbae254a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524626"
---
# <a name="typeparam-visual-basic"></a>> de \<typeparam (Visual Basic)
Define um nome de parâmetro de tipo e uma descrição.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do parâmetro de tipo. Coloque o nome entre aspas duplas (" ").  
  
 `description`  
 Uma descrição do parâmetro de tipo.  
  
## <a name="remarks"></a>Comentários  
 Use a marca `<typeparam>` no comentário para um tipo genérico ou declaração de membro genérico para descrever um dos parâmetros de tipo.  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<typeparam>` para descrever o parâmetro `id`.  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
