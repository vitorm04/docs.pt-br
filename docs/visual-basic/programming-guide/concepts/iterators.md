---
title: "Iteradores (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Iteradores (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um *iterador* pode ser usado para percorrer coleções, como listas e matrizes.  
  
 Um método iterador ou `get` acessador realiza uma iteração personalizada em uma coleção. Usa um método iterador o [Gerar](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento por vez. Quando um `Yield` instrução for atingida, o local atual no código será lembrado. Execução é reiniciada a partir desse local na próxima vez em que a função de iterador é chamada.  
  
 Consumir um iterador no código do cliente usando um [para cada uma... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução, ou usando uma consulta LINQ.  
  
 No exemplo a seguir, a primeira iteração do `For Each` loop faz a execução continue no `SomeNumbers` método iterador até a primeira `Yield` instrução seja atingida. Essa iteração retorna um valor de 3, e o local atual no método iterador é mantido. Na próxima iteração do loop, a execução no método iterador continuará de onde parou, parando novamente quando ele atinge um `Yield` instrução. Essa iteração retorna um valor de 5, e o local atual no método iterador é mantido novamente. O loop termina quando o final do método iterador é atingido.  
  
```vb  
Sub Main()  
    For Each number As Integer In SomeNumbers()  
        Console.Write(number & " ")  
    Next  
    ' Output: 3 5 8  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function SomeNumbers() As System.Collections.IEnumerable  
    Yield 3  
    Yield 5  
    Yield 8  
End Function  
```  
  
 O tipo de retorno de um método iterador ou `get` acessador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Você pode usar um `Exit Function` ou `Return` instrução para finalizar a iteração.  
  
 Uma função de iterador do Visual Basic ou `get` acessador declaração inclui um [iterador](../../../visual-basic/language-reference/modifiers/iterator.md) modificador.  
  
 Iteradores foram introduzidos no Visual Basic no Visual Studio 2012.  
  
 **Neste tópico**  
  
-   [Iterador simples](#BKMK_SimpleIterator)  
  
-   [Criando uma classe de coleção](#BKMK_CollectionClass)  
  
-   [Blocos try](#BKMK_TryBlocks)  
  
-   [Métodos anônimos](#BKMK_AnonymousMethods)  
  
-   [Usando iteradores com uma lista genérica](#BKMK_GenericList)  
  
-   [Informações de sintaxe](#BKMK_SyntaxInformation)  
  
-   [Implementação técnica](#BKMK_Technical)  
  
-   [Uso de iteradores](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Para todos os exemplos no tópico exceto o exemplo simples iterador, incluem [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruções para o `System.Collections` e `System.Collections.Generic` namespaces.  
  
##  <a name="BKMK_SimpleIterator"></a> Iterador simples  
 O exemplo a seguir tem um único `Yield` que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. Em `Main`, cada iteração de `For Each` corpo da instrução cria uma chamada para a função do iterador, que passa para o próximo `Yield` instrução.  
  
```vb  
Sub Main()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    ' Output: 6 8 10 12 14 16 18  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As System.Collections.Generic.IEnumerable(Of Integer)  
  
    ' Yield even numbers in the range.  
    For number As Integer = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
##  <a name="BKMK_CollectionClass"></a> Criando uma classe de coleção  
 No exemplo a seguir, a `DaysOfTheWeek` classe implementa o <xref:System.Collections.IEnumerable> interface, que requer um <xref:System.Collections.IEnumerable.GetEnumerator%2A> método. O compilador chama implicitamente o `GetEnumerator` método, que retorna um <xref:System.Collections.IEnumerator>.  
  
 O `GetEnumerator` método retorna cada cadeia de caracteres de uma por vez usando o `Yield` instrução e um `Iterator` modificador é na declaração da função.  
  
```vb  
Sub Main()  
    Dim days As New DaysOfTheWeek()  
    For Each day As String In days  
        Console.Write(day & " ")  
    Next  
    ' Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey()  
End Sub  
  
Private Class DaysOfTheWeek  
    Implements IEnumerable  
  
    Public days =  
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        ' Yield each day of the week.  
        For i As Integer = 0 To days.Length - 1  
            Yield days(i)  
        Next  
    End Function  
End Class  
```  
  
 O exemplo a seguir cria um `Zoo` classe que contém uma coleção de animais.  
  
 O `For Each` instrução que faz referência à instância de classe \(`theZoo`\) chama implicitamente o `GetEnumerator` método. O `For Each` instruções que fazem referência a `Birds` e `Mammals` uso de propriedades a `AnimalsForType` chamado o método iterador.  
  
```vb  
Sub Main()  
    Dim theZoo As New Zoo()  
  
    theZoo.AddMammal("Whale")  
    theZoo.AddMammal("Rhinoceros")  
    theZoo.AddBird("Penguin")  
    theZoo.AddBird("Warbler")  
  
    For Each name As String In theZoo  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros Penguin Warbler  
  
    For Each name As String In theZoo.Birds  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Penguin Warbler  
  
    For Each name As String In theZoo.Mammals  
        Console.Write(name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: Whale Rhinoceros  
  
    Console.ReadKey()  
End Sub  
  
Public Class Zoo  
    Implements IEnumerable  
  
    ' Private members.  
    Private animals As New List(Of Animal)  
  
    ' Public methods.  
    Public Sub AddMammal(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})  
    End Sub  
  
    Public Sub AddBird(ByVal name As String)  
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})  
    End Sub  
  
    Public Iterator Function GetEnumerator() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        For Each theAnimal As Animal In animals  
            Yield theAnimal.Name  
        Next  
    End Function  
  
    ' Public members.  
    Public ReadOnly Property Mammals As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Mammal)  
        End Get  
    End Property  
  
    Public ReadOnly Property Birds As IEnumerable  
        Get  
            Return AnimalsForType(Animal.TypeEnum.Bird)  
        End Get  
    End Property  
  
    ' Private methods.  
    Private Iterator Function AnimalsForType( _  
    ByVal type As Animal.TypeEnum) As IEnumerable  
        For Each theAnimal As Animal In animals  
            If (theAnimal.Type = type) Then  
                Yield theAnimal.Name  
            End If  
        Next  
    End Function  
  
    ' Private class.  
    Private Class Animal  
        Public Enum TypeEnum  
            Bird  
            Mammal  
        End Enum  
  
        Public Property Name As String  
        Public Property Type As TypeEnum  
    End Class  
End Class  
```  
  
##  <a name="BKMK_TryBlocks"></a> Blocos try  
 O Visual Basic permite um `Yield` instrução o `Try` Bloco de um [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). Um `Try` bloco tem um `Yield` instrução pode ter `Catch` bloqueia e pode ter um `Finally` bloco.  
  
 O exemplo a seguir inclui `Try`, `Catch`, e `Finally` blocos em uma função de iterador. O `Finally` bloco na função iterador é executado antes do `For Each` termina de iteração.  
  
```vb  
Sub Main()  
    For Each number As Integer In Test()  
        Console.WriteLine(number)  
    Next  
    Console.WriteLine("For Each is done.")  
  
    ' Output:  
    '  3  
    '  4  
    '  Something happened. Yields are done.  
    '  Finally is called.  
    '  For Each is done.  
    Console.ReadKey()  
End Sub  
  
Private Iterator Function Test() As IEnumerable(Of Integer)  
    Try  
        Yield 3  
        Yield 4  
        Throw New Exception("Something happened. Yields are done.")  
        Yield 5  
        Yield 6  
    Catch ex As Exception  
        Console.WriteLine(ex.Message)  
    Finally  
        Console.WriteLine("Finally is called.")  
    End Try  
End Function  
```  
  
 Um `Yield` instrução não pode estar dentro de uma `Catch` bloco ou uma `Finally` bloco.  
  
 Se o `For Each` corpo \(em vez do método iterador\) gera uma exceção, um `Catch` bloco na função iterador não é executado, mas um `Finally` bloco na função iterador é executado. Um `Catch` bloco dentro de uma função de iterador captura somente exceções que ocorrem dentro da função de iterador.  
  
##  <a name="BKMK_AnonymousMethods"></a> Métodos anônimos  
 No Visual Basic, uma função anônima pode ser uma função de iterador. O exemplo a seguir ilustra isso.  
  
```vb  
Dim iterateSequence = Iterator Function() _  
                      As IEnumerable(Of Integer)  
                          Yield 1  
                          Yield 2  
                      End Function  
  
For Each number As Integer In iterateSequence()  
    Console.Write(number & " ")  
Next  
' Output: 1 2  
Console.ReadKey()  
```  
  
 O exemplo a seguir tem um método iterador não valida os argumentos. O método retorna o resultado de um iterador anônimo que descreve os elementos da coleção.  
  
```vb  
Sub Main()  
    For Each number As Integer In GetSequence(5, 10)  
        Console.Write(number & " ")  
    Next  
    ' Output: 5 6 7 8 9 10  
    Console.ReadKey()  
End Sub  
  
Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _  
As IEnumerable  
    ' Validate the arguments.  
    If low < 1 Then  
        Throw New ArgumentException("low is too low")  
    End If  
    If high > 140 Then  
        Throw New ArgumentException("high is too high")  
    End If  
  
    ' Return an anonymous iterator function.  
    Dim iterateSequence = Iterator Function() As IEnumerable  
                              For index = low To high  
                                  Yield index  
                              Next  
                          End Function  
    Return iterateSequence()  
End Function  
```  
  
 Se a validação estiver dentro da função de iterador, a validação não pode ser executada antes do início da primeira iteração do `For Each` corpo.  
  
##  <a name="BKMK_GenericList"></a> Usando iteradores com uma lista genérica  
 No exemplo a seguir, a `Stack(Of T)` classe genérica implementa o <xref:System.Collections.Generic.IEnumerable%601> interface genérica. O `Push` método atribui valores a uma matriz do tipo `T`. O <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> método retorna os valores da matriz usando o `Yield` instrução.  
  
 Além de genérica <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> método, não genérico <xref:System.Collections.IEnumerable.GetEnumerator%2A> método também deve ser implementado. Isso ocorre porque <xref:System.Collections.Generic.IEnumerable%601> herda de <xref:System.Collections.IEnumerable>. A implementação não genérico adia a implementação genérica.  
  
 O exemplo usa os iteradores nomeados para dar suporte a várias maneiras de iterar a mesma coleção de dados. Chamado iteradores são o `TopToBottom` e `BottomToTop` Propriedades e o `TopN` método.  
  
 O `BottomToTop` declaração de propriedade inclui o `Iterator` palavra\-chave.  
  
```vb  
Sub Main()  
    Dim theStack As New Stack(Of Integer)  
  
    ' Add items to the stack.  
    For number As Integer = 0 To 9  
        theStack.Push(number)  
    Next  
  
    ' Retrieve items from the stack.  
    ' For Each is allowed because theStack implements  
    ' IEnumerable(Of Integer).  
    For Each number As Integer In theStack  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    ' For Each is allowed, because theStack.TopToBottom  
    ' returns IEnumerable(Of Integer).  
    For Each number As Integer In theStack.TopToBottom  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3 2 1 0  
  
    For Each number As Integer In theStack.BottomToTop  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 0 1 2 3 4 5 6 7 8 9   
  
    For Each number As Integer In theStack.TopN(7)  
        Console.Write("{0} ", number)  
    Next  
    Console.WriteLine()  
    ' Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey()  
End Sub  
  
Public Class Stack(Of T)  
    Implements IEnumerable(Of T)  
  
    Private values As T() = New T(99) {}  
    Private top As Integer = 0  
  
    Public Sub Push(ByVal t As T)  
        values(top) = t  
        top = top + 1  
    End Sub  
  
    Public Function Pop() As T  
        top = top - 1  
        Return values(top)  
    End Function  
  
    ' This function implements the GetEnumerator method. It allows  
    ' an instance of the class to be used in a For Each statement.  
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _  
        Implements IEnumerable(Of T).GetEnumerator  
  
        For index As Integer = top - 1 To 0 Step -1  
            Yield values(index)  
        Next  
    End Function  
  
    Public Iterator Function GetEnumerator1() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
  
        Yield GetEnumerator()  
    End Function  
  
    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)  
        Get  
            Return Me  
        End Get  
    End Property  
  
    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)  
        Get  
            For index As Integer = 0 To top - 1  
                Yield values(index)  
            Next  
        End Get  
    End Property  
  
    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _  
        As IEnumerable(Of T)  
  
        ' Return less than itemsFromTop if necessary.  
        Dim startIndex As Integer =  
            If(itemsFromTop >= top, 0, top - itemsFromTop)  
  
        For index As Integer = top - 1 To startIndex Step -1  
            Yield values(index)  
        Next  
    End Function  
End Class  
  
```  
  
##  <a name="BKMK_SyntaxInformation"></a> Informações de sintaxe  
 Um iterador pode ocorrer como um método ou `get` acessador. Um iterador não pode ocorrer em um evento, construtor de instância, construtor estático ou destruidor static.  
  
 Deve existir uma conversão implícita do tipo de expressão no `Yield` instrução para o tipo de retorno do iterador.  
  
 No Visual Basic, um iterador não pode ter nenhum `ByRef` parâmetros.  
  
 No Visual Basic, "Yield" não é uma palavra reservada e tem um significado especial somente quando ela é usada em um `Iterator` método ou `get` acessador.  
  
##  <a name="BKMK_Technical"></a> Implementação técnica  
 Embora escrever um iterador como um método, o compilador converte em uma classe aninhada isto é, na verdade, uma máquina de estado. Essa classe mantém controle sobre a posição do iterador como tempo o `For Each...Next` continua loop no código do cliente.  
  
 Para ver o que o compilador faz, você pode usar a ferramenta Ildasm.exe para exibir o código Microsoft intermediate language que é gerado para um método iterador.  
  
 Quando você cria um iterador para um [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md), você não precisa implementar todo <xref:System.Collections.IEnumerator> interface. Quando o compilador detecta o iterador, ela gera automaticamente o `Current`, `MoveNext`, e `Dispose` métodos de <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> interface.  
  
 Em cada iteração sucessiva o `For Each…Next` loop \(ou a chamada direta para `IEnumerator.MoveNext`\), o corpo de código do iterador próxima continua após anterior `Yield` instrução. Em seguida, ele continuará até a próxima `Yield` instrução até o final do corpo do iterador é atingido, ou até que um `Exit Function` ou `Return` declaração é encontrada.  
  
 Iteradores não oferecem suporte a <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=fullName> método. Para iterar novamente desde o início, você deve obter um iterador de novo.  
  
 Para obter informações adicionais, consulte o [Especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification.md).  
  
##  <a name="BKMK_UseOfIterators"></a> Uso de iteradores  
 Iteradores que você possa manter a simplicidade de um `For Each` loop quando precisar usar código complexo para preencher uma seqüência de lista. Isso pode ser útil quando você deseja fazer o seguinte:  
  
-   Modificar a seqüência de lista após a primeira `For Each` iteração de loop.  
  
-   Evite o carregamento totalmente uma grande lista antes da primeira iteração de um `For Each` loop. Um exemplo é uma busca paginada para carregar um lote de linhas da tabela. Outro exemplo é o <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> método, que implementa os iteradores dentro do .NET Framework.  
  
-   Encapsule a criação da lista no iterador. No método iterador, você pode criar a lista e, em seguida, gerar cada resultado em um loop.  
  
## Consulte também  
 <xref:System.Collections.Generic>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Instrução Yield](../../../visual-basic/language-reference/statements/yield-statement.md)   
 [Iterador](../../../visual-basic/language-reference/modifiers/iterator.md)