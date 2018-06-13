---
title: Tipos F#
description: 'Saiba mais sobre os tipos que são usados em F # e como tipos F # nomeados e descritos.'
ms.date: 05/16/2016
ms.openlocfilehash: bdbb89dc751970ac31fe102df009f0bff6388e52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565570"
---
# <a name="f-types"></a>Tipos F#

Este tópico descreve os tipos que são usados em F # e como tipos F # nomeados e descritos.


## <a name="summary-of-f-types"></a>Resumo de tipos F #
Alguns tipos são considerados *tipos primitivos*, como o tipo booliano `bool` e tipos de ponto flutuante e integral de vários tamanhos, que incluem os tipos de bytes e caracteres. Esses tipos são descritos na [tipos primitivos](primitive-types.md).

Outros tipos que são internas à linguagem incluem tuplas, listas, matrizes, as sequências, registros e discriminada uniões. Se você tiver experiência com outras linguagens .NET e aprender a F #, você deve ler os tópicos para cada um desses tipos. Links para obter mais informações sobre esses tipos são incluídos na [tópicos relacionados](https://msdn.microsoft.com/library/#rel) seção deste tópico. Esses F #-suportam para tipos específicos estilos de programação que são comuns a linguagens de programação funcionais. Muitos desses tipos associou módulos que oferecem suporte a esses tipos de operações comuns na biblioteca F #.

O tipo de uma função inclui informações sobre os tipos de parâmetro e tipo de retorno.

O .NET Framework é a origem de tipos de objeto, tipos de interface, tipos delegados e outros. Você pode definir seus próprios tipos de objeto, exatamente como faria em qualquer outra linguagem .NET.

Além disso, o código F # pode definir aliases, que são nomeados *abreviações de tipo*, que são nomes alternativos de tipos. Você pode usar as abreviações de tipo quando o tipo pode ser alterado no futuro e para evitar alterar o código que depende do tipo. Ou, você pode usar uma abreviação de tipo como um nome amigável para um tipo que pode tornar o código mais fácil de ler e entender.

F # fornece tipos de coleção úteis que são criados com uma programação funcional em mente. O uso desses tipos de coleção ajuda a escrever código que está mais funcionando em estilo. Para obter mais informações, consulte [tipos de coleção de F #](fsharp-collection-types.md).


## <a name="syntax-for-types"></a>Sintaxe de tipos
No código F #, você geralmente precisa gravar os nomes de tipos. Cada tipo tem um formulário de sintaxe e usar essas formas sintáticas em anotações de tipo, declarações de método abstract, declarações de delegado, assinaturas e outras construções. Sempre que você declara uma nova construção de programa o interpretador, o interpretador imprime o nome da construção e a sintaxe de seu tipo. Essa sintaxe pode ser apenas um identificador para um tipo definido pelo usuário ou um identificador interno tal como para `int` ou `string`, mas para tipos mais complexos, a sintaxe é mais complexa.

A tabela a seguir mostra os aspectos da sintaxe de tipo para tipos F #.



