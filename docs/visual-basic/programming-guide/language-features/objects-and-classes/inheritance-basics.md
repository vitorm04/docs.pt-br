---
title: "No&#231;&#245;es b&#225;sicas de heran&#231;a (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes abstratas, herança"
  - "classes base, estendendo propriedades e métodos"
  - "classes base, herança"
  - "classes [Visual Basic], derivado"
  - "classes derivadas, herança"
  - "herança"
  - "Instrução Inherits, herança"
  - "Classes MustInherit"
  - "Palavra-chave MustInherit, usando"
  - "Palavra-chave MustOverride, usando"
  - "Palavra-chave MyBase, usando"
  - "Palavra-chave MyClass, usando"
  - "Palavra-chave NotInheritable, usando"
  - "Palavra-chave NotOverridable, usando"
  - "palavra-chave Overrides, usando"
  - "substituição, palavra-chave Overridable"
  - "substituição, palavra-chave Overrides"
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No&#231;&#245;es b&#225;sicas de heran&#231;a (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

A declaração `Inherits` é usada para declarar uma nova classe, chamada de *classe derivada*, com base em uma classe existente, conhecida como *classe base*.  Classes derivadas herdam e podem estender, propriedades, métodos, eventos, campos e constantes definidas na classe base.  A seção a seguir descreve algumas das regras de herança e os modificadores que você pode usar para alterar as classes de maneira herdam ou são herdados:  
  
-   Por padrão, todas as classes são herdadas, a menos que marcados com o `NotInheritable` palavra\-chave.  Classes podem herdar de outras classes em seu projeto ou de classes em outros assemblies que faz referência a seu projeto.  
  
-   Ao contrário das linguagens que permitem que a herança múltipla, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite somente herança única em classes; ou seja, as classes derivadas podem ter apenas uma classe base.  Embora a herança múltipla não é permitida em classes, classes podem implementar várias interfaces, o que efetivamente podem realizar as extremidades do mesmas.  
  
-   Para evitar expor restritos itens em uma classe base, o tipo de acesso de uma classe derivada deve ser igual ou mais restritivas do que sua classe base.  Por exemplo, um `Public` classe não pode herdar uma `Friend` ou um `Private` classe e um `Friend` classe não pode herdar uma `Private` classe.  
  
## Modificadores de herança  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]apresenta as seguintes instruções de nível de classe e modificadores para oferecer suporte a herança:  
  
-   `Inherits`instrução — Especifica a classe base.  
  
-   `NotInheritable`modificador — impede que os programadores usando a classe como uma classe base.  
  
