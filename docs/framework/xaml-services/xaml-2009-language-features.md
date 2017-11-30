---
title: Funcionalidades de linguagem XAML 2009
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML 2009 [XAML Services]
- XAML [XAML Services], XAML 2009
ms.assetid: f6bb18d8-c86a-4549-8862-323e6b32a8dd
caps.latest.revision: "11"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 6299a29cb79650eb59df3f198c3ea3fcd49d0076
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-2009-language-features"></a>Funcionalidades de linguagem XAML 2009
XAML 2009 é o termo abreviado para os novos recursos de linguagem XAML que estendem a especificação da linguagem XAML existente. XAML 2009 apresenta várias novas diretivas e construtores. Isso inclui o[diretiva X:arguments](../../../docs/framework/xaml-services/x-arguments-directive.md); o [diretiva X:factorymethod](../../../docs/framework/xaml-services/x-factorymethod-directive.md); o [extensão de marcação X:Reference](../../../docs/framework/xaml-services/x-reference-markup-extension.md); o [diretiva X:TypeArguments ](../../../docs/framework/xaml-services/x-typearguments-directive.md); e os tipos internos para primitivos de linguagem comum (por exemplo `x:Char`).  
  
<a name="xaml_2009_support_in_wpf_and_visual_studio"></a>   
## <a name="xaml-2009-support-in-wpf-and-visual-studio"></a>Suporte de 2009 XAML em WPF e do Visual Studio  
 No WPF, você pode usar os recursos de XAML 2009, mas apenas para XAML que não é compilado marcação do WPF. Compilação de marcação XAML e o formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de linguagem XAML 2009.  
  
 Observe que técnicas existentes para o carregamento XAML livre no WPF também têm possíveis segurança e restrições de acesso para tipos CLR e o sistema de tipos que são mais restritivas do que para compilação de marcação XAML. Para obter mais informações, consulte [segurança (WPF)](../../../docs/framework/wpf/security-wpf.md) ou [estratégia de segurança do WPF - segurança da plataforma](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md).  
  
 XAML 2009 também apresenta recursos adicionais que modifique o 2006 XAML anterior construções ou que modificar os formulários de marcação básica.  
  
### <a name="xkey-as-an-object-element"></a>x: chave como um elemento de objeto  
 Pode dar suporte a XAML 2009 `x:Key` como um objeto (um elemento de propriedade que tem o valor do elemento de objeto); no entanto, o XAML 2006 só tem suporte `x:Key` como um atributo. Consulte a seção "XAML 2009" [diretiva X:Key](../../../docs/framework/xaml-services/x-key-directive.md).  
  
### <a name="xmlns-on-property-elements"></a>xmlns em elementos de propriedade  
 XAML 2009 pode dar suporte a definições de namespace (xmlns) XAML em elementos de propriedade; No entanto, o XAML 2006 suporta apenas definições xmlns em elementos de objeto.  
  
### <a name="event-attributes"></a>Atributos de evento  
 Para atributos que são feitos por eventos, 2006 XAML pressupõe que a compilação da marcação está envolvida e envia os eventos de compilação da marcação. XAML 2009 dá suporte a um formulário de marcação que se parece com uma extensão de marcação, que transfere a ligação de evento até o tempo de execução de análise e o carregamento do XAML. No entanto, os aplicativos WPF e cenários XAML para WPF UI geralmente não usar esse recurso. WPF e sua implementação de 2006 XAML usa a combinação de cabeamento de manipulador de eventos para eventos roteados definidos no <xref:System.Windows.UIElement> nível e o compilador de marcação etapa muito seu atributo processamento de eventos. O compilador de marcação pré-processa também quaisquer atributos de evento encontrados no XAML em que as ações de compilação declara que o compilador de marcação é usado.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
