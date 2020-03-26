---
title: Métodos de extensão – Guia de Programação em C#
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 0b35ad523fc7f0949cb5243edbdc50cd3e927999
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249214"
---
# <a name="extension-methods-c-programming-guide"></a>Métodos de extensão (Guia de Programação em C#)

Os métodos de extensão permitem que você "adicione" tipos existentes sem criar um novo tipo derivado, recompilar ou, caso contrário, modificar o tipo original. Os métodos de extensão são métodos estáticos, mas são chamados como se fossem métodos de ocorrência no tipo estendido. Para o código do cliente escrito em C#, F# e Visual Basic, não há diferença aparente entre chamar um método de extensão e os métodos definidos em um tipo.

Os métodos de extensão mais comuns são os operadores de consulta <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> padrão LINQ que adicionam funcionalidade de consulta aos tipos e tipos existentes. Para usar os operadores de consulta padrão, traga-os primeiro ao escopo com uma diretiva `using System.Linq`. Em seguida, qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601> parece ter métodos de instância como <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A> e assim por diante. Você pode exibir esses métodos adicionais no preenchimento de declaração do IntelliSense ao digitar "ponto" após uma instância de um tipo <xref:System.Collections.Generic.IEnumerable%601> como <xref:System.Collections.Generic.List%601> ou <xref:System.Array>.

### <a name="orderby-example"></a>Exemplo de ordem

O exemplo a seguir mostra como chamar o método de consulta padrão `OrderBy` em qualquer matriz de inteiros. A expressão entre parênteses é uma expressão lambda. Muitos operadores de consulta padrão tomam expressões lambda como parâmetros, mas isso não é um requisito para métodos de extensão. Para obter mais informações, consulte [Expressões Lambda](../statements-expressions-operators/lambda-expressions.md).

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

Os métodos de extensão são definidos como estáticos, mas são chamados usando a sintaxe do método de instância. Seu primeiro parâmetro especifica em qual tipo o método opera. O parâmetro é precedido [this](../../language-reference/keywords/this.md) pelo modificador. Os métodos de extensão só estarão no escopo quando você importar explicitamente o namespace para seu código-fonte com uma diretiva `using`.

O exemplo a seguir mostra um método de extensão definido para a classe <xref:System.String?displayProperty=nameWithType>. É definido dentro de uma classe estática não aninhada e não genérica:

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

O método de extensão `WordCount` pode ser colocado no escopo com esta diretiva `using`:

```csharp
using ExtensionMethods;
```

E pode ser chamado a partir de um aplicativo usando esta sintaxe:

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

Você invoca o método de extensão em seu código com sintaxe de método de instância. A linguagem intermediária (IL) gerada pelo compilador traduz seu código em uma chamada no método estático. O princípio do encapsulamento não está sendo violado. Os métodos de extensão não podem acessar variáveis privadas no tipo que estão estendendo.

Para obter mais informações, consulte [Como implementar e chamar um método de extensão personalizado](./how-to-implement-and-call-a-custom-extension-method.md).

Em geral, você provavelmente estará chamando métodos de extensão muito mais frequentemente do que implementando o seu próprio. Como os métodos de extensão são chamados com a sintaxe do método de instância, nenhum conhecimento especial é necessário para usá-los no código do cliente. Para habilitar métodos de extensão para um tipo específico, apenas adicione uma diretiva `using` para o namespace no qual os métodos estão definidos. Por exemplo, para usar os operadores de consulta padrão, adicione esta diretiva `using` ao seu código:

```csharp
using System.Linq;
```

(Você também pode ter que adicionar uma referência ao System.Core.dll.) Você notará que os operadores de consulta padrão agora aparecem no IntelliSense como métodos adicionais disponíveis para a maioria dos <xref:System.Collections.Generic.IEnumerable%601> tipos.

## <a name="binding-extension-methods-at-compile-time"></a>Associando Métodos de Extensão no Momento da Compilação

Você pode usar métodos de extensão para estender uma classe ou interface, mas não os substituir. Um método de extensão com o mesmo nome e assinatura que um método de interface ou classe nunca será chamado. No tempo de compilação, os métodos de extensão sempre têm menos prioridade que os métodos de instância definidos no próprio tipo. Em outras palavras, se um tipo possuir um método chamado `Process(int i)` e se você tiver um método de extensão com a mesma assinatura, o compilador sempre se associará ao método de instância. Quando o compilador encontra uma invocação de método, primeiro ele procura uma correspondência nos métodos de instância do tipo. Se nenhuma correspondência for encontrada, ele irá procurar todos os métodos de extensão definidos para o tipo e associará o primeiro método de extensão que encontrar. O exemplo a seguir demonstra como o compilador determina a qual método de extensão ou método de instância associar.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra as regras que o compilador C# segue ao determinar se deve associar uma chamada de método a um método de instância no tipo ou a um método de extensão. A classe estática `Extensions` contém métodos de extensão definidos para qualquer tipo que implementa `IMyInterface`. As classes `A`, `B` e `C` implementam a interface.

O método de extensão `MethodB` nunca é chamado porque seu nome e assinatura são exatamente iguais aos métodos já implementados pelas classes.

Quando o compilador não consegue encontrar um método de ocorrência com uma assinatura correspondente, ele se ligará a um método de extensão correspondente se existir.

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>Padrões de uso comuns

