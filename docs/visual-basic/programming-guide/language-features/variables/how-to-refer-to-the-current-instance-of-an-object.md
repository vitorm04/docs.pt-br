---
title: Como fazer referência à instância atual de um objeto
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: 62b22a54904a45380052d3d81d9415517d4f8d3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346889"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Como fazer referência à instância atual de um objeto (Visual Basic)
A *instância atual* de um objeto é a instância na qual o código está sendo executado no momento.  
  
 Use a palavra-chave `Me` para fazer referência à instância atual.  
  
### <a name="to-refer-to-the-current-instance"></a>Para fazer referência à instância atual  
  
- Use a palavra-chave `Me` onde você normalmente usaria o nome de uma variável de objeto.  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Embora `Me` se comporta como uma variável de objeto, você não pode declará-la nem atribuir nada a ela. `Me` sempre se refere à instância atual.  
  
## <a name="see-also"></a>Consulte também

- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
