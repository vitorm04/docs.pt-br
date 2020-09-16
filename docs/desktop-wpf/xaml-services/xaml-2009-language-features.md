---
title: Recursos de linguagem XAML 2009
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: dfa2841d8bc1ed1429372908f0dda97d178c4ac3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556701"
---
# <a name="xaml-2009-language-features"></a>Recursos de linguagem XAML 2009
O XAML 2009 é o termo abreviado para novos recursos de linguagem XAML que estendem a especificação de linguagem XAML existente. O XAML 2009 apresenta várias novas diretivas e construções. Isso inclui a [diretiva x:Arguments](xarguments-directive.md); a [diretiva x:FactoryMethod](xfactorymethod-directive.md); a [extensão de marcação x:Reference](xreference-markup-extension.md); a [diretiva x:TypeArguments](xtypearguments-directive.md); e tipos internos para primitivos de linguagem comum (por exemplo `x:Char` ).

## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Suporte a XAML 2009 no WPF e no Visual Studio

No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja uma marcação do WPF compilada. O XAML com compilação de marcação e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos da linguagem XAML 2009.

Observe que as técnicas existentes para carregar o XAML flexível no WPF também têm possíveis restrições de segurança e acesso aos tipos CLR e ao sistema de tipos que são mais restritivos do que para XAML com compilação de marcação. Para obter mais informações, consulte [segurança (WPF)](/dotnet/desktop/wpf/security-wpf) ou [estratégia de segurança do WPF-segurança da plataforma](/dotnet/desktop/wpf/wpf-security-strategy-platform-security).

O XAML 2009 também apresenta recursos adicionais que modificam as construções XAML 2006 anteriores ou que modificam os formulários de marcação básicos.

### <a name="xkey-as-an-object-element"></a>x:Key como um elemento de objeto

O XAML 2009 pode dar suporte `x:Key` como um objeto (um elemento de propriedade com valor de elemento de objeto); no entanto, o xaml 2006 só tem suporte `x:Key` como um atributo. Consulte a seção "XAML 2009" da [diretiva x:Key](xkey-directive.md).

### <a name="xmlns-on-property-elements"></a>xmlns em elementos de propriedade

O XAML 2009 pode dar suporte a definições de namespace XAML (xmlns) em elementos de propriedade; no entanto, o XAML 2006 dá suporte apenas a definições xmlns em elementos Object.

### <a name="event-attributes"></a>Atributos do evento

Para atributos que são apoiados por eventos, o XAML 2006 supõe que a compilação da marcação esteja envolvida e envie os eventos para a compilação da marcação. O XAML 2009 dá suporte a um formulário de marcação que se assemelha a uma extensão de marcação, o que adia a fiação do evento até a análise e o carregamento do XAML do tempo de execução. No entanto, os aplicativos WPF e cenários XAML para a interface do usuário do WPF geralmente não usam esse recurso. O WPF e sua implementação XAML 2006 usam a combinação de fiação do manipulador de eventos para eventos roteados definidos no <xref:System.Windows.UIElement> nível e sua etapa do compilador de marcação para grande parte de seu processamento de atributo de evento. O compilador de marcação também processa quaisquer atributos de evento encontrados em XAML em que as ações de compilação declaram que o compilador de marcação é usado.

## <a name="see-also"></a>Confira também

- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
