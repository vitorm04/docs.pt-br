---
title: Recursos de linguagem XAML 2009
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: ac18be4732d223561d3a0afcef0e650587385822
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459886"
---
# <a name="xaml-2009-language-features"></a>Recursos de linguagem XAML 2009
O XAML 2009 é o termo abreviado para novos recursos de linguagem XAML que estendem a especificação de linguagem XAML existente. O XAML 2009 apresenta várias novas diretivas e construções. Isso inclui a [diretiva x:Arguments](x-arguments-directive.md); a [diretiva x:FactoryMethod](x-factorymethod-directive.md); a [extensão de marcação x:Reference](x-reference-markup-extension.md); a [diretiva x:TypeArguments](x-typearguments-directive.md); e tipos internos para primitivos de linguagem comum (por exemplo `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Suporte a XAML 2009 no WPF e no Visual Studio  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não seja uma marcação do WPF compilada. O XAML com compilação de marcação e a forma de BAML do XAML atualmente não dão suporte às palavras-chave e aos recursos da linguagem XAML 2009.  
  
 Observe que as técnicas existentes para carregar o XAML flexível no WPF também têm possíveis restrições de segurança e acesso aos tipos CLR e ao sistema de tipos que são mais restritivos do que para XAML com compilação de marcação. Para obter mais informações, consulte [segurança (WPF)](../wpf/security-wpf.md) ou [estratégia de segurança do WPF-segurança da plataforma](../wpf/wpf-security-strategy-platform-security.md).  
  
 O XAML 2009 também apresenta recursos adicionais que modificam as construções XAML 2006 anteriores ou que modificam os formulários de marcação básicos.  
  
### <a name="xkey-as-an-object-element"></a>x:Key como um elemento de objeto  
 O XAML 2009 pode dar suporte a `x:Key` como um objeto (um elemento de propriedade que tem um valor de elemento de objeto); no entanto, o XAML 2006 só tem suporte `x:Key` como um atributo. Consulte a seção "XAML 2009" da [diretiva x:Key](x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns em elementos de propriedade  
 O XAML 2009 pode dar suporte a definições de namespace XAML (xmlns) em elementos de propriedade; no entanto, o XAML 2006 dá suporte apenas a definições xmlns em elementos Object.  
  
### <a name="event-attributes"></a>Atributos do evento  
 Para atributos que são apoiados por eventos, o XAML 2006 supõe que a compilação da marcação esteja envolvida e envie os eventos para a compilação da marcação. O XAML 2009 dá suporte a um formulário de marcação que se assemelha a uma extensão de marcação, o que adia a fiação do evento até a análise e o carregamento do XAML do tempo de execução. No entanto, os aplicativos WPF e cenários XAML para a interface do usuário do WPF geralmente não usam esse recurso. O WPF e sua implementação XAML 2006 usam a combinação de fiação de manipulador de eventos para eventos roteados definidos no nível de <xref:System.Windows.UIElement> e sua etapa de compilador de marcação para grande parte de seu processamento de atributo de evento. O compilador de marcação também processa quaisquer atributos de evento encontrados em XAML em que as ações de compilação declaram que o compilador de marcação é usado.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
