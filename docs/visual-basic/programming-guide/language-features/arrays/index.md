---
title: Matrizes no Visual Basic
ms.custom: 
ms.date: 12/06/2017
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: d223ca8b0ff59a13c31fa777e5cb6a97918421c6
ms.sourcegitcommit: 01ea3686e74ff05e4f6de3d8d46dc603d051ec00
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/13/2017
---
# <a name="arrays-in-visual-basic"></a>Matrizes no Visual Basic
Uma matriz é um conjunto de valores, que são chamadas de *elementos*, que são logicamente relacionados uns aos outros. Por exemplo, uma matriz pode consistir no número de alunos em cada nível na escola gramática. cada elemento da matriz é o número de alunos em um único nível. Da mesma forma, uma matriz pode consistir em classificações de um aluno para uma classe. cada elemento da matriz é um único nível.    

É possível variáveis individuais para armazenar cada um dos nossos itens de dados. Por exemplo, se o nosso aplicativo analisa notas de alunos, podemos usar uma variável separada para classificação de cada aluno, como `englishGrade1`, `englishGrade2`, etc. Essa abordagem tem três limitações principais:
- Precisamos saber em tempo de design exatamente quantas notas que temos que tratar.
- Manipular grandes números de notas rapidamente se torna difícil de manusear. Isso torna um aplicativo muito mais propensos a erros graves.
- É difícil de manter. Cada nível novo que adicionamos requer que o aplicativo ser modificado, recompilado e reimplantado.  
 
 Usando uma matriz, você pode consultar esses valores relacionados com o mesmo nome e usar um número que é chamado um *índice* ou *subscrito* para identificar um elemento individual com base em sua posição na matriz. Os índices de um intervalo de matriz de 0 a menos que o número total de elementos na matriz. Quando você usa a sintaxe do Visual Basic para definir o tamanho de uma matriz, você pode especificar o índice mais alto, não o número total de elementos na matriz. Você pode trabalhar com a matriz como uma unidade e a capacidade de iterar seus elementos libera você da necessidade de saber exatamente como muitos elementos contidos em tempo de design.
  
 Alguns exemplos rápidos antes da explicação:  
  
