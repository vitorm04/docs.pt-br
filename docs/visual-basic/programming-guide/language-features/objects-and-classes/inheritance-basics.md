---
title: "Noções básicas de herança (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- derived classes, inheritance
- MyClass keyword, using
- MyBase keyword, using
- Inherits statement, inheritance
- overriding, Overridable keyword
- MustInherit keyword, using
- Overrides keyword, using
- inheritance
- MustInherit classes
- MustOverride keyword, using
- classes [Visual Basic], derived
- NotInheritable keyword, using
- base classes, extending properties and methods
- NotOverridable keyword, using
- base classes, inheritance
- abstract classes, inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 58aee9f8c348eb06daec2b8c9e332f3f2775bcb6
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="inheritance-basics-visual-basic"></a>Noções básicas de herança (Visual Basic)
O `Inherits` instrução é usada para declarar uma nova classe, chamada um *classe derivada*, com base em uma classe existente, conhecida como uma *classe base*. Classes derivadas herdam e podem estender, propriedades, métodos, eventos, campos e constantes definidas na classe base. A seção a seguir descreve algumas das regras de herança e os modificadores que você pode usar para alterar as classes de maneira herdam ou são herdados:  
  
-   Por padrão, todas as classes são herdadas, a menos que marcados com o `NotInheritable` palavra-chave. Classes podem herdar de outras classes em seu projeto ou de classes em outros assemblies referenciados pelo seu projeto.  
  
-   Ao contrário de linguagens que permitem a herança múltipla, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] permite que a herança única apenas classes; ou seja, classes derivadas podem ter apenas uma classe base. Embora a herança múltipla não é permitida em classes, classes podem implementar várias interfaces, o que efetivamente podem fazer o mesmo fim.  
  
-   Para evitar expor itens restritos em uma classe base, o tipo de acesso de uma classe derivada deve ser igual ou mais restritivo do que sua classe base. Por exemplo, um `Public` classe não pode herdar um `Friend` ou um `Private` classe e um `Friend` classe não pode herdar um `Private` classe.  
  
## <a name="inheritance-modifiers"></a>Modificadores de herança  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]introduz as seguintes declarações de nível de classe e modificadores para dar suporte a herança:  
  
-   `Inherits`instrução — Especifica a classe base.  
  
-   `NotInheritable`modificador — impede que os programadores usando a classe como uma classe base.  
  