### <a name="collection-functionality"></a>Funcionalidade de coleção

No passado, era comum criar "Classes de <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Coleção" que implementassem a interface para um determinado tipo e contivessem funcionalidades que atuavam em coleções desse tipo. Embora não haja nada de errado em criar esse tipo de objeto de coleta, a mesma funcionalidade pode ser alcançada usando uma extensão no <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. As extensões têm a vantagem de permitir que a <xref:System.Array?displayProperty=nameWithType> funcionalidade <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> seja <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> chamada de qualquer coleção, como uma ou que implementa nesse tipo. Um exemplo disso usando uma Matriz de Int32 pode ser encontrado [anteriormente neste artigo](#orderby-example).

### <a name="layer-specific-functionality"></a>Funcionalidade específica da camada

Ao usar uma arquitetura onion ou outro design de aplicativo em camadas, é comum ter um conjunto de Entidades de Domínio ou Objetos de Transferência de Dados que podem ser usados para se comunicar através dos limites do aplicativo. Esses objetos geralmente não contêm funcionalidade, ou apenas funcionalidade mínima que se aplica a todas as camadas do aplicativo. Os métodos de extensão podem ser usados para adicionar funcionalidade específica a cada camada de aplicativo sem carregar o objeto para baixo com métodos não necessários ou desejados em outras camadas.

```aspx-csharp
public class DomainEntity
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

static class DomainEntityExtensions
{
    static string FullName(this DomainEntity value)
        => $"{value.FirstName} {value.LastName}";
}
```

### <a name="extending-predefined-types"></a>Estendendo tipos predefinidos

Em vez de criar novos objetos quando a funcionalidade reutilizável precisa ser criada, muitas vezes podemos estender um tipo existente, como um tipo .NET Framework ou CLR. Como exemplo, se não usarmos métodos de extensão, podemos criar uma `Engine` ou `Query` classe para fazer o trabalho de executar uma consulta em um Servidor SQL que pode ser chamado de vários lugares em nosso código. No entanto, <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> podemos, em vez disso, estender a classe usando métodos de extensão para executar essa consulta de qualquer lugar que tenhamos uma conexão com um Servidor SQL. Outros exemplos podem ser adicionar funcionalidade <xref:System.String?displayProperty=nameWithType> comum à classe, estender os <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Stream?displayProperty=nameWithType> recursos de <xref:System.Exception?displayProperty=nameWithType> processamento de dados dos objetos e objetos para a funcionalidade específica de manipulação de erros. Esses tipos de casos de uso são limitados apenas pela sua imaginação e bom senso.

Estender tipos predefinidos pode `struct` ser difícil com os tipos porque eles são passados por valor para métodos. Isso significa que qualquer alteração na estrutura é feita para uma cópia da estrutura. Essas alterações não são visíveis quando o método de extensão sai. Começando com C# 7.2, `ref` você pode adicionar o modificador ao primeiro argumento de um método de extensão. Adicionar `ref` o modificador significa que o primeiro argumento é aprovado por referência. Isso permite que você escreva métodos de extensão que alteram o estado da estrutura sendo estendida.

## <a name="general-guidelines"></a>Diretrizes gerais

Embora ainda seja considerado preferível adicionar funcionalidade modificando o código de um objeto ou derivando um novo tipo sempre que for razoável e possível, os métodos de extensão tornaram-se uma opção crucial para criar funcionalidades reutilizáveis em todo o .NET Ecossistema. Para aquelas ocasiões em que a fonte original não está seu controle, quando um objeto derivado é inapropriado ou impossível, ou quando a funcionalidade não deve ser exposta além de seu escopo aplicável, os métodos de extensão são uma excelente escolha.

Para obter mais informações sobre os tipos derivados, consulte [Herança](./inheritance.md).

Ao usar um método de extensão para estender um tipo cujo código-fonte você não está no controle, você corre o risco de que uma alteração na implementação do tipo faça com que seu método de extensão se quebre.

Se você implementar métodos de extensão para um determinado tipo, lembre-se das seguintes considerações:

- Um método de extensão nunca será chamado se possuir a mesma assinatura que um método definido no tipo.
- Os métodos de extensão são trazidos para o escopo no nível do namespace. Por exemplo, se você tiver várias classes estáticas `Extensions`que contenham métodos de extensão em um único namespace chamado, todos eles serão colocados em escopo pela `using Extensions;` diretiva.

Para uma biblioteca de classes que você implemente, não use métodos de extensão para evitar incrementar o número de versão de um assembly. Se desejar adicionar funcionalidade significativa a uma biblioteca da qual você possua o código-fonte, siga as diretrizes padrão do .NET Framework para controle de versão do assembly. Para obter mais informações, consulte [Controle de versão do assembly](../../../standard/assembly/versioning.md).

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Exemplos de programação paralela (incluem vários métodos de extensão de exemplo)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Expressões Lambda](../statements-expressions-operators/lambda-expressions.md)
- [Visão geral dos operadores de consulta padrão](../concepts/linq/standard-query-operators-overview.md)
- [Regras de conversão para parâmetros de instância e seu impacto](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact)
- [Interoperabilidade de métodos de extensão entre linguagens](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages)
- [Métodos de extensão e representantes via currying](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates)
- [Associação do método de extensão e relatório de erros](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting)
