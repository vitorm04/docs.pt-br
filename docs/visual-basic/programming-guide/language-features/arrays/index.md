---
title: "Matrizes no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Array"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "matrizes [Visual Basic]"
  - "Visual Basic, matrizes"
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: 47
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Matrizes no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma matriz é um conjunto de valores que são logicamente relacionados uns aos outros, como o número de alunos em cada nível de uma escola de gramática.  Se você estiver procurando ajuda sobre matrizes no Visual Basic for Applications \(VBA\), consulte o [referência de linguagem](https://msdn.microsoft.com/en-us/library/office/gg264383\(v=office.14\).aspx).  
  
 Usando uma matriz, você pode consultar esses valores relacionados com o mesmo nome e use um número que chamou um índice ou subscrito para informá\-los separados. Os valores individuais são chamados de elementos da matriz. Eles são contíguos do índice 0 até o valor de índice mais alto.  
  
 Ao contrário de uma matriz, uma variável que contém um único valor é chamada um *escalar* variável.  
  
 Alguns exemplos rápidos antes da explicação:  
  
```vb  
  
'Declare a single-dimension array of 5 values Dim numbers(4) As Integer ‘Declare a single-dimension array and set array element values Dim numbers = New Integer() {1, 2, 4, 8} ‘Redefine the size of an existing array retaining the current values ReDim Preserve numbers(15) ‘Redefine the size of an existing array, resetting the values ReDim numbers(15) ‘Declare a multi-dimensional array Dim matrix(5, 5) As Double ‘Declare a multi-dimensional array and set array element values Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}} ‘Declare a jagged array Dim sales()() As Double = New Double(11)() {}  
```  
  
 **Neste tópico**  
  
-   [Elementos da matriz em uma matriz simples](#BKMK_ArrayElements)  
  
-   [Criação de uma matriz](#BKMK_CreatingAnArray)  
  
-   [Armazenando valores em uma matriz](#BKMK_StoringValues)  
  
-   [Preencher uma matriz com valores iniciais](#BKMK_Populating)  
  
    -   [Literais de matriz aninhados](#BKMK_NestedArrayLiterals)  
  
-   [Iterar em uma matriz](#BKMK_Iterating)  
  
-   [Matrizes como valores de retorno e parâmetros](#BKMK_ReturnValues)  
  
-   [Matrizes denteadas](#BKMK_JaggedArrays)  
  
-   [Matrizes de comprimento zero](#BKMK_ZeroLength)  
  
-   [Tamanho da matriz](#BKMK_ArraySize)  
  
-   [Tipos de matriz e outros tipos](#BKMK_ArrayTypes)  
  
-   [Coleções como uma alternativa para matrizes](#BKMK_Collections)  
  
##  <a name="BKMK_ArrayElements"></a> Elementos da matriz em uma matriz simples  
 O exemplo a seguir declara uma variável de matriz para armazenar o número de alunos em cada nível de uma escola de gramática.  
  
 [!CODE [VbVbalrArrays#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#2)]  
  
 A matriz `students` no exemplo anterior contém sete elementos. Os índices dos elementos variam de 0 a 6. Essa matriz é mais simples do que declarar sete variáveis.  
  
 A ilustração a seguir mostra a matriz `students`. Para cada elemento da matriz:  
  
-   O índice do elemento representa a classificação \(índice 0 representa se aprende no jardim\).  
  
-   O valor contido no elemento representa o número de alunos em que grau.  
  
 ![Imagem de matriz mostrando números de alunos](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.png "ArrayExampleSchool")  
Elementos da matriz "alunos"  
  
 O exemplo a seguir mostra como se referir ao primeiro, segundo e último elemento da matriz `students`.  
  
 [!CODE [VbVbalrArrays#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#3)]  
  
 Você pode consultar a matriz como um todo, usando apenas o nome da variável matriz sem índices.  
  
 A matriz `students` no exemplo anterior usa um índice e é considerado unidimensional. Uma matriz que usa mais de um índice ou subscrito é chamada multidimensional. Para obter mais informações, consulte o restante deste tópico e [Dimensões de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="BKMK_CreatingAnArray"></a> Criação de uma matriz  
 Você pode definir o tamanho de uma matriz de várias maneiras. Você pode fornecer o tamanho quando a matriz é declarada, como mostra o exemplo a seguir.  
  
 [!CODE [VbVbalrArrays#12](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#12)]  
  
 Você também pode usar um `New` cláusula para fornecer o tamanho de uma matriz, quando ele é criado, como mostra o exemplo a seguir.  
  
 [!CODE [VbVbalrArrays#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#11)]  
  
 Se você tiver uma matriz existente, você pode redefinir o tamanho usando o `Redim` instrução. Você pode especificar que o `Redim` instrução deve manter os valores na matriz, ou você pode especificar que ele crie uma matriz vazia. O exemplo a seguir mostra os diferentes usos da `Redim` instrução para modificar o tamanho de uma matriz existente.  
  
 [!CODE [VbVbalrArrays#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#13)]  
  
 Para obter mais informações, consulte [Instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="BKMK_StoringValues"></a> Armazenando valores em uma matriz  
 Você pode acessar cada local em uma matriz usando um índice do tipo `Integer`. Você pode armazenar e recuperar valores em uma matriz, fazendo referência a cada local de matriz usando seu índice entre parênteses. Índices para matrizes multidimensionais são separados por vírgulas \(,\). Você precisa de um índice para cada dimensão de matriz. O exemplo a seguir mostra algumas declarações que armazenam valores em matrizes.  
  
 [!CODE [VbVbalrArrays#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#5)]  
  
 O exemplo a seguir mostra algumas declarações que obtêm valores de matrizes.  
  
 [!CODE [VbVbalrArrays#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#6)]  
  
##  <a name="BKMK_Populating"></a> Preencher uma matriz com valores iniciais  
 Ao usar um literal de matriz, você pode criar uma matriz que contém um conjunto inicial de valores. Um literal de matriz consiste em uma lista de valores separados por vírgula entre chaves \(`{}`\).  
  
 Quando você cria uma matriz usando um literal de matriz, você pode fornecer o tipo de matriz ou usar inferência de tipo para determinar o tipo de matriz. O código a seguir mostra as duas opções.  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/index_1.vb)]  
  
 Quando você usa a inferência de tipo, o tipo da matriz é determinado pelo dominante tipo na lista de valores que é fornecido para o literal de matriz. O tipo dominante é um tipo exclusivo para que todos os outros tipos na matriz pode ampliar o literal. Se esse tipo exclusivo não puder ser determinado, o tipo dominante é o tipo exclusivo para o qual todos os outros tipos na matriz podem restringir. Se nenhum desses tipos exclusivos pode ser determinado, o tipo dominante é `Object`. Por exemplo, se a lista de valores que é fornecida para o literal de matriz contém os valores do tipo `Integer`, `Long`, e `Double`, a matriz resultante é do tipo `Double`. Ambos `Integer` e `Long` apenas ao ampliar `Double`. Portanto, `Double` é o tipo dominante. Para obter mais informações, consulte [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Essas regras de inferência se aplicam a tipos são inferidos para matrizes de variáveis locais que são definidas em um membro da classe. Embora você possa usar literais de matriz quando você criar variáveis de nível de classe, você não pode usar a inferência de tipos no nível de classe. Como resultado, os literais de matriz são especificados no nível da classe inferir os valores que são fornecidos para a literal como tipo de matriz `Object`.  
  
 Você pode especificar explicitamente o tipo dos elementos em uma matriz é criada usando um literal de matriz. Nesse caso, os valores na matriz literal devem ampliar para o tipo dos elementos da matriz. O exemplo de código a seguir cria uma matriz do tipo `Double` de uma lista de números inteiros.  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/index_2.vb)]  
  
###  <a name="BKMK_NestedArrayLiterals"></a> Literais de matriz aninhados  
 Você pode criar uma matriz multidimensional usando literais de matriz aninhados. Literais de matriz aninhada devem ter uma dimensão e o número de dimensões ou classificação, que é consistente com a matriz resultante. O exemplo de código a seguir cria uma matriz bidimensional de inteiros usando um literal de matriz.  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/index_3.vb)]  
  
 No exemplo anterior, um erro ocorrerá se o número de elementos em literais de matriz aninhados não corresponde. Também poderia ocorrer um erro se você declarou explicitamente a variável de matriz para ser diferente de bidimensional.  
  
> [!NOTE]
>  Você pode evitar um erro ao fornecer literais de matriz aninhados de diferentes dimensões colocando os literais de matriz interna entre parênteses. Os parênteses obrigam a expressão literal de matriz a ser avaliada, e os valores resultantes são usados com a matriz externa literal, como mostra o código a seguir.  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/index_4.vb)]  
  
 Quando você cria uma matriz multidimensional usando literais de matriz aninhados, você pode usar a inferência de tipos. Quando você usa a inferência de tipo, o tipo inferido é o tipo dominante para todos os valores em todos os literais de matriz para um nível de aninhamento. O exemplo de código a seguir cria uma matriz bidimensional de tipo `Double` dos valores que são do tipo `Integer` e `Double`.  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/index_5.vb)]  
  
 Para obter exemplos adicionais, consulte [Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="BKMK_Iterating"></a> Iterar em uma matriz  
 Quando você itera através de uma matriz, acessar cada elemento da matriz de índice mais baixo para o índice mais alto.  
  
 O exemplo a seguir itera por meio de uma matriz unidimensional usando o [Instrução For...Next](../../../../visual-basic/language-reference/statements/for-next-statement.md). O <xref:System.Array.GetUpperBound%2A> método retorna o valor mais alto que o índice pode ter. O menor valor de índice é sempre 0.  
  
 [!CODE [VbVbalrArrays#41](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#41)]  
  
 O exemplo a seguir itera por meio de uma matriz multidimensional usando um `For...Next` instrução. O <xref:System.Array.GetUpperBound%2A> método tem um parâmetro que especifica a dimensão.`GetUpperBound(0)` Retorna o valor de índice alto para a primeira dimensão, e `GetUpperBound(1)` retorna o valor de índice alto para a segunda dimensão.  
  
 [!CODE [VbVbalrArrays#42](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#42)]  
  
 O exemplo a seguir itera por meio de uma matriz unidimensional usando um [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 [!CODE [VbVbalrArrays#43](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#43)]  
  
 O exemplo a seguir itera por meio de uma matriz multidimensional usando um `For Each...Next` instrução. No entanto, você tem mais controle sobre os elementos de uma matriz multidimensional se você usar aninhado `For…Next` instrução, como um exemplo anterior, em vez de um `For Each…Next` instrução.  
  
 [!CODE [VbVbalrArrays#44](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#44)]  
  
##  <a name="BKMK_ReturnValues"></a> Matrizes como valores de retorno e parâmetros  
 Para retornar uma matriz de uma `Function` procedimento, especifique o tipo de dados de matriz e o número de dimensões como o tipo de retorno de [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md). Dentro da função, declare uma variável array local com o mesmo tipo de dados e o número de dimensões. Na [Instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md), incluir a variável de matriz local sem parênteses.  
  
 Para especificar uma matriz como um parâmetro para um `Sub` ou `Function` procedimento, defina o parâmetro como uma matriz com um tipo de dados especificado e o número de dimensões. Na chamada para o procedimento, envie uma variável de matriz com o mesmo tipo de dados e o número de dimensões.  
  
 No exemplo a seguir, o `GetNumbers` função retorna um `Integer()`. Esse tipo de matriz é uma matriz unidimensional do tipo `Integer`. O `ShowNumbers` procedimento aceita um `Integer()` argumento.  
  
 [!CODE [VbVbalrArrays#51](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#51)]  
  
 No exemplo a seguir, o `GetNumbersMultiDim` função retorna um `Integer(,)`. Esse tipo de matriz é um dois matriz tridimensional do tipo `Integer`.  O `ShowNumbersMultiDim` procedimento aceita um `Integer(,)` argumento.  
  
 [!CODE [VbVbalrArrays#52](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#52)]  
  
##  <a name="BKMK_JaggedArrays"></a> Matrizes denteadas  
 Uma matriz que contém outras matrizes como elementos é conhecida como uma matriz de matrizes ou uma matriz denteada. Uma matriz denteada e cada elemento em uma matriz denteada podem ter uma ou mais dimensões. Às vezes, a estrutura de dados em seu aplicativo é bidimensional, mas não retangular.  
  
 O exemplo a seguir tem uma matriz de meses, cada elemento é uma matriz de dias. Como diferentes meses têm diferentes números de dias, os elementos não formam uma matriz bidimensional retangular. Portanto, uma matriz denteada é usada em vez de uma matriz multidimensional.  
  
 [!CODE [VbVbalrArrays#21](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#21)]  
  
##  <a name="BKMK_ZeroLength"></a> Matrizes de comprimento zero  
 Uma matriz que não contém nenhum elemento também é chamada um array de comprimento zero. Uma variável que contém uma matriz de comprimento zero não tem o valor `Nothing`. Para criar uma matriz que não tem nenhum elemento, declare uma das dimensões da matriz como \-1, como mostra o exemplo a seguir.  
  
 [!CODE [VbVbalrArrays#14](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#14)]  
  
 Talvez seja necessário criar uma matriz de comprimento zero nas seguintes circunstâncias:  
  
-   Sem arriscar um <xref:System.NullReferenceException> exceção, seu código precisa acessar membros da <xref:System.Array> classe, como <xref:System.Array.Length%2A> ou <xref:System.Array.Rank%2A>, ou chamar uma [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] função como <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Você deseja manter o código mais simples por não ter que procurar `Nothing` como um caso especial.  
  
-   Seu código interage com uma interface de programação de aplicativo \(API\) que exige que você passe uma matriz de comprimento zero para um ou mais procedimentos ou retorna uma matriz de comprimento zero de um ou mais procedimentos.  
  
##  <a name="BKMK_ArraySize"></a> Tamanho da matriz  
 O tamanho de uma matriz é o produto dos comprimentos de todas as suas dimensões. Representa o número total de elementos contidos no momento da matriz.  
  
 O exemplo a seguir declara uma matriz tridimensional.  
  
```  
Dim prices(3, 4, 5) As Long  
```  
  
 O tamanho total da matriz na variável `prices` é \(3 \+ 1\) x \(4 \+ 1\) x \(5 \+ 1\) \= 120.  
  
 Você pode encontrar o tamanho de uma matriz usando o <xref:System.Array.Length%2A> propriedade. Você pode encontrar o tamanho de cada dimensão de uma matriz multidimensional usando o <xref:System.Array.GetLength%2A> método.  
  
 Você pode redimensionar uma variável de matriz atribuindo um novo objeto de matriz para ele ou usando o `ReDim` instrução.  
  
 Há várias coisas que preciso ter em mente ao lidar com o tamanho de uma matriz.  
  
|||  
|-|-|  
|Tamanho da dimensão|O índice de cada dimensão é baseado em 0, o que significa que ele varia de 0 até o limite superior. Portanto, o comprimento de uma determinada dimensão é maior por 1 o limite superior declarado para a dimensão.|  
|Limites de comprimento|O tamanho de cada dimensão de uma matriz é limitado para o valor máximo do `Integer` tipo de dados, que é \(2 ^ 31\) \- 1. No entanto, o tamanho total de uma matriz também é limitado pela memória disponível no sistema. Se você tentar inicializar uma matriz que excede a quantidade de RAM disponível, o common language runtime lança um <xref:System.OutOfMemoryException> exceção.|  
|Tamanho e o tamanho do elemento|Um tamanho de matriz é independente do tipo de dados de seus elementos. O tamanho sempre representa o número total de elementos, não o número de bytes que eles consomem no armazenamento.|  
|Consumo de memória|Não é seguro fazer suposições sobre como uma matriz é armazenada na memória. Armazenamento varia em plataformas de larguras de dados diferentes, então a mesma matriz pode consumir mais memória em um sistema de 64 bits que em um sistema de 32 bits. Dependendo da configuração do sistema ao inicializar uma matriz, o common language runtime \(CLR\) pode atribuir armazenamento para elementos do pacote tão próximas quanto possível, ou para alinhá\-los em limites de hardware natural. Além disso, uma matriz de armazenamento requer sobrecarga para suas informações de controle, e essa sobrecarga aumenta com cada nova dimensão.|  
  
##  <a name="BKMK_ArrayTypes"></a> Tipos de matriz e outros tipos  
 Cada matriz tem um tipo de dados, mas ele difere do tipo de dados de seus elementos. Não há nenhum tipo de dados único para todas as matrizes. Em vez disso, o tipo de dados de uma matriz é determinado pelo número de dimensões, ou *classificação*, da matriz e o tipo de dados dos elementos na matriz. Duas variáveis array são considerados dos mesmos dados digite somente quando elas têm a mesma classificação e seus elementos têm os mesmos tipo de dados. Os comprimentos das dimensões de uma matriz não influenciam o tipo de dados de matriz.  
  
 Cada matriz herda o <xref:System.Array?displayProperty=fullName> classe e você pode declarar uma variável para ser do tipo `Array`, mas você não pode criar uma matriz do tipo `Array`. Além disso, o [Instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md) não pode operar em uma variável declarada como tipo `Array`. Por esses motivos e segurança de tipo, é aconselhável declarar cada matriz como um tipo específico, como `Integer` no exemplo anterior.  
  
 Você pode descobrir o tipo de dados de uma matriz ou seus elementos de várias maneiras.  
  
-   Você pode chamar o <xref:System.Object.GetType%2A?displayProperty=fullName> método na variável para receber uma <xref:System.Type> objeto para o tipo de tempo de execução da variável. O <xref:System.Type> objeto mantém informações abrangentes em suas propriedades e métodos.  
  
-   Você pode passar a variável para o <xref:Microsoft.VisualBasic.Information.TypeName%2A> função a receber um `String` que contém o nome do tipo de tempo de execução.  
  
-   Você pode passar a variável para o <xref:Microsoft.VisualBasic.Information.VarType%2A> função a receber uma `VariantType` valor que representa a classificação do tipo da variável.  
  
 A exemplo a seguir chama o `TypeName` função para determinar o tipo da matriz e o tipo dos elementos na matriz. O tipo de matriz é `Integer(,)` e os elementos da matriz são do tipo `Integer`.  
  
 [!CODE [VbVbalrArrays#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#15)]  
  
##  <a name="BKMK_Collections"></a> Coleções como uma alternativa para matrizes  
 Matrizes são mais úteis para criar e trabalhar com um número fixo de objetos fortemente tipados. Coleções fornecem uma maneira mais flexível de trabalhar com grupos de objetos. Ao contrário de matrizes, o grupo de objetos que você trabalha pode crescer e reduzir dinamicamente conforme as necessidades do aplicativo mudam.  
  
 Se você precisar alterar o tamanho de uma matriz, você deve usar o [Instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md). Quando você fizer isso, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cria uma nova matriz e libera a matriz anterior para descarte. Isso leva tempo de execução. Portanto, se o número de itens que você está trabalhando com forem alterados com freqüência, ou você não pode prever o número máximo de itens que você precisa, você pode obter melhor desempenho usando uma coleção.  
  
 Para algumas coleções, você pode atribuir uma chave para qualquer objeto que você coloque na coleção para que você possa recuperar rapidamente o objeto usando a chave.  
  
 Se a coleção contém elementos de apenas um tipo de dados, você pode usar uma das classes de <xref:System.Collections.Generic?displayProperty=fullName> namespace. Uma coleção genérica impõe segurança de tipo para que nenhum outro tipo de dados pode ser adicionado a ele. Quando você recupera um elemento de uma coleção genérica, você não precisa determinar seu tipo de dados ou convertê\-lo.  
  
 Para obter mais informações sobre coleções, consulte [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Exemplo  
 O exemplo a seguir usa a [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classe genérica <xref:System.Collections.Generic.List%601?displayProperty=fullName> para criar um conjunto de listas de `Customer` objetos.  
  
 [!CODE [VbVbalrArrays#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrArrays#1)]  
  
 A declaração do `CustomerFile` coleção Especifica que ele pode conter elementos apenas do tipo `Customer`. Ele também fornece uma capacidade inicial de 200 elementos. O procedimento `AddNewCustomer` verifica o novo elemento de validade e o adiciona à coleção. O procedimento `PrintCustomers` usa um `For Each` loop para percorrer a coleção e exibir seus elementos.  
  
## Tópicos relacionados  
  
|Termo|Definição|  
|-----------|---------------|  
|[Dimensões de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Explica a classificação e as dimensões em matrizes.|  
|[Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Descreve como preencher matrizes com valores iniciais.|  
|[Como classificar uma matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Mostra como classificar os elementos de uma matriz em ordem alfabética.|  
|[Como atribuir uma matriz a outra matriz](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Descreve as regras e as etapas para atribuir uma matriz a outra variável de matriz.|  
|[Solucionando problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Aborda alguns problemas comuns que surgem ao trabalhar com matrizes.|  
  
## Consulte também  
 <xref:System.Array>   
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md)