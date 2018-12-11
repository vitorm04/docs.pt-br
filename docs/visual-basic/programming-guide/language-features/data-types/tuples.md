---
title: Tuplas no Visual Basic
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: c0198cde88b66f5e115c82b5454bd8a32db7ef96
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143708"
---
# <a name="tuples-visual-basic"></a>Tuplas (Visual Basic)

Começando com o Visual Basic 2017, a linguagem Visual Basic oferece suporte interno para tuplas tornam criar tuplas e acessar os elementos de tuplas mais fácil. Uma tupla é uma estrutura de dados leve que tem um número específico e a sequência de valores. Quando você cria uma instância de tupla, você define o número e o tipo de dados de cada valor (ou elemento). Por exemplo, uma tupla de 2 (ou um par) tem dois elementos. O primeiro pode ser um `Boolean` de valor, enquanto o segundo é um `String`. Porque as tuplas facilitam armazenar diversos valores em um único objeto, elas geralmente são usadas como uma maneira simples de retornar vários valores de um método.

> [!IMPORTANT]
> Suporte de tupla requer o <xref:System.ValueTuple> tipo. Se o .NET Framework 4.7 não estiver instalado, você deve adicionar o pacote do NuGet `System.ValueTuple`, que está disponível na Galeria do NuGet. Sem esse pacote, você pode receber um erro de compilação semelhante a "Tipo predefinido 'ValueTuple(Of,,,)' não está definido ou importado."

## <a name="instantiating-and-using-a-tuple"></a>Instanciando e usando uma tupla

Você instancia uma tupla, colocando os parênteses de mensagens instantâneas de valores delimitada por vírgulas. Cada um desses valores, em seguida, torna-se um campo da tupla. Por exemplo, o código a seguir define um triplo (ou uma tupla de 3) com um `Date` como seu primeiro valor, uma `String` como seu segundo e um `Boolean` como sua terceira.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Por padrão, o nome de cada campo em uma tupla consiste da cadeia de caracteres `Item` juntamente com base em uma posição na tupla. Para essa tupla de 3, o `Date` campo é `Item1`, o `String` campo é `Item2`e o `Boolean` campo é `Item3`. O exemplo a seguir exibe os valores dos campos da tupla instanciado na linha de código anterior

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Os campos de uma tupla de Visual Basic são leitura / gravação; Depois de instanciar uma tupla, você pode modificar seus valores. O exemplo a seguir modifica duas das três campos da tupla criado no exemplo anterior e exibe o resultado.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Instanciando e usando uma tupla nomeada

Em vez de usar nomes padrão para os campos da tupla, você pode criar uma instância de um *tupla nomeada* atribuindo seus próprios nomes de elementos da tupla. Campos da tupla, em seguida, podem ser acessados por seus nomes atribuídos *ou* por seus nomes padrão. O exemplo a seguir instancia a tupla de 3 mesma de antes, exceto que ela nomeia explicitamente o primeiro campo `EventDate`, a segunda `Name`e o terceiro `IsHoliday`. Em seguida, exibe os valores de campo, modifica e exibe os valores de campo novamente.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Nomes de elementos de tupla inferidos

Começando com o Visual Basic 15.3, Visual Basic pode inferir os nomes dos elementos de tupla; não é preciso atribuí-los explicitamente. Nomes de tupla inferidos são úteis quando você inicializar uma tupla a partir de um conjunto de variáveis, e você deseja que o nome do elemento de tupla para ser o mesmo que o nome da variável. 

O exemplo a seguir cria uma `stateInfo` elementos, de chamada de tupla que contém três explicitamente `state`, `stateName`, e `capital`. Observe que, os elementos de nomenclatura, a instrução de inicialização de tupla simplesmente atribui os elementos nomeados os valores das variáveis com nomes idênticos.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Como variáveis e os elementos têm o mesmo nome, o compilador do Visual Basic pode inferir os nomes dos campos, como mostra o exemplo a seguir.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Para habilitar os nomes de elemento de tupla inferidos, você deve definir a versão do compilador do Visual Basic para usar em seu projeto do Visual Basic (\*. vbproj) arquivo: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