-   `MustInherit`modificador — Especifica que a classe deve ser usado como uma classe base somente.  Instâncias de `MustInherit` não não possível criar classes diretamente. eles só podem ser criados como instâncias de classe base de uma classe derivada.  \(Outras linguagens de programação, como C\+\+ e C\#, usam o termo  *classe abstrata* para descrever essa classe.\)  
  
## Sobrescrevendo propriedades e métodos em Classes derivadas  
 Por padrão, uma classe derivada herda propriedades e métodos da sua classe base.  Se uma propriedade ou método herdado tem que ter um comportamento diferente na classe derivada pode ser  *substituído*.  Ou seja, você pode definir uma nova implementação do método na classe derivada.  Seguintes modificadores são usados para controlar como os métodos e propriedades são substituídos:  
  
-   `Overridable`— Permite que uma propriedade ou método em uma classe para ser substituído em uma classe derivada.  
  
-   `Overrides`— Substitui uma `Overridable` propriedade ou método definido na classe base.  
  
-   `NotOverridable`— Impede uma propriedade ou método que está sendo substituído em uma classe herdada.  Por padrão, `Public` métodos são `NotOverridable`.  
  
-   `MustOverride`— Requer que uma classe derivada substituir a propriedade ou método.  Quando o `MustOverride` palavra\-chave é usada, a definição do método consiste em apenas o `Sub`, `Function`, ou `Property` instrução.  Nenhuma outra instrução é permitidas e, especificamente, há nenhuma `End Sub` ou `End Function` instrução.  `MustOverride`métodos devem ser declarados no `MustInherit` classes.  
  
 Suponha que você queira definir classes para tratar a folha de pagamento.  Você pode definir uma classe `Payroll` genérica que contém um método `RunPayroll` que calcula da folha de pagamento de uma semana típica.  Você poderia então utilizar `Payroll` como uma classe base de uma classe `BonusPayroll` mais especializada, que pode ser usada ao distribuir bônus aos funcionários.  
  
 A classe `BonusPayroll` pode herdar e substituir, o método `PayEmployee` definido na classe base `Payroll`.  
  
 O exemplo a seguir define uma classe base, `Payroll,` e um classe derivada, `BonusPayroll`, que substitui um método `PayEmployee` herdado.  Um procedimento, `RunPayroll`, cria e, em seguida, passa um objeto `Payroll` e um objeto `BonusPayroll` para uma função, `Pay`,que executa o método `PayEmployee` dos dois objetos.  
  
 [!code-vb[VbVbalrOOP#28](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## A palavra\-chave MyBase  
 O `MyBase` palavra\-chave se comporta como uma variável de objeto que se refere a classe base da instância atual de uma classe.  `MyBase`é freqüentemente usado para acessar membros de classe base que são substituídos ou sombreados em uma classe derivada.  Em particular, `MyBase.New` é usado para chamar um construtor de classe base de um construtor de classe derivada explicitamente.  
  
 Por exemplo, suponha que você está criando uma classe derivada que substitui um método herdado da classe base.  O método substituído pode chamar o método na classe base e modifique o valor de retorno, conforme mostrado no fragmento de código a seguir:  
  
 [!code-vb[VbVbalrOOP#109](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 A lista a seguir descreve as restrições sobre o uso de `MyBase`:  
  
-   `MyBase`refere\-se para a classe base imediata e seus membros herdados.  Ela não pode ser usada para acesso `Private` os membros da classe.  
  
-   `MyBase`é uma palavra\-chave, não é um objeto real.  `MyBase`não pode ser atribuído a uma variável, passados para procedimentos ou usado em um `Is` comparação.  
  
-   O método que `MyBase` qualifica não devem ser definidos na classe base imediata; em vez disso, podem ser definido de uma classe de base indiretamente herdada.  Para que uma referência qualificada pela `MyBase` para compilar corretamente, alguns classe base deve conter um correspondência, o nome e tipos de parâmetros que aparecem na chamada de método.  
  
-   Não é possível usar `MyBase` para chamar `MustOverride` métodos de classe de base.  
  
-   `MyBase`não pode ser usado para qualificar a mesmo.  Portanto, o código a seguir não é válido:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase`não pode ser usado em módulos.  
  
-   `MyBase`não pode ser usado para acessar membros de classe base que são marcados como `Friend` se a classe base está em um assembly diferente.  
  
 Para obter mais informações e outro exemplo, consulte [Como acessar uma variável oculta por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## A palavra\-chave MyClass  
 O `MyClass` palavra\-chave se comporta como uma variável de objeto que se refere à instância atual de uma classe como originalmente implementada.  `MyClass`semelhante a `Me`, mas cada método e propriedade chamar em `MyClass` é tratado como se fosse o método ou propriedade [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).  Portanto, o método ou propriedade não é afetado por substituição numa classe derivada.  
  
-   `MyClass`é uma palavra\-chave, não é um objeto real.  `MyClass`não pode ser atribuído a uma variável, passados para procedimentos ou usado em um `Is` comparação.  
  
-   `MyClass`refere\-se para a classe continente e seus membros herdados.  
  
-   `MyClass`pode ser usado como um qualificador para `Shared` membros.  
  
-   `MyClass`não pode ser usado dentro de um `Shared` método, mas pode ser usado dentro de um método de instância para acessar um membro compartilhado de uma classe.  
  
-   `MyClass`não pode ser usado em módulos padrão.  
  
-   `MyClass`pode ser usado para qualificar um método que está definido na classe base e que não tem implementação do método fornecido nessa classe.  Tal referência tem o mesmo significado que `MyBase.`*método*.  
  
 O exemplo a seguir compara `Me` e `MyClass`.  
  
```  
Class baseClass  
    Public Overridable Sub testMethod()  
        MsgBox("Base class string")  
    End Sub  
    Public Sub useMe()  
        ' The following call uses the calling class's method, even if   
        ' that method is an override.  
        Me.testMethod()  
    End Sub  
    Public Sub useMyClass()  
        ' The following call uses this instance's method and not any  
        ' override.  
        MyClass.testMethod()  
    End Sub  
End Class  
Class derivedClass : Inherits baseClass  
    Public Overrides Sub testMethod()  
        MsgBox("Derived class string")  
    End Sub  
End Class  
Class testClasses  
    Sub startHere()  
        Dim testObj As derivedClass = New derivedClass()  
        ' The following call displays "Derived class string".  
        testObj.useMe()  
        ' The following call displays "Base class string".  
        testObj.useMyClass()  
    End Sub  
End Class  
```  
  
 Mesmo se `derivedClass` substitui `testMethod`, a palavra\-chave `MyClass` na `useMyClass` anula os efeitos da substituição, e o compilador defina a chamada à versão da classe base de `testMethod`.  
  
## Consulte também  
 [Instrução Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)