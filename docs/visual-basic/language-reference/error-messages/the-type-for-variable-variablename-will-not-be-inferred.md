---
title: O tipo da variável '<variablename>' não será inferido porque está associado a um campo em um escopo delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: a595f38f6dd68b9c152bfa78ec0bebf36e173e17
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649963"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>O tipo da variável '\<variablename >' não será inferido porque está associado a um campo em um escopo delimitador
O tipo da variável '\<variablename >' não será inferido porque está associado a um campo em um escopo delimitador. Altere o nome do '\<variablename >', ou use o nome totalmente qualificado (por exemplo, 'Me.variablename' ou 'MyBase.variablename').  
  
 Uma variável de controle de loop em seu código tem o mesmo nome como um campo da classe ou em outro escopo delimitador. Como a variável de controle é usada sem um `As` cláusula, ele é associado ao campo no escopo delimitador e o compilador não cria uma nova variável para ele ou inferir seu tipo.  
  
 No exemplo a seguir, `Index`, a variável de controle na `For` instrução, está associado ao `Index` campo o `Customer` classe. O compilador não cria uma nova variável para a variável de controle `Index` ou inferir seu tipo.  
  
```  
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
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42110  
  
### <a name="to-address-this-warning"></a>Para resolver este aviso  
  
- Verifique a variável de controle de loop local, alterando seu nome para um identificador que também não é o nome de um campo da classe.  
  
    ```  
    For I = 1 To 10  
    ```  
  
- Esclarecer o que a variável de controle de loop é associado ao campo de classe, prefixando `Me.` ao nome da variável.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
- Em vez de depender de inferência de tipo local, use um `As` cláusula para especificar um tipo para a variável de controle de loop.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo anterior com a primeira correção em vigor.  
  
```  
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
- [Como: Fazer referência à instância atual de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
