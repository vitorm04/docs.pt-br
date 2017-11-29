---
title: "Segurança de propriedade da dependência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8c1dc0ea45efe32e36b649d92111fff3d5f61a7
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="dependency-property-security"></a>Segurança de propriedade da dependência
As propriedades da dependência geralmente devem ser consideradas como propriedades públicas. A natureza do sistema de propriedades [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] impede que a capacidade de dar garantias de segurança sobre um valor da propriedade de dependência.  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Acesso e segurança de Wrappers e propriedades de dependência  
 Normalmente, as propriedades de dependência são implementadas junto com propriedades [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] de "wrapper" que simplificam obter e configurar a propriedade de uma instância. Mas os wrappers são métodos realmente convenientes que implementam subjacente <xref:System.Windows.DependencyObject.GetValue%2A> e <xref:System.Windows.DependencyObject.SetValue%2A> chamadas estáticas que são usadas ao interagir com propriedades de dependência. Pensando nisso de outra forma, as propriedades são expostas como propriedades [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] que têm o respaldo de uma propriedade de dependência, em vez de um campo particular. Mecanismos de segurança aplicados aos wrappers não são paralelo ao comportamento do sistema de propriedade e acesso da propriedade de dependência subjacente. Colocar uma exigência de segurança em um wrapper só irá prevenir o uso do método conveniente mas não irá prevenir chamadas para <xref:System.Windows.DependencyObject.GetValue%2A> ou <xref:System.Windows.DependencyObject.SetValue%2A>. Da mesma forma, impor um nível de acesso protegido ou privado aos wrappers não oferece nenhuma segurança efetiva.  
  
 Se você estiver escrevendo suas próprias propriedades de dependência, você deve declarar os wrappers e o <xref:System.Windows.DependencyProperty> identificador de campo como membros públicos, para que os chamadores não obter falsos informações sobre o nível de acesso de propriedade (devido ao seu repositório está sendo implementado como uma propriedade de dependência).  
  
 Para uma propriedade de dependência personalizada, você pode registrar sua propriedade como uma propriedade de dependência somente leitura, e isso fornece um meio eficaz de impedir que uma propriedade sendo definida por qualquer pessoa que não possui uma referência para o <xref:System.Windows.DependencyPropertyKey> para essa propriedade. Para obter mais informações, consulte [Propriedades de dependência somente leitura](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
> [!NOTE]
>  Declarando um <xref:System.Windows.DependencyProperty> identificador campo privado não é proibido e perfeitamente pode ser usado para ajudar a reduzir o namespace exposto imediato de uma classe personalizada, mas essa propriedade não deve ser considerada "private" no mesmo sentido que a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] definições de idioma definem o nível de acesso, por razões descritas na próxima seção.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Exposição do sistema de propriedades das propriedades de dependência  
 Não é geralmente útil, e é potencialmente enganosa para declarar um <xref:System.Windows.DependencyProperty> como qualquer nível de acesso diferente de público. Essa configuração de nível de acesso só impede que alguém possa obter uma referência à instância da classe declarante. Mas há vários aspectos do sistema de propriedades que retornará um <xref:System.Windows.DependencyProperty> como o modo de identificar uma propriedade específica, como ele existe em uma instância de uma classe ou uma instância de classe derivada, e este identificador é ainda pode ser usado em um <xref:System.Windows.DependencyObject.SetValue%2A> chamar mesmo Se o identificador estático original é declarado como confidenciais. Além disso, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> métodos virtuais recebem informações de qualquer propriedade de dependência existente que mudaram de valor. Além disso, o <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> método retorna identificadores para qualquer propriedade em instâncias com definidos localmente valor.  
  
### <a name="validation-and-security"></a>Validação e segurança  
 Aplicar uma demanda para um <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> e esperar a falha de validação em uma falha de demanda para impedir que uma propriedade sendo definida não é um mecanismo de segurança adequado. Invalidação de valor definido aplicada por meio de <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> podem também ser suprimidos por chamadores mal-intencionados, se esses chamadores estão operando dentro do domínio de aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades de dependência personalizadas](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
