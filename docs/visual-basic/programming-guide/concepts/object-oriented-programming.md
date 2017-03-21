---
title: "Programação orientada a objeto (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5491b3bd5a25908194d02063f688a319509bb77
ms.lasthandoff: 03/13/2017

---
# <a name="object-oriented-programming-visual-basic"></a>Programação orientada a objeto (Visual Basic)
Visual Basic fornece suporte completo para a programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.  
  
 *Encapsulamento* significa que um grupo de propriedades relacionadas, métodos e outros membros são tratados como uma única unidade ou um objeto.  
  
 *Herança* descreve a capacidade de criar novas classes com base em uma classe existente.  
  
 *Polimorfismo* significa que você pode ter várias classes que podem ser usadas intercambiavelmente, mesmo que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.  
  
 Esta seção descreve os seguintes conceitos:  
  
-   [Classes e objetos](#Classes)  
  
    -   [Membros de classe](#Members)  
  
         [Campos e propriedades](#Properties)  
  
         [Métodos](#Methods)  
  
         [Construtores](#Constructors)  
  
         [Destruidores](#Destructors)  
  
         [Eventos](#Events)  
  
         [Classes aninhadas](#NestedClasses)  
  
    -   [Modificadores de acesso e níveis de acesso](#AccessModifiers)  
  
    -   [Instanciação de Classes](#InstantiatingClasses)  
  
    -   [Classes compartilhadas e membros](#Static)  
  
    -   [Tipos Anônimos](#AnonymousTypes)  
  
-   [Herança](#Inheritance)  
  
    -   [Substituindo membros](#Overriding)  
  
-   [Interfaces](#Interfaces)  
  
-   [Genéricos](#Generics)  
  
-   [Delegados](#Delegates)  
  
##  <a name="Classes"></a>Classes e objetos  
 Os termos de *classe* e *objeto* são às vezes usados alternadamente, mas na verdade, as classes descrevem o *tipo* de objetos, enquanto objetos são utilizáveis *instâncias* de classes. Assim, o ato de criar um objeto é chamado *instanciação*. Usando a analogia da planta, uma classe é a planta e um objeto é a construção feita daquela planta.  
  
 Para definir uma classe:  
  
```vb  
Class SampleClass  
End Class  
```  
  
 Visual Basic também fornece uma versão leve de classes chamado *estruturas* que são úteis quando você precisa criar uma matriz grande de objetos e não deseja consumir muita memória para isso.  
  
 Para definir uma estrutura:  
  
```vb  
Structure SampleStructure  
End Structure  
```  
  
 Para obter mais informações, consulte:  
  
-   [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
###  <a name="Members"></a>Membros de classe  
 Cada classe pode ter diferentes *membros de classe* que incluem propriedades que descrevem os dados de classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.  
  
####  <a name="Properties"></a>Campos e propriedades  
 Campos e propriedades representam informações que um objeto contém. Campos são como variáveis, porque eles podem ser lidos ou definidos diretamente.  
  
 Para definir um campo:  
  
```vb  
Class SampleClass  
    Public SampleField As String  
End Class  
```  
  
 Propriedades têm get e definir procedimentos, que oferecem mais controle sobre como os valores são definidos ou retornados.  
  
 Visual Basic permite que você crie um campo particular para armazenar o valor da propriedade ou use chamadas propriedades implementadas automaticamente que criar esse campo automaticamente em segundo plano e fornecerem a lógica básica para os procedimentos de propriedade.  
  
 Para definir uma propriedade implementada automaticamente:  
  
```vb  
Class SampleClass  
    Public Property SampleProperty as String  
End Class  
```  
  
 Se você precisa executar algumas operações adicionais para ler e gravar o valor de propriedade, defina um campo para armazenar o valor da propriedade e fornecer a lógica básica para armazenar e recuperar:  
  
```vb  
Class SampleClass  
    Private m_Sample As String  
    Public Property Sample() As String  
        Get  
            ' Return the value stored in the field.  
            Return m_Sample  
        End Get  
        Set(ByVal Value As String)  
            ' Store the value in the field.  
            m_Sample = Value  
        End Set  
    End Property  
End Class  
```  
  
 A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade. No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas. No Visual Basic, você pode usar `ReadOnly` e `WriteOnly` palavras-chave. No entanto, as propriedades implementadas automaticamente não podem ser somente leitura ou somente gravação.  
  
 Para obter mais informações, consulte:  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
####  <a name="Methods"></a> Métodos  
 A *método* é uma ação que um objeto pode executar.  
  
> [!NOTE]
>  No Visual Basic, existem duas maneiras de criar um método: o `Sub` instrução é usada se o método retornar um valor; o `Function` instrução é usada se um método retornar um valor.  
  
 Para definir um método de uma classe:  
  
```vb  
Class SampleClass  
    Public Function SampleFunc(ByVal SampleParam As String)  
        ' Add code here  
    End Function  
End Class  
```  
  
 Uma classe pode ter várias implementações, ou *sobrecargas*, do mesmo método que diferem no número de parâmetros ou tipos de parâmetro.  
  
 Para sobrecarregar um método:  
  
```vb  
Overloads Sub Display(ByVal theChar As Char)  
    ' Add code that displays Char data.  
End Sub  
Overloads Sub Display(ByVal theInteger As Integer)  
    ' Add code that displays Integer data.  
End Sub  
```  
  
 Na maioria dos casos você declarar um método dentro de uma definição de classe. No entanto, o Visual Basic também ofereça suporte *métodos de extensão* que permitem que você adicione métodos a uma classe existente fora a definição real da classe.  
  
 Para obter mais informações, consulte:  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
-   [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
  
####  <a name="Constructors"></a> Construtores  
 Construtores são os métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado. Construtores geralmente inicializam os membros de dados do novo objeto. Um construtor pode executar apenas uma vez quando uma classe é criada. Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe. No entanto, você pode criar várias sobrecargas de construtor da mesma forma e qualquer outro método.  
  
 Para definir um construtor para uma classe:  
  
```vb  
Class SampleClass  
    Sub New(ByVal s As String)  
        // Add code here.  
    End Sub  
End Class  
```  
  
 Para obter mais informações, consulte: [tempo de vida do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
####  <a name="Destructors"></a>Destruidores  
 Destruidores são usados para destruct instâncias de classes. No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e liberação de memória para os objetos gerenciados no seu aplicativo. No entanto, talvez ainda seja necessário usar destruidores para limpar os recursos não gerenciados que seu aplicativo cria. Pode haver apenas um destruidor para uma classe.  
  
 Para obter mais informações sobre destruidores e coleta de lixo no .NET Framework, consulte [coleta de lixo](../../../standard/garbagecollection/index.md).  
  
####  <a name="Events"></a> Eventos  
 Eventos permitem que uma classe ou objeto para notificar outras classes ou objetos quando algo interessante ocorre. A classe que envia (ou gera) o evento é chamada de *publisher* e as classes de evento receberem (ou manipularem) são chamadas *assinantes*. Para obter mais informações sobre eventos, como eles são gerados e manipulados, consulte [eventos](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).  
  
-   Para declarar eventos, use o [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).  
  
-   Para gerar eventos, use o [instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
-   Para especificar os manipuladores de eventos usando uma forma declarativa, use o [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrução e o [manipula](../../../visual-basic/language-reference/statements/handles-clause.md) cláusula.  
  
-   Para poder adicionar, remover e alterar o manipulador de eventos associado a um evento dinamicamente, use o [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) e [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) junto com o [operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md).  
  
####  <a name="NestedClasses"></a>Classes aninhadas  
 Uma classe definida dentro de outra classe é chamada *aninhada*. Por padrão, a classe aninhada é particular.  
  
```vb  
Class Container  
    Class Nested  
    ' Add code here.  
    End Class  
End Class  
```  
  
 Para criar uma instância da classe aninhada, use o nome da classe de contêiner, seguido do ponto e, em seguida, seguido do nome da classe aninhada:  
  
```vb  
Dim nestedInstance As Container.Nested = New Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a>Modificadores de acesso e níveis de acesso  
 Todas as classes e membros de classe podem especificar o nível de acesso que eles fornecem a outras classes usando *modificadores de acesso*.  
  
 Os modificadores de acesso a seguir estão disponíveis:  
  
|Modificador de Visual Basic|Definição|  
|---------------------------|----------------|  
|[Público](../../../visual-basic/language-reference/modifiers/public.md)|O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.|  
|[Privado](../../../visual-basic/language-reference/modifiers/private.md)|O tipo ou membro só pode ser acessado pelo código na mesma classe.|  
|[Protegido](../../../visual-basic/language-reference/modifiers/protected.md)|O tipo ou membro só pode ser acessado pelo código na mesma classe ou em uma classe derivada.|  
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.|  
|`Protected Friend`|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, ou por qualquer classe derivada em outro assembly.|  
  
 Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
###  <a name="InstantiatingClasses"></a>Instanciação de Classes  
 Para criar um objeto, você precisa criar uma instância de uma classe, ou criar uma instância da classe.  
  
```vb  
Dim sampleObject as New SampleClass()  
```  
  
 Depois de instanciar uma classe, você pode atribuir valores a propriedades e campos de instância e chamar os métodos da classe.  
  
```vb  
' Set a property value.  
sampleObject.SampleProperty = "Sample String"  
' Call a method.  
sampleObject.SampleMethod()  
```  
  
 Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:  
  
```vb  
Dim sampleObject = New SampleClass With   
    {.FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 Para obter mais informações, consulte:  
  
-   [Operador New](../../../visual-basic/language-reference/operators/new-operator.md)  
  
-   [Inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
  
###  <a name="Static"></a>Classes compartilhadas e membros  
 Um membro compartilhado da classe é uma propriedade, procedimento ou campo que é compartilhado por todas as instâncias de uma classe.  
  
 Para definir um membro compartilhado:  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 Para acessar o membro compartilhado, use o nome da classe sem criar um objeto dessa classe:  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 Módulos compartilhados no Visual Basic somente membros compartilhados e não podem ser instanciados. Membros compartilhados também não é possível acessar métodos, campos ou propriedades não compartilhados  
  
 Para obter mais informações, consulte:  
  
-   [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
###  <a name="AnonymousTypes"></a>Tipos anônimos  
 Tipos anônimos permitem que você crie objetos sem escrever uma definição de classe para o tipo de dados. Em vez disso, o compilador gera uma classe para você. A classe não tem nenhum nome utilizável e contém as propriedades que você especificar no declarar o objeto.  
  
 Para criar uma instância de um tipo anônimo:  
  
```vb  
' sampleObject is an instance of a simple anonymous type.  
Dim sampleObject =   
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 Para obter mais informações, consulte: [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
##  <a name="Inheritance"></a>Herança  
 Herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento que é definido em outra classe. A classe cujos membros são herdados é chamada a *classe base*, e a classe que herda os membros é chamada de *classe derivada*. No entanto, todas as classes no Visual Basic implicitamente herdam o <xref:System.Object>classe que oferece suporte a hierarquia de classe do .NET e fornece serviços de nível baixo para todas as classes.</xref:System.Object>  
  
> [!NOTE]
>  Visual Basic não dá suporte a várias heranças. Ou seja, você pode especificar apenas uma classe base para uma classe derivada.  
  
 Para herdar de uma classe base:  
  
```vb  
Class DerivedClass  
    Inherits BaseClass  
End Class  
```  
  
 Por padrão, todas as classes podem ser herdadas. No entanto, você pode especificar se uma classe não deve ser usada como uma classe base ou cria uma classe que pode ser usada como apenas uma classe base.  
  
 Para especificar que uma classe não pode ser usada como uma classe base:  
  
```vb  
NotInheritable Class SampleClass  
End Class  
```  
  
 Para especificar que uma classe pode ser usada como uma classe base apenas e não pode ser instanciada:  
  
```vb  
MustInherit Class BaseClass  
End Class  
```  
  
 Para obter mais informações, consulte:  
  
-   [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
  
-   [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
  
-   [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
  
###  <a name="Overriding"></a>Substituindo membros  
 Por padrão, uma classe derivada herda todos os membros de sua classe base. Se você quiser alterar o comportamento do membro herdado, você precisa substituí-la. Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.  
  
 Seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:  
  
|Modificador de Visual Basic|Definição|  
|---------------------------|----------------|  
|[Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)|Permite que um membro da classe a ser substituído em uma classe derivada.|  
|[Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)|Substitui um membro (substituível) virtual definido na classe base.|  
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Impede que um membro que está sendo substituído em uma classe herdada.|  
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Requer que um membro da classe a ser substituído na classe derivada.|  
|[Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)|Oculta um membro herdado de uma classe base|  
  
##  <a name="Interfaces"></a>Interfaces  
 Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos. Mas, diferentemente das classes, interfaces não fornecem implementação. Eles são implementados por classes e definidos como entidades separadas de classes. Uma interface representa um contrato que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.  
  
 Para definir uma interface:  
  
```vb  
Public Interface ISampleInterface  
    Sub DoSomething()  
End Interface  
```  
  
 Para implementar uma interface em uma classe:  
  
```vb  
Class SampleClass  
    Implements ISampleInterface  
    Sub DoSomething  
        ' Method implementation.  
    End Sub  
End Class  
```  
  
 Para obter mais informações, consulte:  
  
-   [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
  
-   [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)  
  
##  <a name="Generics"></a>Classes genéricas  
 Classes, estruturas, interfaces e métodos do .NET Framework podem incluir *parâmetros de tipo* que definem os tipos de objetos que podem armazenar ou usar. O exemplo mais comum de genéricos é uma coleção, onde você pode especificar o tipo de objeto a ser armazenado em uma coleção.  
  
 Para definir uma classe genérica:  
  
```vb  
Class SampleGeneric(Of T)  
    Public Field As T  
End Class  
```  
  
 Para criar uma instância de uma classe genérica:  
  
```vb  
Dim sampleObject As New SampleGeneric(Of String)  
sampleObject.Field = "Sample string"  
```  
  
 Para obter mais informações, consulte:  
  
-   [Genéricos](https://msdn.microsoft.com/library/ms172192)  
  
-   [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
  
##  <a name="Delegates"></a>Delegados  
 A *delegar* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível. Você pode invocar (ou chamar) o método por meio do delegado. Delegados são usados para passar métodos como argumentos a outros métodos.  
  
> [!NOTE]
>  Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados. Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [eventos](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).  
  
 Para criar um delegado:  
  
```vb  
Delegate Sub SampleDelegate(ByVal str As String)  
```  
  
 Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:  
  
```vb  
Class SampleClass  
    ' Method that matches the SampleDelegate signature.  
    Sub SampleSub(ByVal str As String)  
        ' Add code here.  
    End Sub  
    ' Method that instantiates the delegate.  
    Sub SampleDelegateSub()  
        Dim sd As SampleDelegate = AddressOf SampleSub  
        sd("Sample string")  
    End Sub  
End Class  
```  
  
 Para obter mais informações, consulte:  
  
-   [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
  
-   [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
-   [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de programação em Visual Basic](../../../visual-basic/programming-guide/index.md)
