---
title: '{1&gt;{2&gt;Atributos&lt;2}&lt;1}'
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: ff38cfdc228fd1eae1ace734ed2688c62c66499a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709550"
---
# <a name="attributes"></a>{1&gt;{2&gt;Atributos&lt;2}&lt;1}
<xref:System.Attribute?displayProperty=nameWithType> é uma classe base usada para definir atributos personalizados.  
  
 Atributos são anotações que podem ser adicionadas a elementos de programação, como assemblies, tipos, membros e parâmetros. Eles são armazenados nos metadados do assembly e podem ser acessados em tempo de execução usando as APIs de reflexão. Por exemplo, a estrutura define o <xref:System.ObsoleteAttribute>, que pode ser aplicado a um tipo ou um membro para indicar que o tipo ou o membro foi preterido.  
  
 Os atributos podem ter uma ou mais propriedades que contêm dados adicionais relacionados ao atributo. Por exemplo, `ObsoleteAttribute` poderia conter informações adicionais sobre a versão na qual um tipo ou um membro foi preterido e a descrição das novas APIs que substituem a API obsoleta.  
  
 Algumas propriedades de um atributo devem ser especificadas quando o atributo é aplicado. Eles são chamados de propriedades obrigatórias ou argumentos necessários, pois são representados como parâmetros de Construtor posicionais. Por exemplo, a propriedade <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> da <xref:System.Diagnostics.ConditionalAttribute> é uma propriedade necessária.  
  
 As propriedades que não precisam necessariamente ser especificadas quando o atributo é aplicado são chamadas de propriedades opcionais (ou argumentos opcionais). Elas são representadas por propriedades de tabela. Os compiladores fornecem uma sintaxe especial para definir essas propriedades quando um atributo é aplicado. Por exemplo, a propriedade <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> representa um argumento opcional.  
  
 **✓ DO** nome classes de atributos personalizados com o sufixo "Atributo".  
  
 **✓ DO** se aplicam a <xref:System.AttributeUsageAttribute> para os atributos personalizados.  
  
 **✓ DO** fornecem propriedades configuráveis para argumentos opcionais.  
  
 **✓ DO** fornecem propriedades somente obtenção para os argumentos necessários.  
  
 **✓ DO** fornecer parâmetros de construtor para inicializar propriedades correspondentes para os argumentos necessários. Cada parâmetro deve ter o mesmo nome (embora com maiúsculas e minúsculas diferentes) como a propriedade correspondente.  
  
 **X AVOID** fornecendo os parâmetros do construtor para inicializar propriedades correspondentes para os argumentos opcionais.  
  
 Em outras palavras, não têm propriedades que podem ser definidas com um construtor e um setter. Essa diretriz torna muito explícito quais argumentos são opcionais e que são necessários e evita que você tenha duas maneiras de fazer a mesma coisa.  
  
 **X AVOID** sobrecarga construtores de atributo personalizado.  
  
 Ter apenas um construtor se comunica claramente ao usuário quais argumentos são necessários e quais são opcionais.  
  
 **✓ DO** lacrar classes de atributo personalizado, se possível. Isso torna a pesquisa para o atributo mais rápida.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
