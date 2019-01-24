---
title: Funcionalidades de linguagem XAML 2009
ms.date: 03/30/2017
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
ms.openlocfilehash: 36b1ad197b5c8e38c77a9a6a92ba1b3b659efbb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661315"
---
# <a name="xaml-2009-language-features"></a>Funcionalidades de linguagem XAML 2009
XAML 2009 é o termo de forma abreviada para novos recursos de linguagem XAML que estendem a especificação da linguagem XAML existente. XAML 2009 introduz várias novas diretivas e construções. Isso inclui o [x: argumentos diretiva](../../../docs/framework/xaml-services/x-arguments-directive.md); o [diretiva X:factorymethod](../../../docs/framework/xaml-services/x-factorymethod-directive.md); o [extensão de marcação X:Reference](../../../docs/framework/xaml-services/x-reference-markup-extension.md); a [diretiva X:TypeArguments ](../../../docs/framework/xaml-services/x-typearguments-directive.md); e tipos inseridos para primitivos de linguagem comum (por exemplo `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Suporte de 2009 do XAML no WPF e o Visual Studio  
 No WPF, você pode usar os recursos do XAML 2009, mas somente para XAML que não é compilado por marcação do WPF. XAML compilado por marcação e o formato BAML de XAML não têm suporte no momento, as palavras-chave de linguagem XAML 2009 e os recursos.  
  
 Observe que as técnicas existentes de carregamento XAML flexível no WPF também têm possíveis segurança e restrições de acesso para tipos CLR e o sistema de tipos que são mais restritivas do que para o XAML compilado por marcação. Para obter mais informações, consulte [segurança (WPF)](../../../docs/framework/wpf/security-wpf.md) ou [estratégia de segurança do WPF – segurança da plataforma](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 também apresenta os recursos adicionais que modifique o XAML de 2006 anterior construções ou que modificar os formulários de marcação básica.  
  
### <a name="xkey-as-an-object-element"></a>X:Key como um elemento de objeto  
 Pode dar suporte a XAML 2009 `x:Key` como um objeto (um elemento de propriedade que tem o valor do elemento de objeto); no entanto, o XAML 2006 só tem suporte `x:Key` como um atributo. Consulte a seção "XAML 2009" [X:Key](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns em elementos de propriedade  
 XAML 2009 pode dar suporte a definições de namespace (xmlns) de XAML em elementos de propriedade; No entanto, o XAML 2006 suporta apenas definições xmlns em elementos de objeto.  
  
### <a name="event-attributes"></a>Atributos de eventos  
 Para atributos que são apoiados por eventos, o XAML 2006 presume que a compilação de marcação está envolvida e envia os eventos de compilação de marcação. XAML 2009 dá suporte a um formulário de marcação que se parece com uma extensão de marcação, que adia a fiação de evento até o tempo de execução de análise e carregar o XAML. No entanto, aplicativos WPF e cenários XAML para WPF UI geralmente não usam esse recurso. WPF e sua implementação do XAML 2006 usa a combinação de fiação do manipulador de eventos para eventos roteados definidos no <xref:System.Windows.UIElement> nível e o compilador de marcação etapa na maior parte do seu processamento do atributo de evento. O compilador de marcação também pré-processa quaisquer atributos de evento encontrados no XAML em que as ações de build declarar que o compilador de marcação é usado.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
