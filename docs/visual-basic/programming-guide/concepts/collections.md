---
title: "Coleções (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b3c8de3e22075d576f86bcd4eb599946740ebe16
ms.lasthandoff: 03/13/2017

---
# <a name="collections-visual-basic"></a>Coleções (Visual Basic)
Para muitos aplicativos, você deseja criar e gerenciar grupos de objetos relacionados. Há duas maneiras para agrupar objetos: criando arrays de objetos e criando coleções de objetos.  
  
 As matrizes são mais úteis para criar e trabalhar com um número fixo de objetos fortemente tipados. Para obter informações sobre matrizes, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 As coleções fornecem uma maneira mais flexível de trabalhar com grupos de objetos. Ao contrário de matrizes, o grupo de objetos que você trabalha pode crescer e reduzir dinamicamente conforme as necessidades do aplicativo mudam. Para algumas coleções, você pode atribuir uma chave para qualquer objeto que você coloque na coleção para que você possa recuperar rapidamente o objeto usando a chave.  
  
 Uma coleção é uma classe, portanto você deve declarar uma instância da classe antes de adicionar elementos à coleção.  
  
 Se a coleção contém elementos de apenas um tipo de dados, você pode usar uma das classes de <xref:System.Collections.Generic?displayProperty=fullName>namespace.</xref:System.Collections.Generic?displayProperty=fullName> Uma coleção genérica impõe segurança de tipo para que nenhum outro tipo de dados pode ser adicionado a ele. Quando você recupera um elemento de uma coleção genérica, você não precisa determinar seu tipo de dados ou convertê-lo.  
  