O número de versão pode ser qualquer versão do compilador do Visual Basic a partir do 15.3. Em vez de embutir uma versão específica do compilador, você também pode especificar "Mais recente" como o valor do `LangVersion` para compilar com a versão mais recente do compilador do Visual Basic instalado em seu sistema.

Para obter mais informações, consulte [definindo a versão da linguagem Visual Basic](../../../language-reference/configure-language-version.md).

Em alguns casos, o compilador do Visual Basic não é possível inferir o nome do elemento de tupla do nome do candidato, e o campo de tupla só pode ser referenciado usando seu nome padrão, como `Item1`, `Item2`, etc. Elas incluem:

- O nome do candidato é igual ao nome de um membro da tupla, como `Item3`, `Rest`, ou `ToString`.

- O nome do candidato é duplicado na tupla.
 
Quando ocorre falha na inferência de nome de campo, o Visual Basic não gera um erro do compilador, nem é uma exceção gerada em tempo de execução. Em vez disso, os campos de tupla devem ser referenciados por seus nomes predefinidos, como `Item1` e `Item2`. 
  
## <a name="tuples-versus-structures"></a>Tuplas versus estruturas

Uma tupla de Visual Basic é um tipo de valor que é uma instância de um a um **valuetuple** tipos genéricos. Por exemplo, o `holiday` tupla definida no exemplo anterior é uma instância do <xref:System.ValueTuple%603> estrutura. Ele é projetado para ser um contêiner leve para dados. Uma vez que a tupla tem como objetivo tornar mais fácil de criar um objeto com vários itens de dados, ele não tem alguns dos recursos que uma estrutura personalizada pode ter. Elas incluem:

- Membros personalizados. Você não pode definir suas próprias propriedades, métodos ou eventos para uma tupla.

- Validação. Você não pode validar os dados atribuídos a campos.

- Imutabilidade. As tuplas de Visual Basic são mutáveis. Em contraste, uma estrutura personalizada permite que você controle se uma instância é mutável ou imutável.

Se membros personalizados, a propriedade e a validação do campo ou a imutabilidade forem importante, você deve usar o Visual Basic [estrutura](../../../language-reference/statements/structure-statement.md) instrução para definir um tipo de valor personalizado.

Uma tupla de Visual Basic herdam os membros de sua **ValueTuple** tipo. Além de seus campos, isso inclui os seguintes métodos:

| Membro | Descrição |
| ---|---|
| CompareTo | Compara a tupla atual para outra tupla com o mesmo número de elementos. |
| Igual a | Determina se a tupla atual é igual a outro objeto ou tupla. |
| GetHashCode | Calcula o código hash para a instância atual. |
| ToString | Retorna a representação de cadeia de caracteres dessa tupla, que utiliza o formato `(Item1, Item2...)`, onde `Item1` e `Item2` representam os valores dos campos da tupla. |

Além disso, o **ValueTuple** tipos implementam <xref:System.Collections.IStructuralComparable> e <xref:System.Collections.IStructuralEquatable> interfaces, que permitem que você defina os comparadores de cliente.

## <a name="assignment-and-tuples"></a>Atribuição e tuplas

Visual Basic dá suporte à atribuição entre tipos de tupla que têm o mesmo número de campos. Os tipos de campo podem ser convertidos se uma das seguintes opções for verdadeira:

- O campo de origem e destino são do mesmo tipo.

- Uma conversão de ampliação (ou implícita) do tipo de origem para o tipo de destino é definida. 

- `Option Strict` é `On`, e uma conversão de estreitamento (ou explícita) do tipo de origem para o tipo de destino é definida. Essa conversão pode lançar uma exceção se o valor de origem está fora do intervalo do tipo de destino.

Outras conversões não são consideradas para atribuições. Vamos examinar os tipos de atribuições que são permitidos entre tipos de tupla.

Considere estas variáveis usadas nos exemplos a seguir:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

As primeiras duas variáveis, `unnamed` e `anonymous`, não têm nomes semânticos fornecidos para os campos. Seus nomes de campo são o padrão `Item1` e `Item2`. As duas últimas variáveis, `named` e `differentName` têm nomes de campo de semântica. Observe que essas duas tuplas têm nomes diferentes para os campos.