|Tipo|Sintaxe de tipo|Exemplos|
|----|-----------|--------|
|tipo primitivo|*type-name*|`int`<br /><br />`float`<br /><br />`string`|
|tipo de agregação (classe, estrutura, união, registro, enum e assim por diante)|*type-name*|`System.DateTime`<br /><br />`Color`|
|abreviação de tipo|*nome de abreviação de tipo*|`bigint`|
|tipo totalmente qualificado|*nome do namespaces.Type*<br /><br />ou<br /><br />*nome do Modules.Type*<br /><br />ou<br /><br />*nome do namespaces.Modules.Type*|`System.IO.StreamWriter`|
|array|*nome do tipo*[] ou<br /><br />*nome do tipo* matriz|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|matriz bidimensional|*nome do tipo*[,]|`int[,]`<br /><br />`float[,]`|
|matriz tridimensional|*nome do tipo*[,]|`float[,,]`|
|coleção de itens|*tipo name1* &#42; *tipo name2* ...|Por exemplo, `(1,'b',3)` tem tipo `int * char * int`|
|tipo genérico|*parâmetro de tipo* *nome de tipo genérico*<br /><br />ou<br /><br />*nome de tipo genérico*&lt;*lista de parâmetros de tipo*&gt;|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|(um tipo genérico que tem um argumento de tipo específico fornecido) do tipo construído|*argumento de tipo* *nome de tipo genérico*<br /><br />ou<br /><br />*nome de tipo genérico*&lt;*lista de argumentos de tipo*&gt;|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|tipo de função que tem um único parâmetro|*parâmetro type1*  - &gt; *tipo de retorno*|Uma função que usa um `int` e retorna um `string` tem tipo `int -> string`|
|tipo de função que tem vários parâmetros|*parâmetro type1*  - &gt; *parâmetro type2*  - &gt; ... -&gt; *tipo de retorno*|Uma função que usa um `int` e um `float` e retorna um `string` tem tipo `int -> float -> string`|
|função de ordem superior como um parâmetro|(*tipo de função*)|`List.map` tem o tipo `('a -> 'b) -> 'a list -> 'b list`|
|delegado|Delegar de *tipo de função*|`delegate of unit -> int`|
|tipos flexíveis|#*nome do tipo*|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a>Tópicos relacionados


|Tópico|Descrição|
|-----|-----------|
|[Tipos Primitivos](primitive-types.md)|Descreve os tipos internos simples como tipos integrais, o tipo booliano e tipos de caracteres.|
|[Tipo Unit](unit-type.md)|Descreve o `unit` tipo, um tipo que tem um valor e que é indicado por (); equivalente ao `void` em c# e `Nothing` no Visual Basic.|
|[Tuplas](tuples.md)|Descreve o tipo de tupla, um tipo que consiste em valores associados de qualquer tipo agrupadas em pares, triplos, quadruples e assim por diante.|
|[Opções](options.md)|Descreve o tipo de opção, um tipo que pode ter um valor ou estar vazio.|
|[Listas](lists.md)|Descreve a lista, que são ordenado, imutável série de elementos todos do mesmo tipo.|
|[Matrizes](arrays.md)|Descreve matrizes, que são conjuntos ordenados de elementos mutáveis do mesmo tipo que ocupam um bloco contínuo de memória e são de tamanho fixo.|
|[Sequências](sequences.md)|Descreve o tipo de sequência, que representa uma série de lógica de valores. valores individuais são computados somente quando necessário.|
|[Registros](records.md)|Descreve o tipo de registro, um pequeno agregação de valores nomeados.|
|[Uniões Discriminadas](discriminated-unions.md)|Descreve o tipo de união discriminado, um tipo cujos valores podem ser qualquer um de um conjunto de possíveis tipos.|
|[Funções](functions/index.md)|Descreve os valores de função.|
|[Classes](classes.md)|Descreve o tipo de classe, um tipo de objeto que corresponde a um tipo de referência do .NET. Tipos de classe podem conter membros, propriedades, interfaces implementadas e um tipo base.|
|[Estruturas](structures.md)|Descreve o `struct` tipo, um tipo de objeto que corresponde a um tipo de valor de .NET. O `struct` tipo normalmente representa uma agregação pequenas de dados.|
|[Interfaces](interfaces.md)|Descreve os tipos de interface, que são tipos que representam um conjunto de membros que fornecem algumas funcionalidades, mas que não contêm nenhum dado. Um tipo de interface deve ser implementado por um tipo de objeto para ser útil.|
|[Delegados](delegates.md)|Descreve o tipo de delegado, que representa uma função como um objeto.|
|[Enumerações](enumerations.md)|Descreve os tipos de enumeração, cujos valores pertencem a um conjunto de valores nomeados.|
|[Atributos](attributes.md)|Descreve os atributos que são usados para especificar metadados para outro tipo.|
|[Tipos de Exceção](exception-handling/exception-types.md)|Descreve as exceções, que especificam as informações de erro.|
