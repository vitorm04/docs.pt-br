---
title: O tipo da variável '<variablename>' não será inferido porque está associado a um campo em um escopo delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: e56529919945558df178e18a83a895a79bfe4919
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512717"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>O tipo da variável '\<VariableName > ' não será inferido porque está associado a um campo em um escopo delimitador

O tipo da variável '\<VariableName > ' não será inferido porque está associado a um campo em um escopo delimitador. Altere o nome de '\<VariableName > ' ou use o nome totalmente qualificado (por exemplo, ' me. VariableName ' ou ' MyBase. VariableName ').

Uma variável de controle de loop em seu código tem o mesmo nome que um campo da classe ou outro escopo delimitador. Como a variável de controle é usada sem `As` uma cláusula, ela é associada ao campo no escopo delimitador, e o compilador não cria uma nova variável para ela ou infere seu tipo.

No exemplo a seguir, `Index`, a variável de controle `For` na instrução é associada `Customer` ao `Index` campo na classe. O compilador não cria uma nova variável para a variável `Index` de controle ou infere seu tipo.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou como tratar avisos como erros, consulte Configurando [avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**ID do erro:** BC42110

### <a name="to-address-this-warning"></a>Para resolver este aviso

- Torne a variável de controle de loop local alterando seu nome para um identificador que não seja também o nome de um campo da classe.

  ```vb
  For I = 1 To 10
  ```

- Esclareça que a variável de controle de loop é vinculada ao campo de classe `Me.` prefixando para o nome da variável.

  ```vb
  For Me.Index = 1 To 10
  ```

- Em vez de depender da inferência de tipo local, `As` use uma cláusula para especificar um tipo para a variável de controle de loop.

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a>Exemplo
 O código a seguir mostra o exemplo anterior com a primeira correção em vigor.

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a>Consulte também

- [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Como: Consulte a instância atual de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
