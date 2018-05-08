---
title: O tipo de variável &#39; &lt;variablename&gt; &#39; não será inferido porque está associado a um campo em um escopo delimitador
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: cb423e8dcced6956eb86d484607915030c91412b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>O tipo de variável &#39; &lt;variablename&gt; &#39; não será inferido porque está associado a um campo em um escopo delimitador
O tipo de variável '\<variablename >' não será inferido porque está associado a um campo em um escopo delimitador. Altere o nome de '\<variablename >', ou use o nome totalmente qualificado (por exemplo, 'Me.variablename' ou 'MyBase.variablename').  
  
 Uma variável de controle de loop no seu código tem o mesmo nome como um campo da classe ou a outro escopo delimitador. Como a variável de controle é usada sem um `As` cláusula, está associado ao campo no escopo delimitador e o compilador não cria uma nova variável para ele ou inferir o tipo.  
  
 No exemplo a seguir, `Index`, a variável de controle no `For` instrução, está associado ao `Index` campo o `Customer` classe. O compilador não cria uma nova variável para a variável de controle `Index` ou inferir o tipo.  
  
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
  
-   Verifique a variável de controle de loop local alterando seu nome para um identificador que também não é o nome de um campo da classe.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Esclarecer que a variável de controle de loop estará associado ao campo de classe, prefixando `Me.` para o nome da variável.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Em vez de depender de inferência de tipo local, use um `As` cláusula para especificar um tipo para a variável de controle de loop.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo anterior, com a primeira correção em vigor.  
  
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
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Como fazer referência à instância atual de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