```vb  
' Declare a single-dimension array of 5 numbers.  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set its 4 values.  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)
  
' Redefine the size of an existing array and reset the values.
ReDim numbers(15)  
  
' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double  
  
' Declare a 4 x 3 multidimensional array and set array element values.  
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}  
  
' Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 ## <a name="in-this-article"></a>Neste artigo
  
- [Elementos da matriz em uma matriz simples](#array-elements-in-a-simple-array)  
  
- [Criação de uma matriz](#creating-an-array)  
  
- [Armazenando valores em uma matriz](#storing-values-in-an-array)  
  
- [Preencher uma matriz com literais de matriz](#populating-an-array-with-array-literals)  
  
- [Iterando por meio de uma matriz](#iterating-through-an-array)  
  
- [Tamanho da matriz](#BKMK_ArraySize)  

- [O tipo de matriz](#the-array-type)  
  
- [Matrizes como valores de retorno e parâmetros](#arrays-as-return-values-and-parameters)  
- [Matrizes denteadas](#jagged-arrays)  
  
- [Matrizes de comprimento zero](#zero-length-arrays)  

- [Uma matriz de divisão](#splitting-an-array)
  
- [Coleções como uma alternativa para matrizes](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a>Elementos da matriz em uma matriz simples  

Vamos criar uma matriz chamada `students` para armazenar o número de alunos em cada nível em uma escola de gramática. Os índices dos elementos variam de 0 a 6. Usar essa matriz é mais simples do que a declaração de sete variáveis.

A ilustração a seguir mostra a `students` matriz. Para cada elemento da matriz:  
  
-   O índice do elemento representa a classificação (o índice 0 representa o jardim de infância).
  
-   O valor contido no elemento representa o número de alunos nessa série.
  
 ![Imagem de matriz mostrando números de alunos](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
Elementos da matriz "alunos"  
 
O exemplo a seguir contém o código do Visual Basic que cria e usa a matriz:

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

O exemplo faz três coisas:

- Ele declara um `students` matriz com sete elementos. O número `6` na matriz de declaração indica que o último índice na matriz; é menor que o número de elementos na matriz.
- Ele atribui valores a cada elemento na matriz. Elementos da matriz são acessados usando o nome de matriz e incluindo o índice do elemento individual entre parênteses.
- Ela lista cada valor da matriz. O exemplo usa um [ `For` ](../../../language-reference/statements/for-next-statement.md) instrução para acessar cada elemento da matriz por seu número de índice.
  
 O `students` matriz no exemplo anterior é uma matriz unidimensional porque ele usa um índice. Uma matriz que usa mais de um índice ou subscrito é chamada *multidimensionais*. Para obter mais informações, consulte o restante deste artigo e [dimensões de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="creating-an-array"></a>Criação de uma matriz  
 
Você pode definir o tamanho de uma matriz de várias maneiras: 

- Você pode especificar o tamanho quando a matriz é declarada:
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - Você pode usar um `New` cláusula para fornecer o tamanho de uma matriz, quando ele é criado:  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 Se você tiver uma matriz existente, você pode redefinir o tamanho usando o [ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md) instrução. Você pode especificar que o `Redim` instrução manter os valores na matriz, ou você pode especificar que ele crie uma matriz vazia. O exemplo a seguir mostra os diferentes usos da instrução `Redim` para modificar o tamanho de uma matriz existente.  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 Para obter mais informações, consulte o [instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="storing-values-in-an-array"></a>Armazenando valores em uma matriz
 
 Você pode acessar cada local em uma matriz usando um índice do tipo `Integer`. Você pode armazenar e recuperar valores em uma matriz, fazendo referência a cada local de matriz usando seu índice entre parênteses. Índices de matrizes multidimensionais são separados por vírgulas (,). Você precisa de um índice para cada dimensão de matriz. 

O exemplo a seguir mostra algumas declarações que armazenam e recuperam valores em matrizes.
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a>Preencher uma matriz com literais de matriz
 Ao usar um literal de matriz, você pode preencher uma matriz com um conjunto inicial de valores ao mesmo tempo que você criá-lo. Um literal de matriz consiste em uma lista de valores separados por vírgulas que são colocados entre chaves (`{}`).  
  
 Ao criar uma matriz usando um literal de matriz, você pode fornecer o tipo de matriz ou usar inferência de tipos para determinar o tipo de matriz. O exemplo a seguir mostra as duas opções.  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 Quando você usa a inferência de tipo, o tipo da matriz é determinado pelo *tipo dominante* na lista de valores literais. O tipo dominante é o tipo para o qual todos os outros tipos de matriz podem ampliar. Se esse tipo exclusivo não puder ser determinado, o tipo dominante será o tipo exclusivo ao qual todos os outros tipos na matriz poderão restringir. Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`. Por exemplo, se a lista de valores que é fornecida para o literal de matriz contiver os valores do tipo `Integer`, `Long` e `Double`, a matriz resultante será do tipo `Double`. Porque `Integer` e `Long` ampliar apenas a `Double`, `Double` é o tipo dominante. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). 
 
> [!NOTE] 
> Você pode usar a inferência de tipo somente para matrizes que são definidas como variáveis locais em um membro de tipo. Se uma definição de tipo explícito estiver ausente, matrizes definidos com literais de matriz no nível de classe são do tipo `Object[]`. Para obter mais informações, consulte [inferência de tipo Local](../variables/local-type-inference.md). 

Observe que o exemplo anterior define `values` como uma matriz do tipo `Double` , embora os literais de matriz são do tipo `Integer`. Você pode criar essa matriz porque os valores na matriz literal podem ampliar a `Double` valores. 
  
 Você também pode criar e preencher uma matriz multidimensional usando *aninhados literais de matriz*. Literais de matriz aninhada devem ter um número de dimensões que é consistente com a matriz resultante. O exemplo a seguir cria uma matriz bidimensional de inteiros usando literais de matriz aninhada.  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
Ao usar literais de matriz aninhada para criar e preencher uma matriz, ocorrerá um erro se o número de elementos em literais de matriz aninhada não corresponde. Também ocorrerá um erro se você declarar explicitamente a variável de matriz têm números diferentes de dimensões que os literais de matriz. 
  
