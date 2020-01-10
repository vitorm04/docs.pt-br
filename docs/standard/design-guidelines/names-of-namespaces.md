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
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709225"
---
# <a name="names-of-namespaces"></a>Nomes de namespaces
Assim como acontece com outras diretrizes de nomenclatura, a meta ao nomear namespaces é criar uma clareza suficiente para o programador usando a estrutura para saber imediatamente qual é a probabilidade do conteúdo do namespace. O modelo a seguir especifica a regra geral para nomes de namespaces:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Veja estes exemplos:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** nomes de namespace com um nome de empresa para evitar namespaces de empresas diferentes tenham o mesmo nome do prefixo.  
  
 **✓ DO** usar um nome de produto estável, independente de versão no segundo nível de um nome de namespace.  
  
 **X DO NOT** usar hierarquias organizacionais como a base para nomes em hierarquias de namespace, como nomes de grupo em corporações tendem a ter vida curta. Organize a hierarquia de namespaces em relação a grupos de tecnologias relacionadas.  
  
 **✓ DO** usar PascalCasing e componentes do namespace separado com pontos (por exemplo, `Microsoft.Office.PowerPoint`). Se sua marca emprega um uso não tradicional, você deve seguir a capitalização definida por sua marca, mesmo que ela se desvie da capitalização normal do namespace.  
  
 **✓ CONSIDER** usando nomes de namespace no plural quando apropriado.  
  
 Por exemplo, use `System.Collections` em vez de `System.Collection`. No entanto, os nomes e acrônimos de marca são exceções a essa regra. Por exemplo, use `System.IO` em vez de `System.IOs`.  
  
 **X DO NOT** usar o mesmo nome de um namespace e um tipo no namespace.  
  
 Por exemplo, não use `Debug` como um nome de namespace e, em seguida, forneça uma classe chamada `Debug` no mesmo namespace. Vários compiladores exigem que esses tipos sejam totalmente qualificados.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Namespaces e conflitos de nome de tipo  
 **X DO NOT** apresentar nomes de tipo genérico como `Element`, `Node`, `Log`, e `Message`.  
  
 Há uma probabilidade muito alta de fazer isso resultará em conflitos de nome de tipo em cenários comuns. Você deve qualificar os nomes de tipo genérico (`FormElement`, `XmlNode`, `EventLog``SoapMessage`).  
  
 Há diretrizes específicas para evitar conflitos de nome de tipo para diferentes categorias de namespaces.  
  
- **Namespaces de modelo de aplicativo**  
  
     Os namespaces que pertencem a um único modelo de aplicativo geralmente são usados juntos, mas quase nunca são usados com namespaces de outros modelos de aplicativo. Por exemplo, o namespace <xref:System.Windows.Forms?displayProperty=nameWithType> é muito raramente usado junto com o namespace <xref:System.Web.UI?displayProperty=nameWithType>. Veja a seguir uma lista de grupos de namespace de modelo de aplicativo conhecidos:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** atribuir o mesmo nome para tipos em namespaces dentro de um modelo de aplicativo único.  
  
     Por exemplo, não adicione um tipo chamado `Page` ao namespace <xref:System.Web.UI.Adapters?displayProperty=nameWithType>, porque o namespace <xref:System.Web.UI?displayProperty=nameWithType> já contém um tipo chamado `Page`.  
  
- **Namespaces de infraestrutura**  
  
     Esse grupo contém namespaces que raramente são importados durante o desenvolvimento de aplicativos comuns. Por exemplo, os namespaces `.Design` são usados principalmente ao desenvolver ferramentas de programação. Evitar conflitos com tipos nesses namespaces não é crítico.  
  
- **Principais namespaces**  
  
     Os namespaces de núcleo incluem todos os namespaces `System`, excluindo namespaces dos modelos de aplicativo e os namespaces de infraestrutura. Os namespaces principais incluem, entre outros, `System`, `System.IO`, `System.Xml`e `System.Net`.  
  
     **X DO NOT** fornecem tipos de nomes que entraria em conflito com qualquer tipo nos namespaces Core.  
  
     Por exemplo, nunca use `Stream` como um nome de tipo. Ele estaria em conflito com <xref:System.IO.Stream?displayProperty=nameWithType>, um tipo muito usado.  
  
- **Grupos de namespace de tecnologia**  
  
     Essa categoria inclui todos os namespaces com os mesmos primeiros dois nós de namespace `(<Company>.<Technology>*`), como `Microsoft.Build.Utilities` e `Microsoft.Build.Tasks`. É importante que os tipos que pertencem a uma única tecnologia não entrem em conflito entre si.  
  
     **X DO NOT** atribuir nomes de tipo que entraria em conflito com outros tipos em uma única tecnologia.  
  
     **X DO NOT** apresentam conflitos de nome de tipo entre os tipos nos namespaces de tecnologia e um namespace do modelo de aplicativo (a menos que a tecnologia não se destina a ser usado com o modelo de aplicativo).  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
