---
title: 'Como: Fazer referência à instância atual de um objeto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: d166ce62a2bb0522d1ca7011aeff7afe076c2d8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542191"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>Como: Fazer referência à instância atual de um objeto (Visual Basic)
O *instância atual* de um objeto é a instância na qual o código está sendo executado.  
  
 Você usa o `Me` palavra-chave para referir-se à instância atual.  
  
### <a name="to-refer-to-the-current-instance"></a>Para fazer referência à instância atual  
  
-   Use o `Me` palavra-chave em que você normalmente usaria o nome de uma variável de objeto.  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     Embora `Me` se comporta como um objeto variável, você não pode declará-la ou atribuir algo a ela. `Me` sempre refere-se à instância atual.  
  
## <a name="see-also"></a>Consulte também
- [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Atribuição de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