-   `MustInherit`modificador — Especifica que a classe é destinada para uso como apenas uma classe base. Instâncias de `MustInherit` classes não podem ser criadas diretamente; eles só podem ser criados instâncias de classe como base de uma classe derivada. (Outras linguagens de programação, como C++ e c#, usam o termo *classe abstrata* para descrever tal classe.)  
  
## <a name="overriding-properties-and-methods-in-derived-classes"></a>Substituindo propriedades e métodos em Classes derivadas  
 Por padrão, uma classe derivada herda propriedades e métodos de sua classe base. Se tiver uma propriedade ou método herdado para se comportar de maneira diferente na classe derivada pode ser *substituído*. Ou seja, você pode definir uma nova implementação do método na classe derivada. Seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:  
  
-   `Overridable`– Permite que uma propriedade ou método em uma classe a ser substituído em uma classe derivada.  
  
-   `Overrides`— Substitui uma `Overridable` propriedade ou método definido na classe base.  
  
-   `NotOverridable`— Impede que uma propriedade ou método que está sendo substituído em uma classe herdada. Por padrão, `Public` métodos são `NotOverridable`.  
  
-   `MustOverride`— Requer que uma classe derivada substituir a propriedade ou método. Quando o `MustOverride` palavra-chave é usado, a definição do método consiste apenas o `Sub`, `Function`, ou `Property` instrução. Não há outras instruções são permitidas e especificamente há nenhum `End Sub` ou `End Function` instrução. `MustOverride`métodos devem ser declarados no `MustInherit` classes.  
  
 Suponha que você queira definir classes para tratar da folha de pagamento. Você pode definir um genérico `Payroll` classe que contém um `RunPayroll` método que calcula da folha de pagamento de uma semana típica. Você pode usar `Payroll` como uma classe base para o mais especializado `BonusPayroll` classe, que pode ser usada ao distribuir bônus aos funcionários.  
  
 O `BonusPayroll` classe pode herdar e substituir, o `PayEmployee` método definido na base de `Payroll` classe.  
  
 O exemplo a seguir define uma classe base, `Payroll,` e uma classe derivada, `BonusPayroll`, que substitui um método herdado, `PayEmployee`. Um procedimento, `RunPayroll`, cria e, em seguida, passa uma `Payroll` objeto e um `BonusPayroll` objeto para uma função, `Pay`, que executa o `PayEmployee` método dos dois objetos.  
  
 [!code-vb[VbVbalrOOP&#28;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_1.vb)]  
  
## <a name="the-mybase-keyword"></a>A palavra-chave MyBase  
 O `MyBase` palavra-chave se comporta como uma variável de objeto que faz referência à classe base da instância atual de uma classe. `MyBase`é frequentemente usado para acessar membros de classe base que são substituídos ou sombreados em um classe derivada. Em particular, `MyBase.New` é usado para chamar um construtor de classe base de um construtor de classe derivada explicitamente.  
  
 Por exemplo, suponha que você está criando uma classe derivada que substitui um método herdado da classe base. O método substituído pode chamar o método na classe base e modifique o valor de retorno, como mostrado no fragmento de código a seguir:  
  
 [!code-vb[VbVbalrOOP&#109;](../../../../visual-basic/misc/codesnippet/VisualBasic/inheritance-basics_2.vb)]  
  
 A lista a seguir descreve as restrições sobre o uso de `MyBase`:  
  
-   `MyBase`refere-se a classe base imediata e seus membros herdados. Ele não pode ser usado para acessar `Private` os membros da classe.  
  
-   `MyBase`é uma palavra-chave, não um objeto real. `MyBase`não pode ser atribuído a uma variável, passados a procedimentos ou usado em um `Is` comparação.  
  
-   O método que `MyBase` qualifica não precisa ser definido na classe base imediata; em vez disso, podem ser definido em uma classe base indiretamente herdada. Para que uma referência qualificada pela `MyBase` para compilar corretamente, uma classe base deve conter um método de correspondência de nome e tipos de parâmetros que aparecem na chamada.  
  
-   Não é possível usar `MyBase` chamar `MustOverride` métodos de classe de base.  
  
-   `MyBase`não pode ser usado para qualificar em si. Portanto, o código a seguir não é válido:  
  
     `MyBase.MyBase.BtnOK_Click()`  
  
-   `MyBase`não pode ser usado nos módulos.  
  
-   `MyBase`não pode ser usado para acessar membros de classe base que são marcados como `Friend` se a classe base está em um assembly diferente.  
  
 Para obter mais informações e um outro exemplo, consulte [como: acessar uma variável oculta por uma classe derivada de](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
## <a name="the-myclass-keyword"></a>A palavra-chave MyClass  
 O `MyClass` palavra-chave se comporta como uma variável de objeto refere-se à instância atual de uma classe como implementada originalmente. `MyClass`é semelhante a `Me`, mas chamar cada método e propriedade em `MyClass` é tratado como se fosse o método ou propriedade [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md). Portanto, o método ou propriedade não é afetada por meio de substituição em uma classe derivada.  
  
-   `MyClass`é uma palavra-chave, não um objeto real. `MyClass`não pode ser atribuído a uma variável, passados a procedimentos ou usado em um `Is` comparação.  
  
-   `MyClass`refere-se a classe recipiente e seus membros herdados.  
  
-   `MyClass`pode ser usado como um qualificador para `Shared` membros.  
  
-   `MyClass`não pode ser usado dentro de um `Shared` método, mas pode ser usado dentro de um método de instância para acessar um membro compartilhado de uma classe.  
  
-   `MyClass`não pode ser usado em módulos padrão.  
  
-   `MyClass`pode ser usado para qualificar um método que é definido em uma classe base e que não tem implementação do método fornecido nessa classe. Essa referência tem o mesmo significado que `MyBase.` *método*.  
  
 O exemplo a seguir compara `Me` e `MyClass`.  
  
```vb
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
  
 Embora `derivedClass` substituições `testMethod`, o `MyClass` palavra-chave em `useMyClass` anula os efeitos da substituição e o compilador resolve a chamada para a versão da classe base de `testMethod`.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Inherits](../../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)

