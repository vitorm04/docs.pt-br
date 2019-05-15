---
title: Métodos de extensão – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: a686716c4e8ed24c9b28426542cdf6bc6aa991b7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600231"
---
# <a name="extension-methods-c-programming-guide"></a>Métodos de extensão (Guia de Programação em C#)
Os métodos de extensão permitem que você "adicione" tipos existentes sem criar um novo tipo derivado, recompilar ou, caso contrário, modificar o tipo original. Os métodos de extensão são um tipo especial de método estático, mas são chamados como se fossem métodos de instância no tipo estendido. No caso do código cliente gravado em C#, F# e Visual Basic, não há nenhuma diferença aparente entre chamar um método de extensão e os métodos realmente definidos em um tipo.  
  
 Os métodos de extensão mais comuns são os operadores de consulta padrão [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] que adicionam funcionalidade de consulta aos tipos <xref:System.Collections.IEnumerable?displayProperty=nameWithType> e <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> existentes. Para usar os operadores de consulta padrão, traga-os primeiro ao escopo com uma diretiva `using System.Linq`. Em seguida, qualquer tipo que implemente <xref:System.Collections.Generic.IEnumerable%601> parece ter métodos de instância como <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A> e assim por diante. Você pode exibir esses métodos adicionais no preenchimento de declaração do IntelliSense ao digitar "ponto" após uma instância de um tipo <xref:System.Collections.Generic.IEnumerable%601> como <xref:System.Collections.Generic.List%601> ou <xref:System.Array>.  
  
 O exemplo a seguir mostra como chamar o método de consulta padrão `OrderBy` em qualquer matriz de inteiros. A expressão entre parênteses é uma expressão lambda. Vários operadores de consulta padrão obtêm expressões lambda como parâmetros, mas isso não é um requisito para métodos de extensão. Para obter mais informações, consulte [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 [!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]  
  
 Os métodos de extensão são definidos como estáticos, mas são chamados usando a sintaxe do método de instância. Seu primeiro parâmetro especifica em que tipo o método opera e o parâmetro é precedido pelo modificador [this](../../../csharp/language-reference/keywords/this.md). Os métodos de extensão só estarão no escopo quando você importar explicitamente o namespace para seu código-fonte com uma diretiva `using`.  
  
 O exemplo a seguir mostra um método de extensão definido para a classe <xref:System.String?displayProperty=nameWithType>. Observe que isso é definido em uma classe estática não aninhada e não genérica:  
  
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
  
 Em seu código, você chama o método de extensão com sintaxe de método de instância. No entanto, a linguagem intermediária (IL) gerada pelo compilador converte seu código em uma chamada no método estático. Portanto, o princípio de encapsulamento ainda não está realmente sendo violado. De fato, os métodos de extensão não podem acessar variáveis particulares no tipo que estão estendendo.  
  
 Para obter mais informações, confira [Como: implementar e chamar um método de extensão personalizado](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).  
  
 Em geral, provavelmente você chamará métodos de extensão com muito mais frequência do que implementará os seus próprios. Como os métodos de extensão são chamados com a sintaxe do método de instância, nenhum conhecimento especial é necessário para usá-los no código do cliente. Para habilitar métodos de extensão para um tipo específico, apenas adicione uma diretiva `using` para o namespace no qual os métodos estão definidos. Por exemplo, para usar os operadores de consulta padrão, adicione esta diretiva `using` ao seu código:  
  
```csharp  
using System.Linq;  
```  
  
 (Também pode ser necessário adicionar uma referência a System.Core.dll.) Você observará que os operadores de consulta padrão agora são exibidos no IntelliSense como métodos adicionais disponíveis para a maioria dos tipos <xref:System.Collections.Generic.IEnumerable%601>.  
  
## <a name="binding-extension-methods-at-compile-time"></a>Associando Métodos de Extensão no Momento da Compilação  
 Você pode usar métodos de extensão para estender uma classe ou interface, mas não os substituir. Um método de extensão com o mesmo nome e assinatura que um método de interface ou classe nunca será chamado. No tempo de compilação, os métodos de extensão sempre têm menos prioridade que os métodos de instância definidos no próprio tipo. Em outras palavras, se um tipo possuir um método chamado `Process(int i)` e se você tiver um método de extensão com a mesma assinatura, o compilador sempre se associará ao método de instância. Quando o compilador encontra uma invocação de método, primeiro ele procura uma correspondência nos métodos de instância do tipo. Se nenhuma correspondência for encontrada, ele irá procurar todos os métodos de extensão definidos para o tipo e associará o primeiro método de extensão que encontrar. O exemplo a seguir demonstra como o compilador determina a qual método de extensão ou método de instância associar.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra as regras que o compilador C# segue ao determinar se deve associar uma chamada de método a um método de instância no tipo ou a um método de extensão. A classe estática `Extensions` contém métodos de extensão definidos para qualquer tipo que implementa `IMyInterface`. As classes `A`, `B` e `C` implementam a interface.  
  
 O método de extensão `MethodB` nunca é chamado porque seu nome e assinatura são exatamente iguais aos métodos já implementados pelas classes.  
  
 Quando o compilador não consegue localizar um método de instância com uma assinatura compatível, ele se associa a um método de extensão correspondente se houver.  
  
 [!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]  
  
## <a name="general-guidelines"></a>Diretrizes gerais  
 Em geral, recomendamos que você implemente métodos de extensão com parcimônia e somente quando for necessário. Sempre que possível, o código do cliente que deve estender um tipo existente deve fazer isso ao criar um novo tipo derivado do tipo existente. Para obter mais informações, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Ao usar um método de extensão para estender um tipo cujo código-fonte você não pode alterar, há o risco de uma alteração na implementação do tipo fazer com que o método de extensão interrompa.  
  
 Se você implementar métodos de extensão para um determinado tipo, lembre-se das seguintes considerações:  
  
- Um método de extensão nunca será chamado se possuir a mesma assinatura que um método definido no tipo.  
  
- Os métodos de extensão são trazidos para o escopo no nível do namespace. Por exemplo, se você tiver várias classes estáticas que contenham métodos de extensão em um único namespace chamado `Extensions`, todos eles serão trazidos para o escopo pela diretiva `using Extensions;`.  
  
 Para uma biblioteca de classes que você implemente, não use métodos de extensão para evitar incrementar o número de versão de um assembly. Se desejar adicionar funcionalidade significativa a uma biblioteca da qual você possua o código-fonte, siga as diretrizes padrão do .NET Framework para controle de versão do assembly. Para obter mais informações, consulte [Controle de versão do assembly](../../../../docs/framework/app-domains/assembly-versioning.md).  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Exemplos de programação paralela (incluem vários métodos de extensão de exemplo)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [Expressões Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Visão Geral de Operadores de Consulta Padrão](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Regras de conversão para parâmetros de instância e seu impacto](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/conversion-rules-for-instance-parameters-and-their-impact)
- [Interoperabilidade de métodos de extensão entre linguagens](https://blogs.msdn.microsoft.com/sreekarc/2007/10/11/extension-methods-interoperability-between-languages)
- [Métodos de extensão e representantes via currying](https://blogs.msdn.microsoft.com/sreekarc/2007/05/01/extension-methods-and-curried-delegates)
- [Associação do método de extensão e relatório de erros](https://blogs.msdn.microsoft.com/sreekarc/2007/04/26/extension-method-binding-and-error-reporting)
