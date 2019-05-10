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
author: KrzysztofCwalina
ms.openlocfilehash: b8b6ec195fd3f95a4255ea820f2bffcb3e27ba19
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615215"
---
# <a name="names-of-namespaces"></a>Nomes de namespaces
Como com outras diretrizes de nomenclatura, a meta ao nomear namespaces é criando clareza suficiente para o programador usando a estrutura de saber imediatamente qual o conteúdo do namespace é provavelmente será. O modelo a seguir especifica a regra geral para a nomeação de namespaces:  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 A seguir estão exemplos:  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** nomes de namespace com um nome de empresa para evitar namespaces de empresas diferentes tenham o mesmo nome do prefixo.  
  
 **✓ DO** usar um nome de produto estável, independente de versão no segundo nível de um nome de namespace.  
  
 **X DO NOT** usar hierarquias organizacionais como a base para nomes em hierarquias de namespace, como nomes de grupo em corporações tendem a ter vida curta. Organize a hierarquia de namespaces em torno de grupos de tecnologias relacionadas.  
  
 **✓ DO** usar PascalCasing e componentes do namespace separado com pontos (por exemplo, `Microsoft.Office.PowerPoint`). Se a sua marca emprega maiusculas e minúsculas não tradicional, você deve seguir as maiusculas e minúsculas definida pela sua marca, mesmo se ele tiver um desvio do uso de maiusculas e minúsculas do namespace normal.  
  
 **✓ CONSIDER** usando nomes de namespace no plural quando apropriado.  
  
 Por exemplo, use `System.Collections` em vez de `System.Collection`. Nomes de marca e acrônimos são exceções a essa regra, no entanto. Por exemplo, use `System.IO` em vez de `System.IOs`.  
  
 **X DO NOT** usar o mesmo nome de um namespace e um tipo no namespace.  
  
 Por exemplo, não use `Debug` como um namespace Nomeie e, em seguida, forneça também uma classe chamada `Debug` no mesmo namespace. Os diversos compiladores exigem tais tipos totalmente qualificados.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Namespaces e conflitos de nome de tipo  
 **X DO NOT** apresentar nomes de tipo genérico como `Element`, `Node`, `Log`, e `Message`.  
  
 Há uma probabilidade muito alta que fazer isso levará para o nome de tipo está em conflito em comum cenários. Você deve qualificar os nomes de tipo genérico (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Há diretrizes específicas para evitar conflitos de nome de tipo para categorias diferentes de namespaces.  
  
- **Namespaces de modelos de aplicativo**  
  
     Os namespaces que pertencem a um modelo de aplicativo único muito geralmente são usados juntos, mas quase nunca são usadas com namespaces de outros modelos de aplicativo. Por exemplo, o <xref:System.Windows.Forms?displayProperty=nameWithType> namespace muito raramente é usado junto com o <xref:System.Web.UI?displayProperty=nameWithType> namespace. A seguir está uma lista de grupos de namespace do modelo de aplicativo bem conhecido:  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** atribuir o mesmo nome para tipos em namespaces dentro de um modelo de aplicativo único.  
  
     Por exemplo, não adicione um tipo chamado `Page` para o <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, porque o <xref:System.Web.UI?displayProperty=nameWithType> namespace já contém um tipo chamado `Page`.  
  
- **Namespaces de infraestrutura**  
  
     Esse grupo contém os namespaces que raramente são importados durante o desenvolvimento de aplicativos comuns. Por exemplo, `.Design` namespaces são usados principalmente das ferramentas de desenvolvimento de programação. Evitando conflitos com os tipos nesses namespaces não é crítica.  
  
- **Namespaces básicos**  
  
     Namespaces básicos incluem todas `System` namespaces, exceto os namespaces dos modelos de aplicativo e os namespaces de infraestrutura. Namespaces básicos incluem, entre outros, `System`, `System.IO`, `System.Xml`, e `System.Net`.  
  
     **X DO NOT** fornecem tipos de nomes que entraria em conflito com qualquer tipo nos namespaces Core.  
  
     Por exemplo, nunca use `Stream` como um nome de tipo. Ela entraria em conflito com <xref:System.IO.Stream?displayProperty=nameWithType>, um tipo muito usados.  
  
- **Grupos de namespace de tecnologia**  
  
     Essa categoria inclui todos os namespaces com os dois primeiros nós de namespace mesmo `(<Company>.<Technology>*`), como `Microsoft.Build.Utilities` e `Microsoft.Build.Tasks`. É importante que os tipos que pertencem a uma única tecnologia não entrem em conflito umas com as outras.  
  
     **X DO NOT** atribuir nomes de tipo que entraria em conflito com outros tipos em uma única tecnologia.  
  
     **X DO NOT** apresentam conflitos de nome de tipo entre os tipos nos namespaces de tecnologia e um namespace do modelo de aplicativo (a menos que a tecnologia não se destina a ser usado com o modelo de aplicativo).  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de nomenclatura](../../../docs/standard/design-guidelines/naming-guidelines.md)
