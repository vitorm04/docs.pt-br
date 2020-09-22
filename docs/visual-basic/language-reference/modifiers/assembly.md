---
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 34d6b94f31336e3e99b8ca981a9c4899e5a3d912
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875522"
---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)

Especifica que um atributo no início de um arquivo de origem se aplica a todo o assembly.  
  
## <a name="remarks"></a>Comentários  

 Muitos atributos pertencem a um elemento de programação individual, como uma classe ou propriedade. Você aplica esse atributo, anexando o bloco de atributo, entre colchetes angulares ( `< >` ), diretamente à instrução de declaração.  
  
 Se um atributo pertencer não apenas ao elemento a seguir, mas ao assembly inteiro, você coloca o bloco de atributo no início do arquivo de origem e identifica o atributo com a `Assembly` palavra-chave. Se se aplicar ao módulo do assembly atual, você usará a palavra-chave do [módulo](module-keyword.md) .  
  
 Você também pode aplicar um atributo a um assembly no arquivo AssemblyInfo. vb, caso em que você não precisa usar um bloco de atributos em seu arquivo de código-fonte principal.  
  
## <a name="see-also"></a>Confira também

- [Modulo \<keyword>](module-keyword.md)
- [Visão geral de atributos](../../programming-guide/concepts/attributes/index.md)
