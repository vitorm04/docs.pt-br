---
title: Attributes1
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 493ac709123c67311ba570894fb324ae7148bfae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574628"
---
# <a name="attributes"></a>Atributos
<xref:System.Attribute?displayProperty=nameWithType> uma classe base é usada para definir atributos personalizados.  
  
 Os atributos são anotações que podem ser adicionadas aos elementos de programação, como assemblies, tipos, membros e parâmetros. Eles são armazenados nos metadados do assembly e podem ser acessados no tempo de execução usando as APIs de reflexão. Por exemplo, a estrutura define o <xref:System.ObsoleteAttribute>, que pode ser aplicado a um tipo ou um membro para indicar que o tipo ou membro foi preterido.  
  
 Atributos podem ter uma ou mais propriedades que contêm dados adicionais relacionados ao atributo. Por exemplo, `ObsoleteAttribute` pode conter informações adicionais sobre a versão em que um tipo ou membro foi preterido e a descrição das novas APIs, substituindo a API obsoleta.  
  
 Algumas propriedades de um atributo devem ser especificadas quando o atributo é aplicado. Esses são denominados as propriedades necessárias ou os argumentos necessários, porque eles são representados como parâmetros posicionais construtor. Por exemplo, o <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> propriedade o <xref:System.Diagnostics.ConditionalAttribute> é uma propriedade necessária.  
  
 Propriedades que não precisam necessariamente ser especificado quando o atributo é aplicado são chamadas propriedades opcionais (ou argumentos opcionais). Eles são representados por propriedades configuráveis. Compiladores de fornecem uma sintaxe especial para definir essas propriedades quando um atributo é aplicado. Por exemplo, o <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriedade representa um argumento opcional.  
  
 **FAZER ✓** nome classes de atributos personalizados com o sufixo "Atributo".  
  
 **FAZER ✓** se aplicam a <xref:System.AttributeUsageAttribute> para os atributos personalizados.  
  
 **FAZER ✓** fornecem propriedades configuráveis para argumentos opcionais.  
  
 **FAZER ✓** fornecem propriedades somente obtenção para os argumentos necessários.  
  
 **FAZER ✓** fornecer parâmetros de construtor para inicializar propriedades correspondentes para os argumentos necessários. Cada parâmetro deve ter o mesmo nome (embora com diferenciam maiusculas de minúsculas) como a propriedade correspondente.  
  
 **X Evite** fornecendo os parâmetros do construtor para inicializar propriedades correspondentes para os argumentos opcionais.  
  
 Em outras palavras, não têm propriedades que podem ser definidas com um construtor e um setter. Esta diretriz torna muito explícitas que os argumentos são opcionais que são necessárias, e evita a necessidade de duas maneiras de fazer a mesma coisa.  
  
 **X Evite** sobrecarga construtores de atributo personalizado.  
  
 Claramente ter apenas um construtor se comunica com o usuário que são necessários e opcionais.  
  
 **FAZER ✓** lacrar classes de atributo personalizado, se possível. Isso torna a pesquisa para o atributo mais rapidamente.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
