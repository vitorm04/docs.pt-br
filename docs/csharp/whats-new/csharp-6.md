---
title: Novidades no C# 6 – Guia do C#
description: Aprenda os novos recursos da versão 6 do C#
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: 00aeb3ed940acfca748a1a9eb876fd0133baf6c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-6"></a>Novidades no C# 6

A versão 6.0 do C# tinha muitos recursos para melhorar a produtividade para desenvolvedores. Os recursos nesta versão incluem:

* [Propriedades automáticas somente leitura](#read-only-auto-properties):
    - Você pode criar propriedades automáticas somente leitura que podem ser definidas apenas em construtores.
* [Inicializadores de propriedade automática](#auto-property-initializers):
    - Você pode escrever expressões de inicialização para definir o valor inicial de uma propriedade automática.
* [Membros de função aptos para expressão](#expression-bodied-function-members):
    - Você pode criar métodos de uma linha usando expressões lambda.
* [using static](#using-static):
    - Você pode importar todos os métodos de uma única classe para o namespace atual.
* [Null – operadores condicionais](#null-conditional-operators):
    - Você pode acessar membros de um objeto com segurança e de forma concisa, durante a verificação de null, com o operador condicional null.
* [Interpolação de cadeia de caracteres](#string-interpolation):
    - Você pode escrever expressões de formatação de cadeias de caracteres, usando expressões embutidas em vez de argumentos posicionais.
* [Filtros de exceção](#exception-filters):
    - Você pode capturar expressões com base nas propriedades da exceção ou outro estado do programa. 
* [Expressões nameof](#nameof-expressions):
    - Você pode deixar que o compilador gere representações de cadeia de caracteres de símbolos.
* [await em blocos catch e finally](#await-in-catch-and-finally-blocks):
    - Você pode usar expressões `await` em locais que antes não era permitido.
* [Inicializadores de índice](#index-initializers):
    - Você pode criar expressões de inicialização para contêineres associativos, bem como para contêineres de sequência.
* [Métodos de extensão para inicializadores de coleção](#extension-add-methods-in-collection-initializers):
    - Os inicializadores de coleção podem depender de métodos de extensão acessíveis, além dos métodos de membro.
* [Resolução de sobrecarga aprimorada](#improved-overload-resolution):
    - Alguns constructos, que antes geravam chamadas de método ambíguas, agora resolvem corretamente.

O efeito geral desses recursos é que você escreve código mais conciso e também mais legível. A sintaxe contém menos cerimônia para várias práticas comuns. É mais fácil de ver a intenção do design com menos cerimônia. Aprenda bem esses recursos e você será mais produtivo, escreverá um código mais legível e se concentrará mais em seus recursos principais que nos constructos da linguagem.

O restante deste tópico fornece detalhes sobre cada um desses recursos.

## <a name="auto-property-enhancements"></a>Aprimoramentos de propriedade automática 

A sintaxe para propriedades implementadas automaticamente (geralmente conhecidas como 'propriedades automáticas ') facilitou muito a criação de propriedades que tinham acessadores simples get e set:

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

No entanto, essa sintaxe simplificada limitava os tipos de design que tinham suporte com o uso de propriedades automáticas. O C# 6 aprimora os recursos das propriedades automáticas para que você possa usá-las em mais cenários. Você não precisará voltar à sintaxe mais detalhada de declaração e manipulação do campo de suporte manualmente com tanta frequência.

A nova sintaxe aborda cenários para propriedades somente leitura e para inicializar o armazenamento de variável atrás de uma propriedade automática.

### <a name="read-only-auto-properties"></a>Propriedades automáticas somente leitura

As *Propriedades automáticas somente leitura* fornecem uma sintaxe mais concisa para criar tipos imutáveis. O mais próximo você chegava em relação a tipos imutáveis nas versões anteriores do C# era para declarar setters particulares:

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
Ao usar esta sintaxe, o compilador não garante que o tipo é realmente imutável. Ele somente impõe que as propriedades `FirstName` e `LastName` não são modificadas de qualquer código fora da classe.

As propriedades automáticas somente leitura habilitam o verdadeiro comportamento somente leitura. Você declara a propriedade automática apenas com um acessador get:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

As propriedades `FirstName` e `LastName` só podem ser definidas no corpo de um construtor:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

A tentativa de definir `LastName` em outro método gera um erro de compilação `CS0200`:

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

Esse recurso habilita o suporte real à linguagem para criar tipos imutáveis e usar a sintaxe de propriedade automática mais concisa e conveniente.

### <a name="auto-property-initializers"></a>Inicializadores de propriedade automática

Os *Inicializadores de propriedade automática* permitem que você declare o valor inicial de uma propriedade automática como parte da declaração de propriedade.  Em versões anteriores, essas propriedades precisariam de setters e você teria que usar esse setter para inicializar o armazenamento de dados usado pelo campo de suporte. Considere essa classe para um aluno que contém o nome e uma lista das notas do aluno:

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
Conforme essa classe cresce, você pode incluir outros construtores. Cada construtor precisa inicializar este campo ou você introduzirá erros.

O C# 6 permite que você atribua um valor inicial para o armazenamento usado por uma propriedade automática na declaração da propriedade automática:

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

O membro `Grades` é inicializado no local em que é declarado. Isso facilita realizar a inicialização exatamente uma vez. A inicialização faz parte da declaração de propriedade, tornando mais fácil igualar a alocação de armazenamento com a interface pública para objetos `Student`.

Os inicializadores de propriedade podem ser usados com propriedades de leitura/gravação bem como com as propriedades de somente leitura, conforme mostrado aqui.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>Membros de função aptos para expressão

O corpo de muitos membros que escrevemos consiste em apenas uma instrução, que pode ser representada como uma expressão. Você pode reduzir essa sintaxe, escrevendo um membro apto para expressão. Isso funciona para métodos e propriedades somente leitura. Por exemplo, uma substituição de `ToString()` é, geralmente, uma ótima candidata:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Você também pode usar membros aptos para expressão em propriedades somente leitura:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a>usando estático

O aprimoramento *using static* permite que você importe os métodos estáticos de uma única classe. Anteriormente, a instrução `using` importava todos os tipos de um namespace. 

Com frequência usamos métodos estáticos de uma classe em todo o nosso código. Digitar o nome de classe repetidamente pode obscurecer o significado do seu código. Um exemplo comum é quando você escreve classes que realizam muitos cálculos numéricos.
Seu código ficará repleto <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> e outras chamadas a métodos diferentes na classe <xref:System.Math>. A nova sintaxe `using static` pode deixar essas classes muito mais limpas para serem lidas. Você especifica a classe que está usando:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

E agora, você pode usar qualquer método estático na classe <xref:System.Math> sem qualificar a classe <xref:System.Math>. A classe <xref:System.Math> é um ótimo caso de uso desse recurso, porque ela não contém nenhum método de instância. Você também pode usar `using static` para importar os métodos estáticos de uma classe para uma classe que tem os métodos estáticos e de instância. Um dos exemplos mais úteis é <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Você deve usar o nome de classe totalmente qualificado `System.String` em uma instrução static using. Não é possível usar a palavra-chave `string` em vez disso. 

Agora você pode chamar métodos estáticos definidos na classe <xref:System.String> sem qualificar esses métodos como membros dessa classe:

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

O recurso `static using` e os métodos de extensão interagem de maneiras interessantes e o design de linguagem incluiu algumas regras que tratam especificamente dessas interações. A meta é minimizar qualquer possibilidade de alterações significativas nas bases de código existentes, incluindo a sua.

Os métodos de extensão só estão no escopo quando chamados usando a sintaxe de invocação do método de extensão e não quando chamados como um método estático.
Você verá isso com frequência em consultas LINQ. Você pode importar o padrão LINQ importando <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Isso importa todos os métodos na classe <xref:System.Linq.Enumerable>.
No entanto, os métodos de extensão somente estão no escopo quando chamados como métodos de extensão. Eles não estão no escopo se chamados usando a sintaxe de método estático:

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Essa decisão foi tomada porque os métodos de extensão são geralmente chamados usando expressões de invocação de método de extensão. No caso raro em que eles são chamados usando a sintaxe de chamada ao método estático, é para resolver a ambiguidade.
Parece prudente exigir o nome de classe como parte da invocação.

Há um último recurso de `static using`. A diretiva `static using` também importa todos tipos aninhados. Isso habilita você a referenciar qualquer tipo aninhado sem qualificação.

## <a name="null-conditional-operators"></a>Operadores condicionais null

Os valores null complicam o código. É necessário verificar cada acesso de variáveis para garantir que você não está desreferenciando `null`. O *operador condicional null* torna essas verificações muito mais fáceis e fluidas.

Basta substituir o acesso de membro `.` por `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

No exemplo anterior, a variável `first` é atribuída como `null` se o objeto person é `null`. Caso contrário, ela é atribuída com o valor da propriedade `FirstName`. Mais importante, o `?.` significa que essa linha de código não gerará um `NullReferenceException` quando a variável `person` for `null`. Em vez disso, ela encurta o caminho e produz `null`.

Além disso, observe que essa expressão retorna uma `string`, independentemente do valor de `person`.
No caso de encurtar o caminho, o valor `null` retornado é tipado para corresponder à expressão completa.

Você também pode usar esse constructo com o operador *null coalescing* para atribuir valores padrão quando uma das propriedades é `null`:

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

O operando do lado direito do operador `?.` não está limitado a campos ou propriedades.
Você também pode usá-lo para invocar métodos de maneira condicional. O uso mais comum de funções membro com o operador condicional null é para invocar delegados com segurança (ou manipuladores de eventos) que podem ser `null`.  Você fará isso chamando o método `Invoke` do delegado, usando o operador `?.` para acessar o membro. Você pode ver um exemplo no  
tópico [padrões delegados](../delegates-patterns.md#handling-null-delegates).

As regras do operador `?.` garantem que o lado esquerdo do operador é avaliado apenas uma vez. Isso é importante e habilita muitas expressões, incluindo o exemplo com o uso de manipuladores de eventos. Vamos começar com o uso do manipulador de eventos. Nas versões anteriores do C#, você era incentivado a escrever código assim:

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

Isso era preferível em relação a uma sintaxe mais simples:

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> O exemplo anterior introduz uma condição de corrida. O evento `SomethingHappened` pode ter assinantes quando verificado em relação a `null` e esses assinantes podem ter sido removidos antes de o evento ser acionado. Isso poderia causar o lançamento de uma <xref:System.NullReferenceException>.

Nesta segunda versão, o manipulador de eventos `SomethingHappened` pode ser não nulo quando testado, mas se outro código remover um manipulador, ele ainda poderia ser null quando o manipulador de eventos foi chamado.

O compilador gera um código para o operador `?.`, que garante que o lado esquerdo (`this.SomethingHappened`) da expressão `?.` é avaliado uma vez e o resultado é armazenado em cache:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Garantir que o lado esquerdo seja avaliado apenas uma vez também habilita você a usar qualquer expressão, inclusive chamadas de método, no lado esquerdo do `?.`. Mesmo que elas tenham efeitos colaterais, elas serão avaliadas uma vez e os efeitos colaterais ocorrerão apenas uma vez. Você pode ver um exemplo em nosso conteúdo em [eventos](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Interpolação de cadeia de caracteres

O C# 6 contém uma nova sintaxe para compor cadeias de caracteres com base em uma cadeia de caracteres de formato e de expressões que são avaliadas para produzir outros valores de cadeia de caracteres.

Tradicionalmente, você precisava usar parâmetros posicionais em um método como `string.Format`:

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

Com o C# 6, o novo recurso de [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) permite que você insira as expressões na cadeia de caracteres de formato. Basta preceder a cadeia de caracteres com `$`:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Este exemplo inicial usou expressões de propriedade para as expressões substituídas. Você pode expandir esta sintaxe para usar qualquer expressão. Por exemplo, você pode calcular a média do aluno como parte da interpolação:

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

Ao executar o exemplo anterior, você veria que a saída de `Grades.Average()` pode ter mais casas decimais do que o desejado. A sintaxe de interpolação de cadeia de caracteres dá suporte a todas as cadeias de caracteres de formato disponíveis que usam métodos de formatação anteriores. Você adiciona as cadeias de caracteres de formato dentro de chaves. Adicione um `:` seguido da expressão a ser formatada:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

A linha de código anterior formata o valor de `Grades.Average()` como um número de ponto flutuante com duas casas decimais.

O `:` é sempre interpretado como o separador entre a expressão que está sendo formatada e a cadeia de caracteres de formato. Isso pode causar problemas quando a expressão usa um `:` de outra forma, como um operador condicional:

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

No exemplo anterior, o `:` é analisado como o início da cadeia de caracteres de formato e não como parte do operador condicional. Em todos os casos em que isso ocorre, você pode colocar a expressão entre parênteses para forçar o compilador a interpretar a expressão como você deseja:

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Não há limitações em expressões que você pode colocar entre as chaves. Você pode executar uma consulta LINQ complexa dentro de uma cadeia de caracteres interpolada para realizar cálculos e exibir o resultado:

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

Neste exemplo você pode ver que é até mesmo possível aninhar uma expressão de interpolação de cadeia de caracteres dentro de outra expressão de interpolação de cadeia de caracteres. É muito provável que este exemplo seja mais complexo do que você desejaria no código de produção.
No entanto, ele serve para ilustrar abrangência do recurso. Qualquer expressão de C# pode ser colocada entre as chaves de uma cadeia de caracteres interpolada.

### <a name="string-interpolation-and-specific-cultures"></a>Interpolação de cadeia de caracteres e culturas específicas

Todos os exemplos mostrados na seção anterior formatam as cadeias de caracteres usando a cultura e o idioma atuais do computador em que o código é executado. Com frequência, talvez seja necessário formatar a cadeia de caracteres gerada, usando uma cultura específica.
Para fazer isso, aproveite o fato de que o objeto produzido por uma interpolação de cadeia de caracteres pode ser convertido implicitamente em <xref:System.FormattableString>.

A instância <xref:System.FormattableString> contém a cadeia de caracteres de formato e os resultados da avaliação de expressões antes de convertê-los em cadeias de caracteres. Você pode usar métodos públicos de <xref:System.FormattableString> para especificar a cultura ao formatar uma cadeia de caracteres. Por exemplo, o exemplo a seguir produz uma cadeia de caracteres usando a cultura alemã. (ele usa o caractere ',' como o separador decimal e o caractere '.' como separador de milhares).

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Para obter mais informações, consulte o tópico [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md).

## <a name="exception-filters"></a>Filtros de exceção

Outro recurso novo no C# 6 são os *filtros de exceção*. Os filtros de exceção são cláusulas que determinam quando uma determinada cláusula catch deve ser aplicada.
Se a expressão usada para um filtro de exceção é avaliada como `true`, a cláusula catch realiza seu processamento normal em uma exceção. Se a expressão for avaliada como `false`, a cláusula `catch` será ignorada.

Um uso é examinar informações sobre uma exceção para determinar se uma cláusula `catch` pode processar a exceção:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

O código gerado pelos filtros de exceção fornece melhores informações sobre uma exceção que é lançada e não é processada. Antes que os filtros de exceção fossem adicionados à linguagem, era preciso criar código semelhante ao seguinte:

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

O ponto em que a exceção é lançada muda nestes dois exemplos.
No código anterior, em que uma cláusula `throw` é usada, qualquer análise do rastreamento de pilha ou exame de despejos de memória mostrará que a exceção foi lançada da instrução `throw` na cláusula catch. O objeto de exceção real conterá a pilha de chamadas original, mas todas as outras informações sobre as variáveis na pilha de chamadas, entre este ponto de lançamento e o local do ponto de lançamento original, foram perdidas. 

Compare isso com a maneira como o código que usa um filtro de exceção é processado: a expressão do filtro de exceção avalia como `false`. Portanto, execução nunca insere a cláusula `catch`. Como a cláusula `catch` não é executada, o desenrolamento de pilha não ocorre. Isso significa que o local de lançamento original é preservado para qualquer atividade de depuração que aconteceria mais tarde.

Sempre que você precisar avaliar campos ou propriedades de uma exceção, em vez de depender exclusivamente do tipo de exceção, use um filtro de exceção para preservar mais informações de depuração.

Outro padrão recomendado com filtros de exceção é usá-los para rotinas de registro em log. Esse uso também aproveita a maneira pela qual o ponto de lançamento de exceção é preservado quando um filtro de exceção é avaliado como `false`.

Um método de registro em log seria um método cujo argumento é a exceção que retorna incondicionalmente `false`:

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Sempre que você desejar registrar uma exceção, você pode adicionar uma cláusula catch e usar esse método como o filtro de exceção:

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

As exceções nunca são capturadas, porque o método `LogException` sempre retorna `false`. Esse filtro de exceção sempre falso significa que você pode colocar esse manipulador de log antes de qualquer outro manipulador de exceção:

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

O exemplo anterior destaca uma faceta muito importante dos filtros de exceção.
Os filtros de exceção permitem cenários em que uma cláusula de captura de exceção mais geral pode aparecer antes de uma mais específica. Também é possível ter o mesmo tipo de exceção aparecendo em várias cláusulas catch:

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Outro padrão recomendado ajuda a evitar que cláusulas catch processem exceções quando um depurador é anexado. Essa técnica permite que você execute um aplicativo com o depurador e interrompa a execução quando uma exceção é lançada.

No seu código, adicione um filtro de exceção para que qualquer código de recuperação seja executado somente quando um depurador não estiver anexado:

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Depois de adicionar isso no código, você deve definir o depurador para interromper em todas as exceções sem tratamento. Execute o programa no depurador e o depurador interromperá sempre que `PerformFailingOperation()` lançar uma `RecoverableException`.
O depurador interrompe o programa, porque a cláusula catch não será executada devido ao filtro de exceção que retorna false.

## <a name="nameof-expressions"></a>Expressões `nameof`

A expressão `nameof` é avaliada para o nome de um símbolo. É uma ótima maneira de fazer com que as ferramentas funcionem sempre que você precisar do nome de uma variável, de uma propriedade ou de um campo de membro.

Um dos usos mais comuns para `nameof` é fornecer o nome de um símbolo que causou uma exceção:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Outro uso é com aplicativos baseados em XAML que implementam a interface `INotifyPropertyChanged`:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

A vantagem de usar o operador `nameof` em uma cadeia de caracteres constante é que as ferramentas podem entender o símbolo. Se você usar ferramentas de refatoração para renomear o símbolo, elas vão renomeá-lo na expressão `nameof`. As cadeias de caracteres constantes não têm essa vantagem. Experimente você mesmo em seu editor favorito: renomeie uma variável e qualquer expressão `nameof` também atualizará.

A expressão `nameof` produz o nome não qualificado de seu argumento (`LastName` nos exemplos anteriores), mesmo que você use o nome totalmente qualificado para o argumento:

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

Essa expressão `nameof` produz `FirstName` e não `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>Await em blocos catch e finally

O C# 5 tinha várias limitações quanto ao local em que você poderia colocar expressões `await`.
Uma delas foi removida no C# 6. Agora você pode usar `await` em expressões `catch` ou `finally`. 

A adição de expressões await em blocos catch e finally pode parecer complicar a maneira como eles são processados. Vamos adicionar um exemplo para discutir como isso é exibido. Em qualquer método assíncrono, você pode usar uma expressão await em uma cláusula finally.

Com o C# 6, você também pode aguardar em expressões catch. Isso geralmente é usado com cenários de registro em log:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Os detalhes de implementação para adicionar suporte ao `await` dentro de cláusulas `catch` e `finally` garante que o comportamento é consistente com o comportamento de código síncrono. Quando o código que é executado em uma cláusula `catch` ou `finally` realiza o lançamento, a execução procura por uma cláusula `catch` adequada no próximo bloco. Se houver uma exceção atual, essa exceção será perdida. O mesmo acontece com expressões aguardadas em cláusulas `catch` e `finally`: um `catch` adequado é pesquisado e a exceção atual, se houver, será perdida.  

> [!NOTE]
> Esse comportamento é a razão pela qual recomenda-se escrever cláusulas `catch` e `finally` com cuidado, a fim de evitar introduzir novas exceções.

## <a name="index-initializers"></a>Inicializadores de índice

Os *inicializadores de índice* são um dos dois recursos que tornam os inicializadores de coleção mais consistentes. Em versões anteriores do C#, você podia usar *inicializadores de coleção* apenas com coleções de estilo de sequência:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

Agora, você também pode usá-los com coleções <xref:System.Collections.Generic.Dictionary%602> e tipos semelhantes:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Esse recurso significa que os contêineres associativos podem ser inicializados usando uma sintaxe semelhante à que está em vigor para contêineres de sequência de várias versões.

### <a name="extension-add-methods-in-collection-initializers"></a>Métodos `Add` de extensão em inicializadores de coleção

Outro recurso que facilita a inicialização de coleção é a capacidade de usar um *método de extensão* para o método `Add`. Esse recurso foi adicionado para a paridade com o Visual Basic. 

O recurso é mais útil quando você tem uma classe de coleção personalizada que tem um método com um nome diferente para adicionar novos itens semanticamente.

Por exemplo, considere uma coleção de alunos como esta:

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

O método `Enroll` adiciona um aluno. Mas não segue o padrão `Add`.
Nas versões anteriores do C#, você não podia usar os inicializadores de coleção com um objeto `Enrollment`:

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

Agora você pode, mas apenas se você criar um método de extensão que mapeia `Add` para `Enroll`:

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

O que você está fazendo com esse recurso é mapear qualquer método que adiciona itens a uma coleção, em um método chamado `Add`, criando um método de extensão: 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a>Resolução de sobrecarga aprimorada

Esse último recurso provavelmente não será notado. Havia constructos nos quais a versão anterior do compilador do C# pode ter encontrado algumas chamadas de método que envolviam expressões lambda ambíguas. Considere este método:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Em versões anteriores do C#, haveria uma falha ao chamar esse método usando a sintaxe de grupo de método:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
O compilador anterior não podia distinguir corretamente entre `Task.Run(Action)` e `Task.Run(Func<Task>())`. Nas versões anteriores, você precisava usar uma expressão lambda como um argumento:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

O compilador do C# 6 determina corretamente que `Task.Run(Func<Task>())` é uma opção melhor.
