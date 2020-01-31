---
title: Nomes de namespaces
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 52fee0dfaff284c2c1a6afcb8aa7530c28a60d65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744146"
---
# <a name="names-of-namespaces"></a>Nomes de namespaces
Assim como acontece com outras diretrizes de nomenclatura, a meta ao nomear namespaces é criar uma clareza suficiente para o programador usando a estrutura para saber imediatamente qual é a probabilidade do conteúdo do namespace. O modelo a seguir especifica a regra geral para nomes de namespaces:

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 Veja a seguir exemplos:

 `Fabrikam.Math` `Litware.Security`

 ✔️ os nomes de namespace de prefixo com um nome de empresa para impedir que os namespaces de diferentes empresas tenham o mesmo nome.

 ✔️ usar um nome de produto estável e independente de versão no segundo nível de um nome de namespace.

 ❌ não usam hierarquias organizacionais como base para nomes em hierarquias de namespace, pois os nomes de grupo nas empresas tendem a ser de curta duração. Organize a hierarquia de namespaces em relação a grupos de tecnologias relacionadas.

 ✔️ usar PascalCasing e separar componentes de namespace com pontos (por exemplo, `Microsoft.Office.PowerPoint`). Se sua marca emprega um uso não tradicional, você deve seguir a capitalização definida por sua marca, mesmo que ela se desvie da capitalização normal do namespace.

 ✔️ Considere o uso de nomes de namespace do plural quando apropriado.

 Por exemplo, use `System.Collections` em vez de `System.Collection`. No entanto, os nomes e acrônimos de marca são exceções a essa regra. Por exemplo, use `System.IO` em vez de `System.IOs`.

 ❌ não use o mesmo nome para um namespace e um tipo nesse namespace.

 Por exemplo, não use `Debug` como um nome de namespace e, em seguida, forneça uma classe chamada `Debug` no mesmo namespace. Vários compiladores exigem que esses tipos sejam totalmente qualificados.

### <a name="namespaces-and-type-name-conflicts"></a>Namespaces e conflitos de nome de tipo
 ❌ não apresentar nomes de tipo genérico, como `Element`, `Node`, `Log`e `Message`.

 Há uma probabilidade muito alta de fazer isso resultará em conflitos de nome de tipo em cenários comuns. Você deve qualificar os nomes de tipo genérico (`FormElement`, `XmlNode`, `EventLog``SoapMessage`).

 Há diretrizes específicas para evitar conflitos de nome de tipo para diferentes categorias de namespaces.

- **Namespaces de modelo de aplicativo**

     Os namespaces que pertencem a um único modelo de aplicativo geralmente são usados juntos, mas quase nunca são usados com namespaces de outros modelos de aplicativo. Por exemplo, o namespace <xref:System.Windows.Forms?displayProperty=nameWithType> é muito raramente usado junto com o namespace <xref:System.Web.UI?displayProperty=nameWithType>. Veja a seguir uma lista de grupos de namespace de modelo de aplicativo conhecidos:

     `System.Windows*` `System.Web.UI*`

     ❌ não fornecem o mesmo nome a tipos em namespaces em um único modelo de aplicativo.

     Por exemplo, não adicione um tipo chamado `Page` ao namespace <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, porque o namespace <xref:System.Web.UI?displayProperty=nameWithType> já contém um tipo chamado `Page`.

- **Namespaces de infraestrutura**

     Esse grupo contém namespaces que raramente são importados durante o desenvolvimento de aplicativos comuns. Por exemplo, os namespaces `.Design` são usados principalmente ao desenvolver ferramentas de programação. Evitar conflitos com tipos nesses namespaces não é crítico.

- **Principais namespaces**

     Os namespaces de núcleo incluem todos os namespaces `System`, excluindo namespaces dos modelos de aplicativo e os namespaces de infraestrutura. Os namespaces principais incluem, entre outros, `System`, `System.IO`, `System.Xml`e `System.Net`.

     ❌ não fornecem nomes de tipos que entram em conflito com qualquer tipo nos namespaces principais.

     Por exemplo, nunca use `Stream` como um nome de tipo. Ele estaria em conflito com <xref:System.IO.Stream?displayProperty=nameWithType>, um tipo muito usado.

- **Grupos de namespace de tecnologia**

     Essa categoria inclui todos os namespaces com os mesmos primeiros dois nós de namespace `(<Company>.<Technology>*`), como `Microsoft.Build.Utilities` e `Microsoft.Build.Tasks`. É importante que os tipos que pertencem a uma única tecnologia não entrem em conflito entre si.

     ❌ não atribua nomes de tipos que possam entrar em conflito com outros tipos em uma única tecnologia.

     ❌ não introduzem conflitos de nome de tipo entre tipos em namespaces de tecnologia e um namespace de modelo de aplicativo (a menos que a tecnologia não se destinar a ser usada com o modelo de aplicativo).

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
