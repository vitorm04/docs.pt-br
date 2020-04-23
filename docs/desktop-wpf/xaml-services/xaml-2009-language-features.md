---
title: Recursos de linguagem XAML 2009
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: e58e6757b88958bf8a3547c8a272c2e6298dcecb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071594"
---
# <a name="xaml-2009-language-features"></a>Recursos de linguagem XAML 2009
XAML 2009 é o termo abreviado para novos recursos de linguagem XAML que ampliam a especificação de linguagem XAML existente. XAML 2009 introduz várias novas diretrizes e construções. Estes incluem a [diretiva x:Argumentos;](xarguments-directive.md) [x:Diretiva FactoryMethod;](xfactorymethod-directive.md) a [extensão x:Marcação de referência;](xreference-markup-extension.md) a [diretiva x:TypeArguments;](xtypearguments-directive.md) e tipos incorporados para primitivos da `x:Char`linguagem comum (por exemplo ).

## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Suporte XAML 2009 no WPF e Visual Studio

No WPF, você pode usar os recursos do XAML 2009, mas apenas para XAML que não é compilado por marcação WPF. O XAML compilado por marcação e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do idioma XAML 2009.

Observe que as técnicas existentes para carregar XAML solto no WPF também têm possíveis restrições de segurança e acesso aos tipos CLR e ao sistema de tipo que são mais restritivos do que para XAML compilado por marcação. Para obter mais informações, consulte [Segurança (WPF)](../../framework/wpf/security-wpf.md) ou [WPF Security Strategy - Platform Security](../../framework/wpf/wpf-security-strategy-platform-security.md).

XAML 2009 também introduz recursos adicionais que modificam os construtos XAML 2006 anteriores ou que modificam os formulários básicos de marcação.

### <a name="xkey-as-an-object-element"></a>x:Chave como elemento objeto

XAML 2009 `x:Key` pode suportar como um objeto (um elemento de propriedade que tem valor de elemento de objeto); no entanto, XAML 2006 só suportado `x:Key` como um atributo. Consulte a seção "XAML 2009" de [x:Key Directive](xkey-directive.md).

### <a name="xmlns-on-property-elements"></a>xmlns em Elementos de Propriedade

XAML 2009 pode suportar definições de namespace XAML (xmlns) em elementos de propriedade; no entanto, XAML 2006 só suporta definições xmlns em elementos de objeto.

### <a name="event-attributes"></a>Atributos de evento

Para atributos apoiados por eventos, xaml 2006 presume que a compilação de marcação está envolvida e submete os eventos à compilação de marcação. XAML 2009 suporta uma forma de marcação que se assemelha a uma extensão de marcação, que adia a fiação do evento até a análise e carregamento do XAML. No entanto, os aplicativos WPF e os cenários XAML para WPF UI geralmente não usam esse recurso. O WPF e sua implementação XAML 2006 utilizam a combinação <xref:System.Windows.UIElement> de fiação do manipulador de eventos para eventos roteados definidos no nível e sua etapa de compilação de marcação para grande parte do processamento de atributos de evento. O compilador de marcação também préprocessa quaisquer atributos de evento encontrados no XAML, onde as ações de compilação declaram que o compilador de marcação é usado.

## <a name="see-also"></a>Confira também

- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
