---
title: Métodos de extensão
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bfc2e6def94d0830df4a4cdf738cdeef106de9f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539155"
---
# <a name="extension-methods"></a>Métodos de extensão
Métodos de extensão são um recurso de linguagem que permite que os métodos estáticos a ser chamado usando a sintaxe de chamada de método de instância. Esses métodos devem ter pelo menos um parâmetro, que representa a instância que o método é no qual operar.  
  
 A classe que define esses métodos de extensão é conhecida como a classe "Patrocinador" e deve ser declarado como estático. Para usar os métodos de extensão, uma deve importar o namespace de definição da classe de patrocinador.  
  
 **X AVOID** frivolously definir métodos de extensão, especialmente em tipos que você não possui.  
  
 Se você é proprietário de um tipo de código-fonte, considere o uso de métodos de instância normal. Se você não possui, e você deseja adicionar um método, tenha muito cuidado. Utilização liberal dos métodos de extensão tem o potencial de desorganizar APIs de tipos que não foram projetados para ter esses métodos.  
  
 **✓ CONSIDER** usando métodos de extensão em qualquer um dos seguintes cenários:  
  
-   Para fornecer auxiliar funcionalidade relevante para cada implementação de uma interface, disse que a funcionalidade pode ser escrita em termos de interface principal. Isso ocorre porque as implementações concretas, caso contrário, não podem ser atribuídas às interfaces. Por exemplo, o `LINQ to Objects` operadores são implementados como métodos de extensão para todos os <xref:System.Collections.Generic.IEnumerable%601> tipos. Portanto, qualquer `IEnumerable<>` implementação é automaticamente habilitado para LINQ.  
  
-   Quando um método de instância introduziria uma dependência em algum tipo, mas tal dependência interrompe as regras de gerenciamento de dependência. Por exemplo, uma dependência de <xref:System.String> à <xref:System.Uri?displayProperty=nameWithType> provavelmente não é desejável e, portanto `String.ToUri()` retornando do método de instância `System.Uri` seria um design incorreto de uma perspectiva de gerenciamento de dependência. Um método de extensão estático `Uri.ToUri(this string str)` retornando `System.Uri` seria um design muito melhor.  
  
 **X AVOID** definir métodos de extensão em <xref:System.Object?displayProperty=nameWithType>.  
  
 Os usuários do VB não poderá chamar esses métodos em referências de objeto usando a sintaxe de método de extensão. VB não suporta chamar esses métodos porque, no VB, declarar uma referência de objeto força todas as invocações de método em que ele seja atrasado associado (chamado de membro real é determinado em tempo de execução), enquanto as associações para métodos de extensão são determinadas em tempo de compilação (no início associado).  
  
 Observe que a diretriz se aplica a outros idiomas em que o mesmo comportamento de associação está presente, ou onde não há suporte para métodos de extensão.  
  
 **X DO NOT** colocar os métodos de extensão no mesmo namespace que o tipo estendido, a menos que ele seja para a adição de métodos para interfaces de ou para o gerenciamento de dependência.  
  
 **X AVOID** definir dois ou mais métodos de extensão com a mesma assinatura, mesmo que eles estejam em namespaces diferentes.  
  
 **✓ CONSIDER** definir métodos de extensão no mesmo namespace que o tipo estendido se o tipo é uma interface e se os métodos de extensão devem ser usados na maioria dos casos.  
  
 **X DO NOT** definir métodos de extensão implementando um recurso nos namespaces normalmente associados com outros recursos. Em vez disso, defini-los no namespace associado com o recurso pertencem.  
  
 **X AVOID** genérico de nomenclatura de namespaces dedicado para métodos de extensão (por exemplo, "extensões"). Use um nome descritivo (por exemplo, "roteamento") em vez disso.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design de membro](../../../docs/standard/design-guidelines/member.md)  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
