---
title: Matrizes no Visual Basic
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Array
dev_langs:
- VB
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
caps.latest.revision: 47
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8ebad59a07d07d61ea77e41e4044b3febc0ef250
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="arrays-in-visual-basic"></a>Matrizes no Visual Basic
Uma matriz é um conjunto de valores que são logicamente relacionados uns aos outros, como o número de alunos em cada nível em uma escola primária.  Se você estiver procurando ajuda sobre matrizes no VBA (Visual Basic for Applications), consulte a [referência de linguagem](https://msdn.microsoft.com/library/office/gg264383\(v=office.14\).aspx).  
  
 Usando uma matriz, você pode consultar esses valores relacionados com o mesmo nome e usar um número que é chamado de índice ou subscrito para identificação. Os valores individuais são chamados de elementos da matriz. Eles são contíguos do índice 0 até o valor de índice mais alto.  
  
 Em contraste com uma matriz, uma variável que contém um único valor é chamada de variável *escalar*.  
  
 Alguns exemplos rápidos antes da explicação:  
  
```vb  
'Declare a single-dimension array of 5 values  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set array element values  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
'Redefine the size of an existing array retaining the current values  
ReDim Preserve numbers(15)  
  
'Redefine the size of an existing array, resetting the values  
ReDim numbers(15)  
  
'Declare a multi-dimensional array  
Dim matrix(5, 5) As Double  
  
'Declare a multi-dimensional array and set array element values  
Dim matrix = New Integer(4, 4) {{1, 2}, {3, 4}, {5, 6}, {7, 8}}  
  
'Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 **Neste tópico**  
  
-   [Elementos da matriz em uma matriz simples](#BKMK_ArrayElements)  
  
-   [Criando uma matriz](#BKMK_CreatingAnArray)  
  
-   [Armazenando valores em uma matriz](#BKMK_StoringValues)  
  
-   [Preenchendo uma matriz com valores iniciais](#BKMK_Populating)  
  
    -   [Literais de matriz aninhados](#BKMK_NestedArrayLiterals)  
  
-   [Iterando por uma matriz](#BKMK_Iterating)  
  
-   [Matrizes como valores de retorno e parâmetros](#BKMK_ReturnValues)  
  
-   [Matrizes denteadas](#BKMK_JaggedArrays)  
  
-   [Matrizes de tamanho igual a zero](#BKMK_ZeroLength)  
  
-   [Tamanho da matriz](#BKMK_ArraySize)  
  
-   [Tipos de matriz e outros tipos](#BKMK_ArrayTypes)  
  
-   [Coleções como uma alternativa para matrizes](#BKMK_Collections)  
  
##  <a name="BKMK_ArrayElements"></a> Elementos da matriz em uma matriz simples  
 O exemplo a seguir declara uma variável de matriz para armazenar o número de alunos em cada nível em uma escola primária.  
  
 [!code-vb[VbVbalrArrays#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#2)]  
  
 A matriz `students` no exemplo anterior contém sete elementos. Os índices dos elementos variam de 0 a 6. Ter essa matriz é mais simples do que declarar sete variáveis.  
  
 A ilustração a seguir mostra a matriz `students`. Para cada elemento da matriz:  
  
-   O índice do elemento representa a classificação (o índice 0 representa o jardim de infância).  
  
-   O valor contido no elemento representa o número de alunos nessa série.  
  
 ![Imagem de matriz mostrando números de alunos](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
Elementos da matriz "alunos"  
  
 O exemplo a seguir mostra como se referir ao primeiro, segundo e último elemento da matriz `students`.  
  
 [!code-vb[VbVbalrArrays#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#3)]  
  
 Você pode consultar a matriz como um todo usando apenas o nome da variável da matriz sem índices.  
  
 A matriz `students` no exemplo anterior usa um índice e é considerada unidimensional. Uma matriz que usa mais de um índice ou subscrito é chamada multidimensional. Para obter mais informações, consulte o restante deste tópico e [Dimensões de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="BKMK_CreatingAnArray"></a> Criando uma matriz  
 Você pode definir o tamanho de uma matriz de várias maneiras. Você pode fornecer o tamanho quando a matriz é declarada, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrArrays#12](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#12)]  
  
 Você também pode usar uma cláusula `New` para fornecer o tamanho de uma matriz quando ela é criada, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrArrays#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#11)]  
  
 Se tiver uma matriz existente, você poderá redefinir o tamanho usando a instrução `Redim`. Você pode especificar que a instrução `Redim` deve manter os valores na matriz ou você pode especificar que ela crie uma matriz vazia. O exemplo a seguir mostra os diferentes usos da instrução `Redim` para modificar o tamanho de uma matriz existente.  
  
 [!code-vb[VbVbalrArrays#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#13)]  
  
 Para obter mais informações, consulte [Instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="BKMK_StoringValues"></a> Armazenando valores em uma matriz  
 Você pode acessar cada local em uma matriz usando um índice do tipo `Integer`. Você pode armazenar e recuperar valores em uma matriz, fazendo referência a cada local de matriz usando seu índice entre parênteses. Índices de matrizes multidimensionais são separados por vírgulas (,). Você precisa de um índice para cada dimensão de matriz. O exemplo a seguir mostra algumas instruções que armazenam valores em matrizes.  
  
 [!code-vb[VbVbalrArrays#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#5)]  
  
 O exemplo a seguir mostra algumas instruções que obtêm valores de matrizes.  
  
 [!code-vb[VbVbalrArrays#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#6)]  
  
##  <a name="BKMK_Populating"></a> Preenchendo uma matriz com valores iniciais  
 Usando um literal de matriz, você pode criar uma matriz que contém um conjunto inicial de valores. Um literal de matriz consiste em uma lista de valores separados por vírgulas que são colocados entre chaves (`{}`).  
  
 Ao criar uma matriz usando um literal de matriz, você pode fornecer o tipo de matriz ou usar inferência de tipos para determinar o tipo de matriz. O código a seguir mostra as duas opções.  
  
 [!code-vb[VbVbalrCollectionInitializers#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#3)]  
  
 Quando você usa a inferência de tipos, o tipo da matriz é determinado pelo tipo dominante na lista de valores que é fornecida para o literal de matriz. O tipo dominante é um tipo exclusivo ao qual todos os outros tipos no literal da matriz podem ser ampliados. Se esse tipo exclusivo não puder ser determinado, o tipo dominante será o tipo exclusivo ao qual todos os outros tipos na matriz poderão restringir. Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`. Por exemplo, se a lista de valores que é fornecida para o literal de matriz contiver os valores do tipo `Integer`, `Long` e `Double`, a matriz resultante será do tipo `Double`. `Integer` e `Long` são ampliados apenas para `Double`. Portanto, `Double` é o tipo dominante. Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Essas regras de inferência se aplicam a tipos que são inferidos para matrizes que são variáveis locais que são definidas em um membro da classe. Embora possa usar literais de matriz ao criar variáveis de nível de classe, você não pode usar a inferência de tipos no nível de classe. Como resultado, os literais de matriz que são especificados no nível da classe inferem nos valores que são fornecidos para o literal de matriz como tipo `Object`.  
  
 Você pode especificar explicitamente o tipo dos elementos em uma matriz que é criada usando um literal de matriz. Nesse caso, os valores no literal da matriz devem ser ampliados para o tipo dos elementos da matriz. O exemplo de código a seguir cria uma matriz do tipo `Double` de uma lista de números inteiros.  
  
 [!code-vb[VbVbalrCollectionInitializers#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#4)]  
  
###  <a name="BKMK_NestedArrayLiterals"></a> Literais de matriz aninhados  
 Você pode criar uma matriz multidimensional usando literais de matriz aninhados. Os literais de matriz aninhados devem ter uma dimensão e o número de dimensões, ou classificação, consistentes com a matriz resultante. O exemplo de código a seguir cria uma matriz bidimensional de números inteiros usando um literal de matriz.  
  
 [!code-vb[VbVbalrCollectionInitializers#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#7)]  
  
 No exemplo anterior, ocorrerá um erro se o número de elementos em literais de matriz aninhados não corresponder. Também ocorre um erro se você declarou explicitamente a variável de matriz como não sendo bidimensional.  
  
> [!NOTE]
>  Você pode evitar um erro ao fornecer literais de matriz aninhados de diferentes dimensões colocando os literais de matriz interna entre parênteses. Os parênteses forçam a avaliação da expressão literal de matriz, e os valores resultantes são usados com o literal de matriz externo, como mostra o código a seguir.  
  
 [!code-vb[VbVbalrCollectionInitializers#11](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#11)]  
  
 Ao criar uma matriz multidimensional usando literais de matriz aninhados, você pode usar inferência de tipos. Quando você usa a inferência de tipos, o tipo inferido é o tipo dominante para todos os valores em todos os literais de matriz para um nível de aninhamento. O exemplo de código a seguir cria uma matriz bidimensional de tipo `Double` de valores que são do tipo `Integer` e `Double`.  
  
 [!code-vb[VbVbalrCollectionInitializers#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#8)]  
  
 Para obter exemplos adicionais, consulte [Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md).  
  
##  <a name="BKMK_Iterating"></a> Iterando por uma matriz  
 Quando você itera por uma matriz, pode acessar cada elemento na matriz do índice menor para o índice maior.  
  
 O exemplo a seguir itera por meio de uma matriz unidimensional usando [Para... Próxima instrução](../../../../visual-basic/language-reference/statements/for-next-statement.md). O método <xref:System.Array.GetUpperBound%2A> retorna o valor mais alto que o índice pode ter. O menor valor de índice é sempre 0.  
  
 [!code-vb[VbVbalrArrays#41](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#41)]  
  
 O exemplo a seguir itera por meio de uma matriz multidimensional usando uma instrução `For...Next`. O método <xref:System.Array.GetUpperBound%2A> tem um parâmetro que especifica a dimensão. `GetUpperBound(0)` retorna o valor de índice alto para a primeira dimensão, e `GetUpperBound(1)` retorna o valor de índice alto para a segunda dimensão.  
  
 [!code-vb[VbVbalrArrays#42](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#42)]  
  
 O exemplo a seguir itera por meio de uma matriz unidimensional usando [Para cada...Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 [!code-vb[VbVbalrArrays#43](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#43)]  
  
 O exemplo a seguir itera por meio de uma matriz multidimensional usando uma instrução `For Each...Next`. No entanto, você terá mais controle sobre os elementos de uma matriz multidimensional se usar uma instrução `For…Next` aninhada, como no exemplo anterior, em vez de uma instrução `For Each…Next`.  
  
 [!code-vb[VbVbalrArrays#44](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#44)]  
  
##  <a name="BKMK_ReturnValues"></a> Matrizes como valores de retorno e parâmetros  
 Para retornar uma matriz de um procedimento `Function`, especifique o tipo de dados de matriz e o número de dimensões como o tipo de retorno de [instrução de função](../../../../visual-basic/language-reference/statements/function-statement.md). Dentro da função, declare uma variável da matriz local com o mesmo tipo de dados e número de dimensões. Na [instrução Return](../../../../visual-basic/language-reference/statements/return-statement.md), inclua a variável da matriz local sem parênteses.  
  
 Para especificar uma matriz como um parâmetro para um procedimento `Sub` ou `Function`, defina o parâmetro como uma matriz com um tipo de dados especificado e o número de dimensões. Na chamada para o procedimento, envie uma variável de matriz com o mesmo tipo de dados e o número de dimensões.  
  
 No exemplo a seguir, a função `GetNumbers` retorna um `Integer()`. Esse tipo de matriz é uma matriz unidimensional do tipo `Integer`. O procedimento `ShowNumbers` aceita um argumento `Integer()`.  
  
 [!code-vb[VbVbalrArrays#51](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#51)]  
  
 No exemplo a seguir, a função `GetNumbersMultiDim` retorna um `Integer(,)`. Esse tipo de matriz é uma matriz bidimensional do tipo `Integer`.  O procedimento `ShowNumbersMultiDim` aceita um argumento `Integer(,)`.  
  
 [!code-vb[VbVbalrArrays#52](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#52)]  
  
##  <a name="BKMK_JaggedArrays"></a> Matrizes denteadas  
 Uma matriz que contém outras matrizes como elementos é conhecida como uma matriz de matrizes ou uma matriz denteada. Uma matriz denteada e cada elemento em uma matriz denteada podem ter uma ou mais dimensões. Às vezes, a estrutura de dados em seu aplicativo é bidimensional, mas não retangular.  
  
 O exemplo a seguir tem uma matriz de meses, cada elemento é uma matriz de dias. Como diferentes meses têm diferentes números de dias, os elementos não formam uma matriz bidimensional retangular. Portanto, uma matriz denteada é usada em vez de uma matriz multidimensional.  
  
 [!code-vb[VbVbalrArrays#21](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#21)]  
  
##  <a name="BKMK_ZeroLength"></a> Matrizes de tamanho igual a zero  
 Uma matriz que não contém nenhum elemento também é chamada de uma matriz de tamanho igual a zero. Uma variável que contém uma matriz de tamanho igual a zero não tem o valor `Nothing`. Para criar uma matriz que não tem elementos, declare uma das dimensões da matriz como -1, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrArrays#14](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#14)]  
  
 Talvez seja necessário criar uma matriz de tamanho igual a zero nas seguintes circunstâncias:  
  
-   Sem arriscar uma exceção <xref:System.NullReferenceException>, seu código precisa acessar membros da classe <xref:System.Array>, como <xref:System.Array.Length%2A> ou <xref:System.Array.Rank%2A>, ou chamar uma função [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] como <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Você deseja manter o código de consumo mais simples por não ter que procurar `Nothing` como um caso especial.  
  
-   Seu código interage com uma API (interface de programação do aplicativo) que exige que você passe uma matriz de tamanho igual a zero para um ou mais procedimentos ou retorna uma matriz de tamanho igual a zero de um ou mais procedimentos.  
  
##  <a name="BKMK_ArraySize"></a> Tamanho da matriz  
 O tamanho de uma matriz é o produto dos comprimentos de todas as suas dimensões. Ele representa o número total de elementos contidos no momento na matriz.  
  
 O exemplo a seguir declara uma matriz tridimensional.  
  
```vb
Dim prices(3, 4, 5) As Long  
```  
  
 O tamanho total da matriz na variável `prices` é (3 + 1) x (4 + 1) x (5 + 1) = 120.  
  
 Você pode encontrar o tamanho de uma matriz usando a propriedade <xref:System.Array.Length%2A>. Você pode encontrar o tamanho de cada dimensão de uma matriz multidimensional usando o método <xref:System.Array.GetLength%2A>.  
  
 Você pode redimensionar uma variável de matriz atribuindo um novo objeto de matriz a ela ou usando a instrução `ReDim`.  
  
 Há várias coisas para ter em mente ao lidar com o tamanho de uma matriz.  
  
|||  
|---|---|  
|Tamanho da dimensão|O índice de cada dimensão é baseado em 0, o que significa que ele varia de 0 até o limite superior. Portanto, o tamanho de uma determinada dimensão é maior em 1 dígito que o limite superior declarado para a dimensão.|  
|Limites de comprimento|O tamanho de cada dimensão de uma matriz é limitado ao valor máximo do tipo de dados `Integer`, que é (2 ^ 31) – 1. No entanto, o tamanho total de uma matriz também é limitado pela memória disponível no sistema. Se você tentar inicializar uma matriz que excede a quantidade de RAM disponível, o Common Language Runtime lançará uma exceção <xref:System.OutOfMemoryException>.|  
|Tamanho e tamanho do elemento|Um tamanho de matriz é independente do tipo de dados de seus elementos. O tamanho sempre representa o número total de elementos, não o número de bytes que eles consomem no armazenamento.|  
|Consumo de memória|Não é seguro fazer suposições sobre como uma matriz é armazenada na memória. O armazenamento varia em plataformas de larguras de dados diferentes, então a mesma matriz pode consumir mais memória em um sistema de 64 bits que em um sistema de 32 bits. Dependendo da configuração do sistema ao inicializar uma matriz, o CLR (Common Language Runtime) pode atribuir armazenamento para elementos do pacote o mais próximo possível, ou alinhá-los em limites naturais de hardware. Além disso, uma matriz de armazenamento requer sobrecarga de armazenamento para suas informações de controle, e essa sobrecarga aumenta com cada nova dimensão.|  
  
##  <a name="BKMK_ArrayTypes"></a> Tipos de matriz e outros tipos  
 Cada matriz tem um tipo de dados, que difere do tipo de dados de seus elementos. Não há nenhum tipo de dados único para todas as matrizes. Em vez disso, o tipo de dados de uma matriz é determinado pelo número de dimensões, ou *classificação*, da matriz e o tipo de dados dos elementos na matriz. Duas variáveis de matriz são consideradas tendo os mesmos dados somente quando elas têm a mesma classificação e quando seus elementos têm os mesmo tipo de dados. Os comprimentos das dimensões de uma matriz não influenciam o tipo de dados de matriz.  
  
 Cada matriz herda da classe <xref:System.Array?displayProperty=fullName> e você pode declarar uma variável para ser do tipo `Array`, mas não pode criar uma matriz do tipo `Array`. Além disso, a [instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md) não pode operar em uma variável declarada como tipo `Array`. Por esses motivos, e para a segurança de tipo, é aconselhável declarar cada matriz como um tipo específico, como `Integer` no exemplo anterior.  
  
 Você pode descobrir o tipo de dados de uma matriz ou seus elementos de várias maneiras.  
  
-   Você pode chamar o método <xref:System.Object.GetType%2A?displayProperty=fullName> na variável para receber um objeto <xref:System.Type> para o tipo de tempo de execução da variável. O objeto <xref:System.Type> mantém informações abrangentes em suas propriedades e métodos.  
  
-   Você pode passar a variável para o a função <xref:Microsoft.VisualBasic.Information.TypeName%2A> para receber um `String` que contém o nome do tipo de tempo de execução.  
  
-   Você pode passar a variável para a função <xref:Microsoft.VisualBasic.Information.VarType%2A> para receber um valor `VariantType` que representa a classificação de tipo da variável.  
  
 O exemplo a seguir chama a função `TypeName` para determinar o tipo da matriz e o tipo dos elementos na matriz. O tipo de matriz é `Integer(,)` e os elementos na matriz são do tipo `Integer`.  
  
 [!code-vb[VbVbalrArrays#15](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#15)]  
  
##  <a name="BKMK_Collections"></a> Coleções como uma alternativa para matrizes  
 As matrizes são mais úteis para criar e trabalhar com um número fixo de objetos fortemente tipados. As coleções fornecem uma maneira mais flexível de trabalhar com grupos de objetos. Ao contrário das matrizes, o grupo de objetos com o qual você trabalha pode crescer e reduzir dinamicamente conforme as necessidades do aplicativo são alteradas.  
  
 Se precisar alterar o tamanho de uma matriz, você deverá usar a [instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md). Ao fazer isso, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cria uma nova matriz e libera a matriz anterior para descarte. Isso leva o tempo da execução. Portanto, se o número de itens com o qual você está trabalhando for alterado com frequência ou se você não puder prever o número máximo de itens que precisa, você poderá obter melhor desempenho usando uma coleção.  
  
 Para algumas coleções, você pode atribuir uma chave para qualquer objeto que colocar na coleção para que você possa recuperar rapidamente o objeto, usando a chave.  
  
 Se a coleção contiver elementos de apenas um tipo de dados, você poderá usar uma das classes no namespace <xref:System.Collections.Generic?displayProperty=fullName>. Uma coleção genérica impõe segurança de tipos para que nenhum outro tipo de dados possa ser adicionado a ela. Ao recuperar um elemento de uma coleção genérica, você não precisa determinar seu tipo de dados ou convertê-lo.  
  
 Para obter mais informações sobre coleções, consulte [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir usa a classe genérica [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Collections.Generic.List%601?displayProperty=fullName> para criar uma coleção de lista de objetos `Customer`.  
  
 [!code-vb[VbVbalrArrays#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#1)]  
  
 A declaração da coleção `CustomerFile` especifica que ela pode conter elementos apenas do tipo `Customer`. Ela também fornece uma capacidade inicial de 200 elementos. O procedimento `AddNewCustomer` verifica o novo elemento de validade e o adiciona à coleção. O procedimento `PrintCustomers` usa um loop `For Each` para percorrer a coleção e exibir seus elementos.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Termo|Definição|  
|----------|----------------|  
|[Dimensões de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Explica a classificação e as dimensões em matrizes.|  
|[Como inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)|Descreve como preencher matrizes com valores iniciais.|  
|[Como classificar uma matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md)|Mostra como classificar os elementos de uma matriz em ordem alfabética.|  
|[Como atribuir uma matriz a outra matriz](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Descreve as regras e as etapas para atribuir uma matriz a outra variável de matriz.|  
|[Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Aborda alguns problemas comuns que surgem ao trabalhar com matrizes.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Array>   
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md)

