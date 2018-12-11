---
title: Programação orientada a objeto (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 058d8b932e50f784d4a5cefa9fadfb31953687f0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153912"
---
# <a name="object-oriented-programming-visual-basic"></a>Programação orientada a objeto (Visual Basic)

Visual Basic oferece suporte completo para a programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.

 *Encapsulamento* significa que um grupo de propriedades, métodos e outros membros relacionados é tratado como uma única unidade ou objeto.

 *Herança* descreve a capacidade de criar novas classes com base em uma classe existente.

 *Polimorfismo* significa que você pode ter várias classes que podem ser usadas de forma intercambiável, ainda que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.

 Esta seção descreve os seguintes conceitos:

- [Classes e objetos](#classes-and-objects)
  - [Membros de classe](#class-members)
    - [Propriedades e campos](#properties-and-fields)
    - [Métodos](#methods)
    - [Construtores](#constructors)
    - [Destruidores](#destructors)
    - [Eventos](#events)
    - [Classes aninhadas](#nested-classes)
  - [Modificadores de acesso e níveis de acesso](#access-modifiers-and-access-levels)
    - [Instanciando classes](#instantiating-classes)
    - [Classes compartilhadas e membros](#shared-classes-and-members)
    - [Tipos anônimos](#anonymous-types)
- [Herança](#inheritance)
  - [Substituindo membros](#overriding-members)
- [Interfaces](#interfaces)
- [Genéricos](#generics)
- [Delegados](#delegates)

## <a name="classes-and-objects"></a>Classes e objetos

Os termos *classe* e *objeto* às vezes são usados de forma intercambiável, mas, na verdade, as classes descrevem o *tipo* dos objetos, enquanto os objetos são *instâncias* utilizáveis das classes. Sendo assim, o ato de criar um objeto é chamado de *instanciação*. Usando a analogia da uma planta, uma classe é a planta e um objeto é a construção feita com base naquela planta.

Para definir uma classe:

```vb
Class SampleClass
End Class
```

Visual Basic também fornece uma versão light de classes chamadas *estruturas* que são úteis quando você precisa criar uma matriz grande de objetos e desejar consumir muita memória para fazer isso.

Para definir uma estrutura:

```vb
Structure SampleStructure
End Structure
```

Para obter mais informações, consulte:

- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Membros de classe

Cada classe tem diferentes *membros de classe* que incluem propriedades que descrevem dados da classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.

#### <a name="properties-and-fields"></a>Propriedades e campos

Os campos e as propriedades representam as informações que um objeto contém. Os campos são como variáveis, porque podem ser lidos ou definidos de forma direta.

Para definir um campo:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

As propriedades têm procedimentos de obter e definir, que oferecem mais controle sobre como os valores são definidos ou retornados.

Visual Basic permite que você crie um campo particular para armazenar o valor da propriedade ou usar chamadas propriedades implementadas automaticamente que criam este campo automaticamente em segundo plano e fornecem a lógica básica para os procedimentos de propriedade.

Para definir uma propriedade autoimplementada:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Se você precisar executar operações adicionais para ler e gravar o valor da propriedade, defina um campo para armazenar o valor da propriedade e forneça a lógica básica para armazenar e recuperá-la:

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

A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade. No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas. No Visual Basic, você pode usar `ReadOnly` e `WriteOnly` palavras-chave. No entanto, propriedades autoimplementadas não podem ser somente leitura ou somente gravação.

Para obter mais informações, consulte:

- [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Métodos

 Um *método* é uma ação que um objeto pode executar.

> [!NOTE]
> No Visual Basic, há duas maneiras de criar um método: o `Sub` instrução é usada se o método não retorna um valor; o `Function` instrução é usada se um método retorna um valor.

Para definir um método de uma classe:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Uma classe pode ter várias implementações ou *sobrecargas*, do mesmo método que diferem quanto ao número de parâmetros ou tipos de parâmetro.

Para sobrecarregar um método:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Na maioria dos casos, você declara um método dentro de uma definição de classe. No entanto, o Visual Basic também suporta *métodos de extensão* que permitem adicionar métodos a uma classe existente fora da definição real da classe.

Para obter mais informações, consulte:

- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Construtores

Construtores são métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado. Os construtores normalmente inicializam os membros de dados do novo objeto. Um construtor pode ser executado apenas uma vez quando uma classe é criada. Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe. No entanto, é possível criar várias sobrecargas de construtor da mesma forma que é feita para qualquer outro método.

Para definir um construtor para uma classe:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Para obter mais informações, consulte: [Tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruidores

Destruidores são usados para destruir instâncias de classes. No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e a liberação de memória para os objetos gerenciados em seu aplicativo. No entanto, talvez ainda seja necessário usar os destruidores para limpar recursos não gerenciados que seu aplicativo criar. Pode haver apenas um destruidor para uma classe.

Para obter mais informações sobre os destruidores e a coleta de lixo no .NET Framework, consulte [Coleta de lixo](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Eventos

Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer. A classe que envia (ou aciona) o evento é chamada de *editor* e as classes que recebem (ou manipulam) os eventos são chamadas *assinantes*. Para obter mais informações sobre os eventos e como eles são gerados e manipulados, consulte [Eventos](../../../standard/events/index.md).

- Para declarar eventos, use o [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).

- Para gerar eventos, use o [instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Para especificar os manipuladores de eventos usando uma forma declarativa, use o [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrução e o [manipula](../../../visual-basic/language-reference/statements/handles-clause.md) cláusula.

- Para poder adicionar, remover e alterar o manipulador de eventos associado com um evento dinamicamente, use o [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) e [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) junto com o [AddressOf Operador](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Classes aninhadas

Uma classe definida dentro de outra classe é chamada de *aninhada*. Por padrão, a classe aninhada é particular.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Para criar uma instância da classe aninhada, use o nome da classe de contêiner seguido pelo ponto e, em seguida, seguido pelo nome da classe aninhada:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modificadores de acesso e níveis de acesso

Todas as classes e membros de classe podem especificar o nível de acesso que fornecem a outras classes usando *modificadores de acesso*.

Os modificadores de acesso a seguir estão disponíveis:

|Modificador do Visual Basic|Definição|
|---------------------------|----------------|
|[Público](../../../visual-basic/language-reference/modifiers/public.md)|O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.|
|[Privado](../../../visual-basic/language-reference/modifiers/private.md)|O tipo ou membro pode ser acessado somente pelo código na mesma classe.|
|[Protegido](../../../visual-basic/language-reference/modifiers/protected.md)|O tipo ou membro pode ser acessado somente pelo código na mesma classe ou em uma classe derivada.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.|
|`Protected Friend`|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly ou por qualquer classe derivada em outro assembly.|

Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Instanciando classes

Para criar um objeto, você precisa instanciar uma classe ou criar uma instância da classe.

```vb
Dim sampleObject as New SampleClass()
```

Após instanciar uma classe, você pode atribuir valores às propriedades e campos da instância e invocar métodos da classe.

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

- [Operador New](../../../visual-basic/language-reference/operators/new-operator.md)
- [Inicializadores de objeto: Tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Classes compartilhadas e membros

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

 Módulos compartilhados no Visual Basic compartilharam apenas membros e não podem ser instanciados. Membros compartilhados também não é possível acessar métodos, campos ou propriedades não compartilhados

 Para obter mais informações, consulte:

- [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)
- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Tipos anônimos

Os tipos anônimos permitem criar objetos sem escrever uma definição de classe para o tipo de dados. Em vez disso, o compilador gera uma classe para você. A classe não tem nenhum nome utilizável e contém as propriedades que você especificar ao declarar o objeto.

Para criar uma instância de um tipo anônimo:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Para obter mais informações, consulte: [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Herança

A herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento definido em outras classes. A classe cujos membros são herdados é chamada *classe base* e a classe que herda esses membros é chamada *classe derivada*. No entanto, todas as classes no Visual Basic implicitamente herdam o <xref:System.Object> classe que dá suporte a hierarquia de classes do .NET e fornece serviços de nível baixo para todas as classes.

> [!NOTE]
> Visual Basic não dá suporte a várias heranças. Ou seja, você pode especificar apenas uma classe base para uma classe derivada.

Para herdar de uma classe base:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Por padrão, todas as classes podem ser herdadas. No entanto, é possível especificar se uma classe não deve ser usada como classe base ou criar uma classe que possa ser usada apenas como classe base.

Para especificar que uma classe não pode ser usada como classe base:

```vb
NotInheritable Class SampleClass
End Class
```

Para especificar que uma classe pode ser usada apenas como classe base e não pode ser instanciada:

```vb
MustInherit Class BaseClass
End Class
```

Para obter mais informações, consulte:

- [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Substituindo membros

Por padrão, uma classe derivada herda todos os membros de sua classe base. Se quiser alterar o comportamento do membro herdado, você precisa substituí-la. Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.

Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:

|Modificador do Visual Basic|Definição|
|---------------------------|----------------|
|[Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)|Permite que um membro de classe seja substituído em uma classe derivada.|
|[Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)|Substitui um membro virtual (substituível) definido na classe base.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Impede que um membro que está sendo substituído em uma classe herdada.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Requer que um membro de classe seja substituído na classe derivada.|
|[Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)|Oculta um membro herdado de uma classe base|

## <a name="interfaces"></a>Interfaces

Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos. Mas, diferente das classes, as interfaces não fornecem implementação. Elas são implementadas por classes e definidas como entidades separadas das classes. Uma interface representa um contrato, no sentido em que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.

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

- [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a>Genéricos

Classes, estruturas, interfaces e métodos no .NET podem incluir *parâmetros de tipo* que definem tipos de objetos que podem armazenar ou usar. O exemplo mais comum dos genéricos é uma coleção, em que você pode especificar o tipo dos objeto a serem armazenados em uma coleção.

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

- [Genéricos](../../../standard/generics/index.md)
- [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegados

 Um *delegado* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível. Você pode invocar (ou chamar) o método através do delegado. Delegados são usados para passar métodos como argumentos a outros métodos.

> [!NOTE]
> Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados. Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [Eventos](../../../standard/events/index.md).

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

- [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Consulte também

- [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)
