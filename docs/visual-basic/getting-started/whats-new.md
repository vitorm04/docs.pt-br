---
title: Novidades do Visual Basic
ms.date: 02/15/2018
f1_keywords:
- VB.StartPage.WhatsNew
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09a113130d29336ecabb52095ca7f5809f5f0ade
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-for-visual-basic"></a>Novidades do Visual Basic

Este tópico lista os nomes das principais funcionalidades para cada versão do Visual Basic, com descrições detalhadas das funcionalidades novas e aprimoradas na versão mais recente da linguagem.
  
## <a name="current-version"></a>Versão atual

Visual Basic 15.5   
Para as novas funcionalidades, consulte [Visual Basic 15.5](#visual-basic-155)

## <a name="previous-versions"></a>Versões anteriores

Visual Basic 15.3   
Para as novas funcionalidades, consulte [Visual Basic 15.3](#visual-basic-153)

Visual Basic 2017   
Para as novas funcionalidades, consulte [Visual Basic 2017](#visual-basic-2017)

Visual Basic / Visual Studio .NET 2015   
Para as novas funcionalidades, consulte [Visual Basic 14](#visual-basic-14)

Visual Basic / Visual Studio .NET 2013  
Visualizações de tecnologia da Plataforma do Compilador .NET (“Roslyn”)

Visual Basic / Visual Studio .NET 2012   
palavras-chave `Async` e `await`, iteradores, atributos de informações do chamador

Visual Basic, Visual Studio .NET 2010   
Propriedades autoimplementadas, inicializadores de coleção, continuação de linha implícita, covariância/contravariância genérica, acesso ao namespace global

Visual Basic / Visual Studio .NET 2008   
LINQ (consulta integrada à linguagem), literais XML, inferência de tipos de variável local, inicializadores de objeto, tipos anônimos, métodos de extensão, inferência de tipos `var` local, expressões lambda, operador `if`, métodos parciais, tipos de valor anulável  

Visual Basic / Visual Studio .NET 2005   
O tipo `My` e tipos auxiliares (acesso ao aplicativo, computador, sistema de arquivos, rede)

Visual Basic / Visual Studio .NET 2003   
Operadores bit shift, declaração de variável de loop

Visual Basic / Visual Studio .NET 2002   
A primeira versão do Visual Basic .NET

## <a name="visual-basic-155"></a>Visual Basic 15.5

[Argumentos nomeados que não estejam à direita](../programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md#mixing-arguments-by-position-and-by-name)

No Visual Basic 15.3 e nas versões anteriores, quando uma chamada de método incluía argumentos por posição e por nome, os argumentos posicionais tinham que preceder os argumentos nomeados. A partir do Visual Basic 15.5 os argumentos posicionais e nomeados podem aparecer em qualquer ordem, desde que todos os argumentos, até o último argumento posicional, estejam na posição correta. Isso é especialmente útil quando os argumentos nomeados são usados para tornar o código mais legível.

Por exemplo, a seguinte chamada de método tem dois argumentos posicionais entre um argumento nomeado. O argumento nomeado deixa claro que o valor 19 representa uma idade.

```vb
StudentInfo.Display("Mary", age:=19, #9/21/1998#)
```

**Separador hex/binário/octal à esquerda**

O Visual Basic 2017 agora tem suporte para o caractere de sublinhado (`_`) como um separador de dígito. A partir do Visual Basic 15.5, você pode usar o caractere de sublinhado como separador à esquerda entre o prefixo e os dígitos binários, hexadecimais ou octais. O exemplo a seguir usa um separador de dígito à esquerda para definir 3.271.948.384 como um número hexadecimal:

```vb
Dim number As Integer = &H_C305_F860
``` 
Para usar o caractere de sublinhado como um separador à esquerda, você deve adicionar o seguinte elemento ao arquivo de projeto (\*.vbproj) do Visual Basic:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="visual-basic-153"></a>Visual Basic 15.3

[**Inferência de tupla nomeada**](../programming-guide/language-features/data-types/tuples.md#inferred-tuple-element-names)

Quando você atribui o valor de elementos de tupla com base em variáveis, o Visual Basic infere o nome dos elementos de tupla dos nomes de variável correspondentes; não é necessário nomear explicitamente um elemento de tupla. O exemplo a seguir usa a inferência para criar uma tupla com três elementos nomeados, `state`, `stateName` e `capital`.

[!code-vb[Inferred tuple names](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

**Opções adicionais do compilador**  

O compilador de linha de comando do Visual Basic agora é compatível com as opções do compilador [**-refout**](../reference/command-line-compiler/refout-compiler-option.md) e [**-refonly**](../reference/command-line-compiler/refonly-compiler-option.md) para controlar a saída de assemblies de referência. A **-refout** define o diretório de saída do assembly de referência e a **-refonly** especifica que somente um assembly de referência deve ser produzido pela compilação.

## <a name="visual-basic-2017"></a>Visual Basic 2017

[**Tuplas**](../programming-guide/language-features/data-types/tuples.md)

As tuplas são uma estrutura de dados leve que é mais comumente usada para retornar vários valores de uma única chamada de método. Normalmente, para retornar vários valores de um método, você precisa realizar uma das seguintes ações:

- Defina um tipo personalizado (uma `Class` ou `Structure`). Esta é uma solução pesada.

- Definir um ou mais parâmetros `ByRef`, além de retornar um valor do método.
 
O suporte do Visual Basic para tuplas permite definir rapidamente uma tupla, opcionalmente atribuir nomes semânticos para seus valores e recuperar rapidamente seus valores. O exemplo a seguir encapsula uma chamada para o método <xref:System.Int32.TryParse%2A> e retorna uma tupla.

[!code-vb[Tuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

O chamador pode então chamar o método e manipular a tupla retornada com o código semelhante ao seguinte.

[!code-vb[ReturnTuple](../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)] 

**Literais binários e os separadores de dígito**

Você pode definir um literal binário usando o prefixo `&B` ou `&b`. Além disso, você pode usar o caractere de sublinhado, `_`, como um separador de dígitos para melhorar a legibilidade. O exemplo a seguir usa as duas funcionalidades para atribuir um valor `Byte` e exibi-lo como um número decimal, hexadecimal e binário.

[!code-vb[Binary](../../../samples/snippets/visualbasic/getting-started/bin-example.vb#1)]

Para obter mais informações, consulte a seção "Atribuições de literal" dos tipos de dados [Byte](../language-reference/data-types/byte-data-type.md#literal-assignments), [Integer](../language-reference/data-types/integer-data-type.md#literal-assignments), [Long](../language-reference/data-types/long-data-type.md#literal-assignments), [Short](../language-reference/data-types/short-data-type.md#literal-assignments), [SByte](../language-reference/data-types/sbyte-data-type.md#literal-assignments), [UInteger](../language-reference/data-types/uinteger-data-type.md#literal-assignments), [ULong](../language-reference/data-types/ulong-data-type.md#literal-assignments) e [UShort](../language-reference/data-types/ushort-data-type.md#literal-assignments).

**Suporte para valores retornados de referência do C#**

Começando com o C# 7.0, o C# é compatível com valores retornados de referência. Isto é, quando o método de chamada recebe um valor retornado por referência, ele pode alterar o valor da referência. O Visual Basic não permite a criação de métodos com valores retornados de referência, mas isso não permite o consumo e a modificação de valores de retorno de referência.

Por exemplo, a classe `Sentence` a seguir escrita em C# inclui um método `FindNext` que localiza a próxima palavra em uma sentença que começa com uma subcadeia de caracteres especificada. A cadeia de caracteres é retornada como um valor retornado de referência e uma variável `Boolean` passada pela referência para o método indica se a pesquisa foi bem-sucedida. Isso significa que o chamador não pode apenas ler o valor retornado, ele também pode modificá-lo e essa modificação é refletida na classe `Sentence`.

[!code-csharp[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

Em sua forma mais simples, você pode modificar a palavra encontrada na frase usando um código semelhante ao seguinte. Observe que você não está atribuindo um valor ao método, mas para a expressão que o método retorna, que é o valor retornado de referência.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#1)]

Um problema com esse código, no entanto, é que, se uma correspondência não for encontrada, o método retornará a primeira palavra. Como o exemplo não examina o valor do argumento `Boolean` para determinar se uma correspondência foi encontrada, ele modificará a primeira palavra se não houver nenhuma correspondência. O exemplo a seguir corrige isso substituindo a primeira palavra por ela mesma se não há nenhuma correspondência.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return.vb#2)]

Uma solução melhor é usar um método auxiliar para o qual o valor retornado de referência é passado por referência. O método auxiliar pode modificar o argumento passado para ele por referência. O exemplo a seguir faz isso.

[!code-vb[Ref-Return](../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

Para obter mais informações, consulte [Reference return values](../programming-guide/language-features/procedures/ref-return-values.md) (Valores retornados de referência).

## <a name="visual-basic-14"></a>Visual Basic 14

[Nameof](../../csharp/language-reference/keywords/nameof.md)  
 Você pode obter o nome da cadeia de caracteres não qualificada de um tipo ou de um membro para uso em uma mensagem de erro sem realizar hard-coding de uma cadeia de caracteres.  Isso permite que seu código permaneça correto ao refatorar.  Esse recurso também é útil para conectar links MVC do tipo modelo-exibição-controlador e acionar eventos de alteração de propriedade.  
  
[Interpolação de cadeia de caracteres](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)  
 Você pode usar expressões de interpolação de cadeia de caracteres para construir cadeias de caracteres.  Uma expressão de cadeia de caracteres interpolada é semelhante a uma cadeia de caracteres de modelo que contém expressões.  Uma cadeia de caracteres interpolada é mais fácil de entender, em relação aos argumentos, do que a [formatação de composição](../../standard/base-types/composite-format.md).  
  
[Acesso de membro nulo condicional e indexação](../../csharp/language-reference/operators/null-conditional-operators.md)  
Você pode testar a nulidade de uma maneira sintática muito simples antes de executar uma operação de acesso de membro (`?.`) ou índice (`?[]`).  Esses operadores ajudam a escrever menos código para lidar com verificações de nulidade, especialmente para entrar em estruturas de dados.  Se a referência de objeto ou o operando esquerdo for nulo, as operações retornarão valores nulos.  
  
[Literais de cadeia de caracteres multilinha](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 Literais de cadeia de caracteres podem conter sequências de nova linha.  Você não precisa da solução alternativa antiga de usar `<xml><![CDATA[...text with newlines...]]></xml>.Value`  
  
Comentários  
É possível colocar comentários após continuações de linha implícitas, em expressões de inicializador e entre termos de expressão do LINQ.  
  
 Resolução de nome totalmente qualificado mais inteligente  
 Dado um código como `Threading.Thread.Sleep(1000)`, o Visual Basic pesquisava o namespace "Threading", descobria que ele era ambíguo entre System.Threading e System.Windows.Threading e, então, relatava um erro.  Agora, o Visual Basic considera os dois namespaces possíveis juntos.  Se você mostrar a lista de conclusão, o editor do Visual Studio listará membros dos dois tipos na lista de conclusão.  
  
 Literais de data do primeiro ano  
 Você pode ter literais de data no formato aaaa-mm-dd, `#2015-03-17 16:10 PM#`.  
  
 Propriedades de interface readonly  
 Você pode implementar propriedades de interface readonly usando uma propriedade readwrite.  A interface garante a funcionalidade mínima e não impede que uma classe de implementação permita que a propriedade seja definida.  
  
 [TypeOf \<expr> IsNot \<type>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 Para facilitar a leitura do seu código, agora você pode usar `TypeOf` com `IsNot`.  
  
 [#Disable Warning \<ID> e #Enable Warning \<ID>](../../visual-basic/language-reference/directives/directives.md)  
 É possível desabilitar e habilitar avisos específicos para regiões dentro de um arquivo de origem.  
  
 Aprimoramentos de comentário de documento XML  
 Ao escrever comentários de documento, você obtém o editor inteligente e suporte de build para validar nomes de parâmetro, tratamento adequado de `crefs` (genéricos, operadores etc.), coloração e refatoração.  
  
 [Definições de interface e módulo parcial](../../visual-basic/language-reference/modifiers/partial.md)  
 Além das classes e structs, você pode declarar interfaces e módulos parciais.  
  
 [Diretivas #Region dentro de corpos de método](../../visual-basic/language-reference/directives/region-directive.md)  
 Você pode colocar delimitadores #Region...#End Region em qualquer lugar em um arquivo, dentro de funções e até mesmo estendê-los por corpos de função.  
  
 [Definições de substituição são sobrecargas implicitamente](../../visual-basic/language-reference/modifiers/overrides.md)  
 Se você adicionar o modificador `Overrides` a uma definição, o compilador adicionará implicitamente `Overloads`, para que você possa digitar menos código em casos comuns.  
  
 CObj permitido em argumentos de atributos  
 O compilador apresentava um erro de que CObj(...) não era uma constante quando usado em construções de atributo.  
  
 Declarando e consumindo métodos ambíguos de interfaces diferentes  
 Anteriormente, o código a seguir gerava erros que impediam você de declarar `IMock` ou chamar `GetDetails` (se eles tivessem sido declarados em C#):  
  
```vb  
Interface ICustomer  
  Sub GetDetails(x As Integer)  
End Interface  
  
Interface ITime  
  Sub GetDetails(x As String)  
End Interface  
  
Interface IMock : Inherits ICustomer, ITime  
  Overloads Sub GetDetails(x As Char)  
End Interface  
  
Interface IMock2 : Inherits ICustomer, ITime  
End Interface  
```  
  
 Agora, o compilador usará regras de resolução de sobrecarga normais para escolher o `GetDetails` mais apropriado a ser chamado e você pode declarar relações de interface no Visual Basic, como aquelas mostradas no exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [Novidades no Visual Studio 2017](/visualstudio/ide/whats-new-in-visual-studio)
