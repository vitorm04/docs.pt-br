---
title: Métodos de Extensão
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 13f92470b23d138e0d30bed947ff1932f2605d28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741614"
---
# <a name="extension-methods"></a>Métodos de Extensão
Os métodos de extensão são um recurso de linguagem que permite que métodos estáticos sejam chamados usando a sintaxe de chamada de método de instância. Esses métodos devem ter pelo menos um parâmetro, que representa a instância em que o método deve operar.

 A classe que define esses métodos de extensão é conhecida como a classe "patrocinador" e deve ser declarada como estática. Para usar métodos de extensão, é necessário importar o namespace que define a classe patrocinador.

 ❌ Evite definir frivolously métodos de extensão, especialmente em tipos que não são de sua propriedade.

 Se você tiver o código-fonte próprio de um tipo, considere o uso de métodos de instância regular. Se você não for o proprietário e quiser adicionar um método, tenha muito cuidado. O uso liberal de métodos de extensão tem o potencial de desobstruir APIs de tipos que não foram projetados para ter esses métodos.

 ✔️ Considere o uso de métodos de extensão em qualquer um dos seguintes cenários:

- Para fornecer a funcionalidade auxiliar relevante para cada implementação de uma interface, se dito, a funcionalidade pode ser escrita em termos da interface principal. Isso ocorre porque as implementações concretas não podem ser atribuídas de outra forma a interfaces. Por exemplo, os operadores de `LINQ to Objects` são implementados como métodos de extensão para todos os tipos de <xref:System.Collections.Generic.IEnumerable%601>. Assim, qualquer implementação de `IEnumerable<>` é habilitada automaticamente por LINQ.

- Quando um método de instância introduzir uma dependência em algum tipo, mas essa dependência quebraria as regras de gerenciamento de dependência. Por exemplo, uma dependência de <xref:System.String> para <xref:System.Uri?displayProperty=nameWithType> provavelmente não é desejável e, portanto, `String.ToUri()` método de instância que retorna `System.Uri` seria o design errado de uma perspectiva de gerenciamento de dependência. Um método de extensão estático `Uri.ToUri(this string str)` retornar `System.Uri` seria um design muito melhor.

 ❌ evitar definir métodos de extensão em <xref:System.Object?displayProperty=nameWithType>.

 Visual Basic usuários não poderão chamar esses métodos em referências de objeto usando a sintaxe do método de extensão. Visual Basic não dá suporte à chamada de tais métodos porque, em Visual Basic, declarar uma referência como Object força todas as invocações de método nele para serem associadas tardias (o membro real chamado é determinado em tempo de execução), enquanto as associações aos métodos de extensão são determinadas em tempo de compilação (Associação antecipada).

 Observe que a diretriz se aplica a outros idiomas em que o mesmo comportamento de ligação está presente, ou onde os métodos de extensão não têm suporte.

 ❌ não coloque os métodos de extensão no mesmo namespace que o tipo estendido, a menos que seja para adicionar métodos a interfaces ou para o gerenciamento de dependências.

 ❌ evitar definir dois ou mais métodos de extensão com a mesma assinatura, mesmo que eles residam em namespaces diferentes.

 ✔️ Considere definir métodos de extensão no mesmo namespace que o tipo estendido se o tipo é uma interface e se os métodos de extensão devem ser usados na maioria ou em todos os casos.

 ❌ não definir métodos de extensão que implementam um recurso em namespaces normalmente associados a outros recursos. Em vez disso, defina-os no namespace associado ao recurso ao qual eles pertencem.

 ❌ evitar a nomenclatura genérica de namespaces dedicados aos métodos de extensão (por exemplo, "extensões"). Em vez disso, use um nome descritivo (por exemplo, "roteamento").

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