> [!NOTE]
>  Para os exemplos neste tópico, incluir [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruções para o `System.Collections.Generic` e `System.Linq` namespaces.  
  
 **Neste tópico**  
  
-   [Usando uma coleção Simple](#BKMK_SimpleCollection)  
  
-   [Tipos de coleções](#BKMK_KindsOfCollections)  
  
    -   [Classes de System.Collections.Generic](#BKMK_Generic)  
  
    -   [Classes de System.Collections.Concurrent](#BKMK_Concurrent)  
  
    -   [Classes de System. Collections](#BKMK_Collections)  
  
    -   [Classe de coleção do Visual Basic](#BKMK_VisualBasic)  
  
-   [Implementação de uma coleção de pares chave/valor](#BKMK_KeyValuePairs)  
  
-   [Usando LINQ para acessar uma coleção](#BKMK_LINQ)  
  
-   [Classificando uma coleção](#BKMK_Sorting)  
  
-   [Definindo uma coleção personalizada](#BKMK_CustomCollection)  
  
-   [Iteradores](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Usando uma coleção Simple  
 Os exemplos nesta seção usam genérica <xref:System.Collections.Generic.List%601>classe, que permite que você trabalhe com uma lista com rigidez de tipos de objetos.</xref:System.Collections.Generic.List%601>  
  
 O exemplo a seguir cria uma lista de cadeias de caracteres e, em seguida, percorre as cadeias de caracteres usando um [para cada uma... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução.  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Se o conteúdo de uma coleção forem conhecido antecipadamente, você pode usar um *inicializador de coleção* para inicializar a coleção. Para obter mais informações, consulte [inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 O exemplo a seguir é igual ao exemplo anterior, exceto um inicializador de coleção é usado para adicionar elementos à coleção.  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Você pode usar um [para... Próximo](../../../visual-basic/language-reference/statements/for-next-statement.md) instrução em vez de um `For Each` instrução para iterar através de uma coleção. Você pode fazer isso acessando os elementos da coleção por posição de índice. O índice dos elementos começa em 0 e termina em menos de 1 a contagem do elemento.  
  
 O exemplo a seguir itera através dos elementos de uma coleção usando `For…Next` em vez de `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 O exemplo a seguir remove um elemento da coleção especificando o objeto a ser removido.  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 O exemplo a seguir remove elementos de uma lista genérica. Em vez de um `For Each` instrução, um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) instrução que itera em ordem decrescente é usada. Isso ocorre porque o <xref:System.Collections.Generic.List%601.RemoveAt%2A>método faz com que elementos após um elemento removido para ter um valor de índice mais baixo.</xref:System.Collections.Generic.List%601.RemoveAt%2A>  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 Para o tipo dos elementos no <xref:System.Collections.Generic.List%601>você também pode definir sua própria classe.</xref:System.Collections.Generic.List%601> No exemplo a seguir, o `Galaxy` classe que é usada pelo <xref:System.Collections.Generic.List%601>é definido no código.</xref:System.Collections.Generic.List%601>  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a>Tipos de coleções   
 Várias coleções comuns são fornecidas pelo .NET Framework. Cada tipo de coleção é projetado para uma finalidade específica.  
  
 Algumas das classes de coleção comuns são descritas nesta seção:  
  
-   @System.Collections.Genericclasses  
  
-   @System.Collections.Concurrentclasses  
  
-   @System.Collectionsclasses  
  
-   Visual Basic `Collection` classe  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>Classes de System.Collections.Generic  

 Você pode criar uma coleção genérica, usando uma das classes de <xref:System.Collections.Generic>namespace.</xref:System.Collections.Generic> Uma coleção genérica é útil quando cada item na coleção tem os mesmo tipo de dados. Uma coleção genérica impõe tipagem forte, permitindo que apenas os dados desejados tipo a ser adicionado.  
  
 A tabela a seguir lista algumas das classes usadas com frequência da <xref:System.Collections.Generic?displayProperty=fullName>namespace:</xref:System.Collections.Generic?displayProperty=fullName>  
  
|Classe|Descrição|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602>|Representa uma coleção de pares chave/valor que são organizados com base na chave.|  
|<xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601>|Representa uma lista de objetos que podem ser acessados pelo índice. Fornece métodos para pesquisar, classificar e modificar listas.|  
|<xref:System.Collections.Generic.Queue%601></xref:System.Collections.Generic.Queue%601>|Representa o primeiro a entrar, primeiro a sair (PEPS) coleção de objetos.|  
|<xref:System.Collections.Generic.SortedList%602></xref:System.Collections.Generic.SortedList%602>|Representa uma coleção de pares chave/valor que são classificadas por chave com base em associado <xref:System.Collections.Generic.IComparer%601>implementação.</xref:System.Collections.Generic.IComparer%601>|  
|<xref:System.Collections.Generic.Stack%601></xref:System.Collections.Generic.Stack%601>|Representa um último a entrar, primeiro a sair (UEPS) coleção de objetos.|  
  
 Para obter informações adicionais, consulte [comumente usados tipos de coleção](http://msdn.microsoft.com/library/f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55), [selecionando uma classe de coleção](../../../standard/collections/selecting-a-collection-class.md)e <xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>Classes de System.Collections.Concurrent   
 No .NET Framework 4 ou mais recente, as coleções de <xref:System.Collections.Concurrent>namespace fornecem operações thread-safe eficientes para acessar itens de coleção de vários threads.</xref:System.Collections.Concurrent>  
  
 As classes de <xref:System.Collections.Concurrent>namespace deve ser usado em vez dos tipos correspondentes no <xref:System.Collections.Generic?displayProperty=fullName>e <xref:System.Collections?displayProperty=fullName>namespaces sempre que vários threads estão acessando a coleção simultaneamente.</xref:System.Collections?displayProperty=fullName> </xref:System.Collections.Generic?displayProperty=fullName> </xref:System.Collections.Concurrent> Para obter mais informações, consulte [coleção Thread-Safe](../../../standard/collections/threadsafe/index.md) e <xref:System.Collections.Concurrent>.</xref:System.Collections.Concurrent>  
  
 Algumas classes incluídas no <xref:System.Collections.Concurrent>namespace são <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>e <xref:System.Collections.Concurrent.ConcurrentStack%601>.</xref:System.Collections.Concurrent.ConcurrentStack%601> </xref:System.Collections.Concurrent.ConcurrentQueue%601> </xref:System.Collections.Concurrent.ConcurrentDictionary%602> </xref:System.Collections.Concurrent.BlockingCollection%601> </xref:System.Collections.Concurrent>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>Classes de System. Collections    
 As classes de <xref:System.Collections?displayProperty=fullName>namespace não armazenam elementos como especificamente objetos tipados, mas como objetos do tipo `Object`.</xref:System.Collections?displayProperty=fullName>  
  
 Sempre que possível, você deve usar as coleções genéricas no <xref:System.Collections.Generic?displayProperty=fullName>namespace ou o <xref:System.Collections.Concurrent>namespace em vez dos tipos herdados no `System.Collections` namespace.</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName>  
  
 A tabela a seguir lista algumas das classes usadas no `System.Collections` namespace:  
  
|Classe|Descrição|  
|---|---|  
|<xref:System.Collections.ArrayList></xref:System.Collections.ArrayList>|Representa uma matriz de objetos cujo tamanho é aumentado dinamicamente conforme necessário.|  
|<xref:System.Collections.Hashtable></xref:System.Collections.Hashtable>|Representa uma coleção de pares chave-valor organizados com base no código hash da chave.|  
|<xref:System.Collections.Queue></xref:System.Collections.Queue>|Representa o primeiro a entrar, primeiro a sair (PEPS) coleção de objetos.|  
|<xref:System.Collections.Stack></xref:System.Collections.Stack>|Representa um último a entrar, primeiro a sair (UEPS) coleção de objetos.|  
  
 O <xref:System.Collections.Specialized>namespace fornece classes de coleções especializadas e fortemente tipadas, como coleções de sequência apenas e listas vinculadas e dicionários híbridos.</xref:System.Collections.Specialized>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Classe de coleção do Visual Basic  
 Você pode usar o Visual Basic <xref:Microsoft.VisualBasic.Collection>classe para acessar uma coleção de itens, usando qualquer um índice numérico ou um `String` chave.</xref:Microsoft.VisualBasic.Collection> Você pode adicionar itens a um objeto de coleção com ou sem especificar uma chave. Se você adicionar um item sem uma chave, você deve usar seu índice numérico para acessá-lo.  
  
 O Visual Basic `Collection` classe armazena todos seus elementos com o tipo `Object`, portanto, você pode adicionar um item de qualquer tipo de dados. Não há nenhuma segurança contra tipos de dados inapropriados sendo adicionados.  
  
 Quando você usa o Visual Basic `Collection` classe, o primeiro item em uma coleção tem um índice de 1. Isso é diferente de classes de coleção do .NET Framework, para que o índice inicial é 0.  
  
 Sempre que possível, você deve usar as coleções genéricas no <xref:System.Collections.Generic?displayProperty=fullName>namespace ou o <xref:System.Collections.Concurrent>namespace em vez do Visual Basic `Collection` classe</xref:System.Collections.Concurrent> </xref:System.Collections.Generic?displayProperty=fullName>  
  
 Para obter mais informações, consulte <xref:Microsoft.VisualBasic.Collection>.</xref:Microsoft.VisualBasic.Collection>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Implementação de uma coleção de pares chave/valor   
 O <xref:System.Collections.Generic.Dictionary%602>coleção genérica permite que você acesse a elementos em uma coleção usando a chave de cada elemento.</xref:System.Collections.Generic.Dictionary%602> Cada adição ao dicionário consiste em um valor e a chave associada. Recuperar um valor usando sua chave é rápido, porque o `Dictionary` classe é implementada como uma tabela de hash.  
  
 O exemplo a seguir cria um `Dictionary` coleta e itera pelo dicionário usando um `For Each` instrução.  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 Em vez disso, usar um inicializador de coleção para criar o `Dictionary` coleção, você pode substituir o `BuildDictionary` e `AddToDictionary` métodos com o seguinte método.  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 O exemplo a seguir usa o <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A>método e o <xref:System.Collections.Generic.Dictionary%602.Item%2A>propriedade `Dictionary` para localizar rapidamente um item por chave.</xref:System.Collections.Generic.Dictionary%602.Item%2A> </xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> O `Item` propriedade permite que você acesse um item de `elements` coleção usando o `elements(symbol)` código no Visual Basic.  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 O exemplo a seguir usará o <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>método localizar rapidamente um item por chave.</xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a>Usando LINQ para acessar uma coleção  
 LINQ (consulta integrada à linguagem) pode ser usado para acessar coleções. Consultas LINQ fornecem filtragem, classificação e agrupamento de recursos. Para obter mais informações, consulte [Introdução ao LINQ no Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 O exemplo a seguir executa uma consulta LINQ em um genérico `List`. A consulta LINQ retorna uma coleção diferente que contém os resultados.  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a>Classificando uma coleção  
 O exemplo a seguir ilustra um procedimento para uma coleção de classificação. O exemplo classifica instâncias de `Car` classe são armazenados em <xref:System.Collections.Generic.List%601>.</xref:System.Collections.Generic.List%601> O `Car` classe implementa o <xref:System.IComparable%601>interface, que requer que o <xref:System.IComparable%601.CompareTo%2A>método ser implementado.</xref:System.IComparable%601.CompareTo%2A> </xref:System.IComparable%601>  
  
 Cada chamada para o <xref:System.IComparable%601.CompareTo%2A>método faz uma comparação única que é usada para classificação.</xref:System.IComparable%601.CompareTo%2A> Códigos escritos pelo usuário no `CompareTo` método retorna um valor para cada comparação do objeto atual com outro objeto. O valor retornado é menor que zero se o objeto atual é menor do que o outro objeto maior do que zero se o objeto atual é maior do que o outro objeto e zero se eles forem iguais. Isso permite que você defina no código os critérios para maior que, menor que e igual.  
  
 No `ListCars` método, o `cars.Sort()` instrução classifica a lista. Essa chamada para o <xref:System.Collections.Generic.List%601.Sort%2A>método o <xref:System.Collections.Generic.List%601>faz com que o `CompareTo` método a ser chamado automaticamente para o `Car` objetos no `List`.</xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.List%601.Sort%2A>  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a>Definindo uma coleção personalizada  
 Você pode definir uma coleção Implementando a <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Collections.IEnumerable>interface.</xref:System.Collections.IEnumerable> </xref:System.Collections.Generic.IEnumerable%601> Para obter informações adicionais, consulte [enumerando uma coleção](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 Embora seja possível definir uma coleção personalizada, é melhor usar as coleções que estão incluídas no .NET Framework, que são descritos em [tipos de coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) anteriormente neste tópico.  
  
 O exemplo a seguir define uma classe de coleção personalizada chamada `AllColors`. Essa classe implementa o <xref:System.Collections.IEnumerable>interface, que requer que o <xref:System.Collections.IEnumerable.GetEnumerator%2A>método ser implementado.</xref:System.Collections.IEnumerable.GetEnumerator%2A> </xref:System.Collections.IEnumerable>  
  
 O `GetEnumerator` método retorna uma instância da `ColorEnumerator` classe. `ColorEnumerator`implementa o <xref:System.Collections.IEnumerator>interface, que requer que o <xref:System.Collections.IEnumerator.Current%2A>propriedade <xref:System.Collections.IEnumerator.MoveNext%2A>método, e <xref:System.Collections.IEnumerator.Reset%2A>método ser implementado.</xref:System.Collections.IEnumerator.Reset%2A> </xref:System.Collections.IEnumerator.MoveNext%2A> </xref:System.Collections.IEnumerator.Current%2A> </xref:System.Collections.IEnumerator>  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a>Iteradores  
 Um *iterador* é usado para executar uma iteração personalizada em uma coleção. Um iterador pode ser um método ou um `get` acessador. Um iterador usa um [gerar](../../../visual-basic/language-reference/statements/yield-statement.md) instrução para retornar cada elemento da coleção um por vez.  
  
 Chamar um iterador usando um [para cada uma... Próxima](../../../visual-basic/language-reference/statements/for-each-next-statement.md) instrução. Cada iteração de `For Each` loop chama o iterador. Quando um `Yield` instrução for atingida no iterador, uma expressão é retornada e o local atual no código é retido. Execução é reiniciada a partir desse local na próxima vez que o iterador é chamado.  
  
 Para obter mais informações, consulte [iteradores (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 O exemplo a seguir usa um método iterador. O método iterador tem um `Yield` instrução que está dentro de um [para... Próxima](../../../visual-basic/language-reference/statements/for-next-statement.md) loop. No `ListEvenNumbers` cada iteração de um método, o `For Each` corpo da instrução cria uma chamada para o método iterador, que passa para o próximo `Yield` instrução.  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a>Consulte também  
 [Inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [Conceitos de programação (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ paralelo (PLINQ)](http://msdn.microsoft.com/library/3d4d0cd3-bde4-490b-99e7-f4e41be96455)   
 [Coleções e estruturas de dados](../../../standard/collections/index.md)   
 [Criando e manipulando coleções](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069)   
 [Selecionando uma classe de coleção](../../../standard/collections/selecting-a-collection-class.md)   
 [Comparações e ordenações dentro de coleções](../../../standard/collections/comparisons-and-sorts-within-collections.md)   
 [Quando Usar Coleções Genéricas](../../../standard/collections/when-to-use-generic-collections.md)