Exatamente como faria para matrizes unidimensionais, você pode contar com inferência de tipo durante a criação de uma matriz multidimensional com literais de matriz aninhada. O tipo inferido é o tipo dominante para todos os valores de todos os literais de matriz para o nível de aninhamento de todos os. O exemplo a seguir cria uma matriz bidimensional de tipo `Double[,]` dos valores que são do tipo `Integer` e `Double`.  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 Para obter exemplos adicionais, consulte [Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="iterating-through-an-array"></a>Iterando por meio de uma matriz  
 Quando você percorrer uma matriz, você acessar cada elemento na matriz de índice mais baixo para o mais alto ou da maior para o menor. Em geral, use ou o [para... Próxima instrução](../../../../visual-basic/language-reference/statements/for-next-statement.md) ou [para cada um... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) para iterar por meio dos elementos de uma matriz. Quando você não souber os limites superiores da matriz, você pode chamar o <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> método para obter o valor mais alto do índice. Embora o menor valor de índice é quase sempre 0, você pode chamar o <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> método para obter o valor mais baixo do índice.   
  
 O exemplo a seguir itera por meio de uma matriz unidimensional usando o [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) instrução. 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 O exemplo a seguir itera por meio de uma matriz multidimensional usando um [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) instrução. O método <xref:System.Array.GetUpperBound%2A> tem um parâmetro que especifica a dimensão. `GetUpperBound(0)`Retorna o maior índice da primeira dimensão, e `GetUpperBound(1)` retorna o maior índice da primeira dimensão.
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 O exemplo a seguir usa um [para cada um... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)para iterar por meio de uma matriz unidimensional e uma matriz bidimensional.  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a>Tamanho da matriz  

 O tamanho de uma matriz é o produto dos comprimentos de todas as suas dimensões. Ele representa o número total de elementos contidos no momento na matriz.  Por exemplo, o exemplo a seguir declara uma matriz dimensional de 2 com quatro elementos em cada dimensão. Como mostra a saída do exemplo, o tamanho da matriz é 16 (ou (3 + 1) * (3 + 1).

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> Esta discussão do tamanho da matriz não se aplica a matrizes denteadas. Para obter informações sobre matrizes denteadas e determinar o tamanho de uma matriz denteada, consulte o [matrizes denteadas](#jagged-arrays) seção.
  
  Você pode encontrar o tamanho de uma matriz usando a propriedade <xref:System.Array.Length%2A?displayProperty=nameWithType>. Você pode encontrar o comprimento de cada dimensão de uma matriz multidimensional usando o <xref:System.Array.GetLength%2A?displayProperty=nameWithType> método.  
  
 Você pode redimensionar uma variável de matriz atribuindo um novo objeto de matriz para ele ou usando o [ `ReDim` instrução](../../../../visual-basic/language-reference/statements/redim-statement.md) instrução. O exemplo a seguir usa o `ReDim` instrução para alterar uma matriz de elementos de 100 para uma matriz de elementos de 51.

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 Há várias coisas para ter em mente ao lidar com o tamanho de uma matriz.  
  
|||  
|---|---|  
|Tamanho da dimensão|O índice de cada dimensão é baseado em 0, o que significa que ele varia de 0 a seu limite superior. Portanto, o comprimento de uma determinada dimensão é maior do que o limite superior declarado da dimensão.|  
|Limites de comprimento|O tamanho de cada dimensão de uma matriz é limitado ao valor máximo do `Integer` tipo de dados, que é <xref:System.Int32.MaxValue?displayProperty=nameWithType> ou (2 ^ 31) - 1. No entanto, o tamanho total de uma matriz também é limitado pela memória disponível no sistema. Se você tentar inicializar uma matriz que excede a quantidade de memória disponível, o tempo de execução gera um <xref:System.OutOfMemoryException>.|  
|Tamanho e tamanho do elemento|Um tamanho de matriz é independente do tipo de dados de seus elementos. O tamanho sempre representa o número total de elementos, não o número de bytes que consomem na memória.|  
|Consumo de memória|Não é seguro fazer suposições sobre como uma matriz é armazenada na memória. O armazenamento varia em plataformas de larguras de dados diferentes, então a mesma matriz pode consumir mais memória em um sistema de 64 bits que em um sistema de 32 bits. Dependendo da configuração do sistema ao inicializar uma matriz, o CLR (Common Language Runtime) pode atribuir armazenamento para elementos do pacote o mais próximo possível, ou alinhá-los em limites naturais de hardware. Além disso, uma matriz de armazenamento requer sobrecarga de armazenamento para suas informações de controle, e essa sobrecarga aumenta com cada nova dimensão.|  

## <a name="the-array-type"></a>O tipo de matriz 
 Cada matriz tem um tipo de dados, que é diferente do tipo de dados de seus elementos. Não há nenhum tipo de dados único para todas as matrizes. Em vez disso, o tipo de dados de uma matriz é determinado pelo número de dimensões, ou *classificação*, da matriz e o tipo de dados dos elementos na matriz. Duas variáveis de matriz são dos mesmos dados somente quando elas têm a mesma classificação de tipo e seus elementos têm os mesmo tipo de dados. Os comprimentos das dimensões de uma matriz não influenciam o tipo de dados de matriz.  
  
 Cada matriz herda da classe <xref:System.Array?displayProperty=nameWithType> e você pode declarar uma variável para ser do tipo `Array`, mas não pode criar uma matriz do tipo `Array`. Por exemplo, embora o código a seguir declara a `arr` variável para ser do tipo `Array` e chama o <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> método para criar uma instância de matriz, o tipo da matriz é Object [].

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

Além disso, a [instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md) não pode operar em uma variável declarada como tipo `Array`. Por esses motivos e para segurança de tipo, é aconselhável declarar cada matriz como um tipo específico.  
  
 Você pode descobrir o tipo de dados de uma matriz ou seus elementos de várias maneiras. 
  
-   Você pode chamar o <xref:System.Object.GetType%2A> método na variável de obter um <xref:System.Type> objeto que representa o tipo de tempo de execução da variável. O objeto <xref:System.Type> mantém informações abrangentes em suas propriedades e métodos.  
  
-   Você pode passar a variável para o <xref:Microsoft.VisualBasic.Information.TypeName%2A> função para obter um `String` com o nome do tipo de tempo de execução.  
  
 O exemplo a seguir chama a ambos os `GetType` método e o `TypeName` função para determinar o tipo de uma matriz. O tipo de matriz é `Byte(,)`. Observe que o <xref:System.Type.BaseType%2A?displayProperty=nameWithType> propriedade também indica que o tipo base da matriz de bytes é o <xref:System.Array> classe.  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a>Matrizes como valores de retorno e parâmetros  
 Para retornar uma matriz de um procedimento `Function`, especifique o tipo de dados de matriz e o número de dimensões como o tipo de retorno de [instrução de função](../../../../visual-basic/language-reference/statements/function-statement.md). Dentro da função, declare uma variável da matriz local com o mesmo tipo de dados e número de dimensões. Na [instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md), inclua a variável da matriz local sem parênteses.  
  
 Para especificar uma matriz como um parâmetro para um procedimento `Sub` ou `Function`, defina o parâmetro como uma matriz com um tipo de dados especificado e o número de dimensões. Na chamada para o procedimento, passe uma variável de matriz com o mesmo tipo de dados e o número de dimensões.  
  
 No exemplo a seguir, o `GetNumbers` função retorna um `Integer()`, uma matriz unidimensional de tipo `Integer`. O procedimento `ShowNumbers` aceita um argumento `Integer()`. 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 No exemplo a seguir, o `GetNumbersMultiDim` função retorna um `Integer(,)`, uma matriz bidimensional de tipo `Integer`.  O procedimento `ShowNumbersMultiDim` aceita um argumento `Integer(,)`.  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a>Matrizes denteadas  
 
Às vezes, a estrutura de dados em seu aplicativo é bidimensional, mas não retangular. Por exemplo, você pode usar uma matriz para armazenar dados sobre a alta temperatura de cada dia do mês. A primeira dimensão da matriz representa o mês, mas a segunda dimensão representa o número de dias e o número de dias em um mês não é uniforme. Um *matriz denteada*, que também é chamado um *matriz de matrizes*, foi projetado para esses cenários. Uma matriz denteada é uma matriz cujos elementos também são matrizes. Uma matriz denteada e cada elemento em uma matriz denteada podem ter uma ou mais dimensões.  
  
 O exemplo a seguir usa uma matriz de meses, cada elemento que é uma matriz de dias. O exemplo usa uma matriz denteada porque meses diferentes têm números diferentes de dias.  O exemplo mostra como criar uma matriz denteada, atribuir valores a ele e recuperar e exibir seus valores.
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

O exemplo anterior atribui valores para a matriz denteada em uma base por elemento usando um `For...Next` loop. Você também pode atribuir valores para os elementos de uma matriz denteada usando literais de matriz aninhada. No entanto, a tentativa de usar aninhados literais de matriz (por exemplo, ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) gera um erro do compilador [BC30568](../../../,,/../misc/bc30568.md). Para corrigir o erro, coloque os literais de matriz interna entre parênteses. Os parênteses forçam a expressão literal de matriz a ser avaliada, e os valores resultantes são usados com a matriz externa literal, como mostra o exemplo a seguir.  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

Uma matriz denteada é uma matriz unidimensional cujos elementos contêm matrizes. Portanto, o <xref:System.Array.Length%2A?displayProperty=nameWithType> propriedade e o `Array.GetLength(0)` método retornar o número de elementos na matriz unidimensional, e `Array.GetLength(1)` lança um <xref:System.IndexOutOfRangeException> porque não é uma matriz denteada multidimensional. Determinar o número de elementos em cada submatriz por recuperar o valor de cada submatriz <xref:System.Array.Length%2A?displayProperty=nameWithType> propriedade. O exemplo a seguir ilustra como determinar o número de elementos em uma matriz denteada.

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a>Matrizes de comprimento zero  
Visual Basic faz distinção entre uma matriz não inicializada (uma matriz cujo valor é `Nothing`) e um *matriz de comprimento zero* ou matriz em branco (uma matriz que não tem elementos). Uma matriz não inicializada é aquele que não tenha sido dimensionadas ou tiveram valores atribuídos a ele. Por exemplo:

```vb
Dim arr() As String
```
Uma matriz de comprimento zero é declarada com uma dimensão de -1. Por exemplo:

```vb
Dim arrZ(-1) As String
```
Talvez seja necessário criar uma matriz de tamanho igual a zero nas seguintes circunstâncias:  
  
-   Sem arriscar uma <xref:System.NullReferenceException> exceção, seu código precisa acessar membros do <xref:System.Array> classe, como <xref:System.Array.Length%2A> ou <xref:System.Array.Rank%2A>, ou chamar uma função do Visual Basic, como <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Para manter o seu código simple por não ter que verificar se há `Nothing` como um caso especial.  
  
-   Seu código interage com uma API (interface de programação do aplicativo) que exige que você passe uma matriz de tamanho igual a zero para um ou mais procedimentos ou retorna uma matriz de tamanho igual a zero de um ou mais procedimentos.

## <a name="splitting-an-array"></a>Uma matriz de divisão

Em alguns casos, talvez seja necessário dividir uma única matriz em várias matrizes. Isso envolve a identificar o ponto ou pontos em que a matriz é dividida e, em seguida, spitting a matriz em dois ou mais conjuntos separados. 

> [!NOTE] 
> Esta seção discute dividir uma única cadeia de caracteres em uma matriz de cadeia de caracteres com base em alguma delimitador. Para obter informações sobre como dividir uma cadeia de caracteres, consulte o <xref:System.String.Split%2A?displayProperty=nameWithType> método.

Os critérios mais comuns para a divisão de uma matriz são:

- O número de elementos na matriz. Por exemplo, você talvez queira dividir uma matriz de mais de um número especificado de elementos em um número de aproximadamente partes iguais. Para essa finalidade, você pode usar o valor retornado pelo <xref:System.Array.Length%2A?displayProperty=nameWithType> ou <xref:System.Array.GetLength%2A?displayProperty=nameWithType> método.

- O valor de um elemento, que serve como um delimitador que indica onde a matriz deve ser dividida. Você pode procurar um valor específico ao chamar o <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> e <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> métodos.
 
Depois de determinar o índice ou índices em que a matriz deve ser dividida, você pode criar os conjuntos individuais chamando o <xref:System.Array.Copy%2A?displayProperty=nameWithType> método. 

O exemplo a seguir divide uma matriz em duas matrizes de aproximadamente tamanhos iguais. (Se o número total de elementos da matriz é ímpar, a primeira matriz tem um elemento mais do que o segundo). 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

O exemplo a seguir divide uma matriz de cadeia de caracteres em duas matrizes com base na presença de um elemento cujo valor é "zzz", que serve como o delimitador de matriz. Os novos conjuntos não incluem o elemento que contém o delimitador.

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a>Ingressar em matrizes

Você também pode combinar várias matrizes em uma única matriz maior. Para fazer isso, você também usar o <xref:System.Array.Copy%2A?displayProperty=nameWithType> método. 

> [!NOTE] 
> Esta seção discute a ingressar em uma matriz de cadeia de caracteres em uma única cadeia de caracteres. Para obter informações sobre como associar uma matriz de cadeia de caracteres, consulte o <xref:System.String.Join%2A?displayProperty=nameWithType> método.

Antes de copiar os elementos de cada matriz para a nova matriz, primeiro você deve garantir que inicializou a matriz para que ele seja grande o suficiente para accompodate nova matriz. Você pode fazer isso de duas maneiras:

- Use o [ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md) instrução para expandir a matriz dinamicamente antes de adicionar novos elementos a ele. Essa é a técnica mais fácil, mas pode resultar em degradação de desempenho e o consumo excessivo de memória quando você estiver copiando matrizes grandes.
- Calcule o número total de elementos necessários para a nova matriz grande e adicione os elementos de cada matriz de origem para ele.

O exemplo a seguir usa a segunda abordagem para adicionar quatro matrizes com dez elementos a uma única matriz.  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

Como nesse caso, as matrizes de origem são todos os pequenas, podemos também dinamicamente expandir a matriz como adicionamos os elementos de cada nova matriz para ele. O exemplo a seguir faz isso.

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a>Coleções como uma alternativa para matrizes  
 As matrizes são mais úteis para criar e trabalhar com um número fixo de objetos fortemente tipados. As coleções fornecem uma maneira mais flexível de trabalhar com grupos de objetos. Ao contrário das matrizes, que exige que você altere explicitamente o tamanho de uma matriz com o [ `ReDim` instrução](../../../../visual-basic/language-reference/statements/redim-statement.md), coleções de aumentar ou reduzir dinamicamente conforme as necessidades de uma alteração de aplicativo.  
  
 Quando você usa `ReDim` para redimensionar uma matriz, o Visual Basic cria uma nova matriz e versões anterior. Isso leva o tempo da execução. Portanto, se o número de itens que você está trabalhando com as alterações com frequência, ou você não pode prever o número máximo de itens que você precisa, geralmente será obter melhor desempenho usando uma coleção.  
  
 Para algumas coleções, você pode atribuir uma chave para qualquer objeto que colocar na coleção para que você possa recuperar rapidamente o objeto, usando a chave.  
  
 Se a coleção contiver elementos de apenas um tipo de dados, você poderá usar uma das classes no namespace <xref:System.Collections.Generic?displayProperty=nameWithType>. Uma coleção genérica impõe segurança de tipos para que nenhum outro tipo de dados possa ser adicionado a ela.  
  
 Para obter mais informações sobre coleções, consulte [Coleções](../../concepts/collections.md).
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Termo|Definição|  
|----------|----------------|  
|[Dimensões de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Explica a classificação e as dimensões em matrizes.|  
|[Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Descreve como preencher matrizes com valores iniciais.|  
|[Como classificar uma matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Mostra como classificar os elementos de uma matriz em ordem alfabética.|  
|[Como atribuir uma matriz a outra matriz](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Descreve as regras e as etapas para atribuir uma matriz a outra variável de matriz.|  
|[Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Aborda alguns problemas comuns que surgem ao trabalhar com matrizes.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Array?displayProperty=nameWithType>  
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md)