Todas essas quatro tuplas têm o mesmo número de campos (chamados de 'aridades'), e os tipos desses campos são idênticos. Portanto, todas essas atribuições funcionam:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Observe que os nomes das tuplas não são atribuídos. Os valores dos campos são atribuídos na ordem dos campos na tupla.

Finalmente, observe que podemos atribuir a `named` tupla para o `conversion` tupla, mesmo que o primeiro campo da `named` é uma `Integer`e o primeiro campo da `conversion` é um `Long`. Essa atribuição será bem-sucedida porque a conversão de um `Integer` para um `Long` é uma conversão de ampliação.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

As tuplas com diferentes números de campos não são atribuíveis:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Tuplas como valores retornados do método

Um método pode retornar apenas um único valor. Com frequência, no entanto, seria uma chamada de método para retornar vários valores. Há várias maneiras de contornar essa limitação:

- Você pode criar uma classe personalizada ou uma estrutura cujas propriedades ou campos representam valores retornados pelo método. Portanto, é uma solução pesada; ele requer que você definir um tipo personalizado, cuja única finalidade é recuperar valores de uma chamada de método.

- Você pode retornar um único valor do método e retornar os valores restantes, passando-os por referência para o método. Isso envolve a sobrecarga de instanciar uma variável e riscos substitua inadvertidamente o valor da variável que é passada por referência.

- Você pode usar uma tupla que fornece uma solução leve para recuperar vários valores de retorno.

Por exemplo, o **TryParse** métodos de retorno de .NET uma `Boolean` valor que indica se a operação de análise foi bem-sucedida. O resultado da operação de análise é retornado em uma variável passada por referência para o método. Normalmente, uma chamada para a um método de análise, como <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> é semelhante ao seguinte:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Podemos pode retornar uma tupla da operação de análise se podemos encapsular a chamada para o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método no nosso próprio método. No exemplo a seguir `NumericLibrary.ParseInteger` chama o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método e retorna uma tupla nomeada com dois elementos. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Em seguida, você pode chamar o método com um código semelhante ao seguinte:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Tuplas de Visual Basic e tuplas no .NET Framework

Uma tupla de Visual Basic é uma instância de um dos **valuetuple** tipos genéricos, que foram introduzidos no .NET Framework 4.7. O .NET Framework também inclui um conjunto de genérico **System. Tuple** classes. Essas classes, no entanto, são diferentes das tuplas de Visual Basic e o **valuetuple** tipos genéricos de várias maneiras:

- Os elementos do **tupla** classes são as propriedades nomeadas `Item1`, `Item2`e assim por diante. No Visual Basic tuplas e o **ValueTuple** tipos de elementos de tupla são os campos.

- Você não pode atribuir nomes significativos para os elementos de uma **tupla** instância ou de uma **ValueTuple** instância. Visual Basic permite que você atribua nomes de comunicam o significado dos campos.

- As propriedades de um **tupla** instância são somente leitura; as tuplas são imutáveis. No Visual Basic tuplas e o **ValueTuple** tipos, campos da tupla são leitura / gravação; as tuplas são mutáveis.

- Genérica **tupla** tipos são tipos de referência. Usando essas **tupla** significa alocar objetos de tipos. Em caminhos de acesso, isso pode ter um impacto mensurável no desempenho do aplicativo. As tuplas do Visual Basic e o **ValueTuple** tipos são tipos de valor.

Métodos de extensão na <xref:System.TupleExtensions> classe tornam mais fácil converter entre as tuplas do Visual Basic e .NET **tupla** objetos. O **ToTuple** método converte uma tupla de Visual Basic para um .NET **tupla** objeto e o **ToValueTuple** método converte um .NET **tupla** objeto a ser uma tupla de Visual Basic.

O exemplo a seguir cria uma tupla, converte-o em um .NET **tupla** objeto e converte-o novamente para uma tupla de Visual Basic. O exemplo, em seguida, compara essa tupla pelo original para garantir que eles são iguais.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Consulte também

[Referência da linguagem Visual Basic](index.md)  
