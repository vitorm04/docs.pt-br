---
title: 'Como: Criar uma nova variável (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: db317b160a27c7e38bddba82eb4eac3088886705
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506882"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>Como: Criar uma nova variável (Visual Basic)
Crie uma variável com um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
### <a name="to-create-a-new-variable"></a>Para criar uma nova variável  
  
1.  Declare a variável em um `Dim` instrução.  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  Incluir as especificações para as características da variável, como [privados](../../../../visual-basic/language-reference/modifiers/private.md), [estático](../../../../visual-basic/language-reference/modifiers/static.md), [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md), ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md). Para obter mais informações, consulte [características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
     Não é necessário o `Dim` palavra-chave se você usar outras palavras-chave na declaração.  
  
3.  Siga as especificações com o nome da variável, que deve seguir as convenções e regras do Visual Basic. Para obter mais informações, consulte [nomes de elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  Siga o nome com o [como](../../../../visual-basic/language-reference/statements/as-clause.md) cláusula para especificar o tipo de dados da variável.  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     Se você não especificar o tipo de dados, ele usa o padrão: `Object`.  
  
5.  Siga as `As` cláusula com um sinal de igual (`=`) e siga o sinal de igualdade com o valor da variável inicial.  
  
     Visual Basic atribui o valor especificado para a variável de cada vez que executar o `Dim` instrução. Se você não especificar um valor inicial, o Visual Basic atribui o valor inicial de padrão para o tipo de dados quando ele entra pela primeira vez o código que contém o `Dim` instrução.  
  
     Se a variável é um tipo de referência, você pode criar uma instância de sua classe, incluindo o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave no `As` cláusula. Se você não usar `New`, o valor inicial da variável é [nada](../../../../visual-basic/language-reference/nothing.md).  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>Consulte também
- [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Nomes de Elementos Declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Características do Elemento Declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Instruções](../../../../visual-basic/language-reference/statements/index.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
