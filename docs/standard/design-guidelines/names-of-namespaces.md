---
title: Nomes de Namespaces
ms.date: 03/30/2017
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e0b6c5ac60474cfe984b3802e880eb58b017722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576426"
---
# <a name="names-of-namespaces"></a>Nomes de Namespaces
Como com outras diretrizes de nomenclatura, a meta ao nomear namespaces está criando clareza suficiente para o programador usando a estrutura imediatamente saber o que é provavelmente o conteúdo do namespace. O modelo a seguir especifica a regra geral para nomear namespaces:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 A seguir estão exemplos:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** nomes de namespace com um nome de empresa para evitar namespaces de empresas diferentes tenham o mesmo nome do prefixo.  
  
 **✓ DO** usar um nome de produto estável, independente de versão no segundo nível de um nome de namespace.  
  
 **X DO NOT** usar hierarquias organizacionais como a base para nomes em hierarquias de namespace, como nomes de grupo em corporações tendem a ter vida curta. Organize a hierarquia de namespaces em torno de grupos de tecnologias relacionadas.  
  
 **✓ DO** usar PascalCasing e componentes do namespace separado com pontos (por exemplo, `Microsoft.Office.PowerPoint`). Se a marca emprega maiusculas e minúsculas não tradicional, você deve seguir o uso de maiusculas e minúsculas definido por sua marca, mesmo se ele tiver um desvio de maiusculas e minúsculas do namespace normal.  
  
 **✓ CONSIDER** usando nomes de namespace no plural quando apropriado.  
  
 Por exemplo, use `System.Collections` em vez de `System.Collection`. Nomes de marca e acrônimos são exceções a essa regra, no entanto. Por exemplo, use `System.IO` em vez de `System.IOs`.  
  
 **X DO NOT** usar o mesmo nome de um namespace e um tipo no namespace.  
  
 Por exemplo, não use `Debug` como um namespace do nome e, em seguida, também fornecem uma classe denominada `Debug` no mesmo namespace. Alguns compiladores exigem tipos totalmente qualificados.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Namespaces e conflitos de nome de tipo  
 **X DO NOT** apresentar nomes de tipo genérico como `Element`, `Node`, `Log`, e `Message`.  
  
 Há uma probabilidade muito alta que fazer isso levará para o nome de tipo está em conflito em comum cenários. Você deve qualificar os nomes de tipo genérico (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Há instruções específicas para evitar conflitos de nome de tipo para categorias diferentes de namespaces.  
  
-   **Namespaces do modelo de aplicativo**  
  
     Namespaces que pertencem a um modelo de aplicativo único com muita frequência, são usados juntos, mas quase nunca são usadas com namespaces de outros modelos de aplicativo. Por exemplo, o <xref:System.Windows.Forms?displayProperty=nameWithType> namespace muito raramente é usado junto com o <xref:System.Web.UI?displayProperty=nameWithType> namespace. A seguir está uma lista de grupos de namespace do modelo de aplicativo conhecidas:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** atribuir o mesmo nome para tipos em namespaces dentro de um modelo de aplicativo único.  
  
     Por exemplo, não adicione um tipo chamado `Page` para o <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, porque o <xref:System.Web.UI?displayProperty=nameWithType> namespace já contém um tipo chamado `Page`.  
  
-   **Namespaces de infraestrutura**  
  
     Esse grupo contém namespaces que raramente são importados durante o desenvolvimento de aplicativos comuns. Por exemplo, `.Design` namespaces são usados principalmente quando as ferramentas de desenvolvimento de programação. Evitando conflitos com os tipos nesses namespaces, não é crítico.  
  
-   **Namespaces de núcleo**  
  
     Namespaces básicos incluem todos os `System` namespaces, excluindo espaços para nome dos modelos de aplicativo e os namespaces de infraestrutura. Namespaces básicos incluem, entre outros, `System`, `System.IO`, `System.Xml`, e `System.Net`.  
  
     **X DO NOT** fornecem tipos de nomes que entraria em conflito com qualquer tipo nos namespaces Core.  
  
     Por exemplo, nunca use `Stream` como um nome de tipo. Ela entraria em conflito com <xref:System.IO.Stream?displayProperty=nameWithType>, um tipo muito usados.  
  
-   **Grupos de espaço para nome de tecnologia**  
  
     Essa categoria inclui todos os namespaces com os dois primeiros nós de namespace mesmo `(<Company>.<Technology>*`), como `Microsoft.Build.Utilities` e `Microsoft.Build.Tasks`. É importante que tipos que pertencem a uma única tecnologia não entrem em conflito entre si.  
  
     **X DO NOT** atribuir nomes de tipo que entraria em conflito com outros tipos em uma única tecnologia.  
  
     **X DO NOT** apresentam conflitos de nome de tipo entre os tipos nos namespaces de tecnologia e um namespace do modelo de aplicativo (a menos que a tecnologia não se destina a ser usado com o modelo de aplicativo).  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
