---
title: "O tipo da variável &quot;&lt;variablename&gt;&quot; não será inferido porque está associado a um campo em um escopo delimitador | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
dev_langs:
- VB
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ab7d69c34a58dc898553868258c4fdf6b81db343
ms.lasthandoff: 03/13/2017

---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>O tipo da variável '&lt;variablename&gt;' não será inferido porque está associado a um campo em um escopo delimitador
O tipo da variável '\<NOMEDAVARIÁVEL >' não será inferido porque está associado a um campo em um escopo delimitador. Altere o nome de '\<NOMEDAVARIÁVEL >', ou use o nome totalmente qualificado (por exemplo, 'Me.variablename' ou 'MyBase.variablename').  
  
 Uma variável de controle de loop em seu código tem o mesmo nome como um campo de classe ou em outro escopo delimitador. Como a variável de controle é usada sem um `As` cláusula, ele é associado ao campo no escopo delimitador e o compilador não cria uma nova variável para ele ou inferir o tipo.  
  
 No exemplo a seguir, `Index`, a variável de controle no `For` instrução, está vinculado ao `Index` campo o `Customer` classe. O compilador não cria uma nova variável para a variável de controle `Index` ou inferir o tipo.  
  
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
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42110  
  
### <a name="to-address-this-warning"></a>Para resolver este aviso  
  
-   Verifique a variável de controle de loop local alterando seu nome para um identificador que também não é o nome de um campo da classe.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Esclarecer o que a variável de controle de loop associa ao campo classe prefixando `Me.` para o nome da variável.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Em vez de contar com a inferência de tipo local, use um `As` cláusula para especificar um tipo para a variável de controle de loop.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra o exemplo anterior com a primeira correção no lugar.  
  
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
 [Para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Como: fazer referência à instância atual de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
