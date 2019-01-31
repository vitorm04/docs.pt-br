---
title: Módulo <keyword> (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: fa798e8a2c82bdf204edb1812b0020f874b1e978
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257690"
---
# <a name="module-keyword-visual-basic"></a>Módulo \<palavra-chave > (Visual Basic)
Especifica que um atributo no início de um arquivo de origem se aplica ao módulo assembly atual.  
  
## <a name="remarks"></a>Comentários  
 Muitos atributos referem-se a um elemento de programação individual, como uma classe ou propriedade. Aplicar tal um atributo, anexando o bloco de atributo, entre colchetes angulares (`< >`), diretamente à instrução de declaração.  
  
 Se um atributo pertence não apenas para o próximo elemento, mas para o módulo do assembly atual, coloque o bloco de atributo no início do arquivo de origem e identifica o atributo com o `Module` palavra-chave. Se ele se aplica a todo o assembly, você usa o [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) palavra-chave.  
  
 O `Module` modificador não é igual a [instrução Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
## <a name="see-also"></a>Consulte também
- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

