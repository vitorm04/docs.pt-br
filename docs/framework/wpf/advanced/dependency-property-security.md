---
title: Segurança de propriedade da dependência
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: f5640b348ccd68819052f58756489489371862d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186393"
---
# <a name="dependency-property-security"></a>Segurança de propriedade da dependência
As propriedades da dependência geralmente devem ser consideradas como propriedades públicas. A natureza do sistema de propriedades [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] impede que a capacidade de dar garantias de segurança sobre um valor da propriedade de dependência.  

<a name="AccessSecurity"></a>
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Acesso e segurança de Wrappers e propriedades de dependência  
 Normalmente, as propriedades de dependência são implementadas juntamente com propriedades de tempo de execução de linguagem comum (CLR) que simplificam a obtenção ou configuração da propriedade a partir de uma instância. Mas os invólucros são realmente apenas <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> métodos de conveniência que implementam as chamadas subjacentes e estáticas que são usadas ao interagir com propriedades de dependência. Pensando nisso de outra forma, as propriedades são expostas como propriedades comuns de tempo de execução (CLR) que por acaso são apoiadas por uma propriedade de dependência e não por um campo privado. Mecanismos de segurança aplicados aos wrappers não são paralelo ao comportamento do sistema de propriedade e acesso da propriedade de dependência subjacente. Colocar uma demanda de segurança no invólucro só impedirá o <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A>uso do método de conveniência, mas não impedirá chamadas ou . Da mesma forma, impor um nível de acesso protegido ou privado aos wrappers não oferece nenhuma segurança efetiva.  
  
 Se você está escrevendo suas próprias propriedades de dependência, <xref:System.Windows.DependencyProperty> você deve declarar os invólucros e o campo identificador como membros públicos, para que os chamadores não obtenham informações enganosas sobre o verdadeiro nível de acesso dessa propriedade (devido à sua loja ser implementada como uma propriedade de dependência).  
  
 Para uma propriedade de dependência personalizada, você pode registrar sua propriedade como uma propriedade de dependência somente leitura, e isso fornece um <xref:System.Windows.DependencyPropertyKey> meio eficaz de impedir que um imóvel seja definido por qualquer pessoa que não tenha uma referência à propriedade. Para obter mais informações, consulte [Propriedades de dependência somente leitura](read-only-dependency-properties.md).  
  
> [!NOTE]
> Declarar um <xref:System.Windows.DependencyProperty> campo identificador privado não é proibido, e pode ser usado para ajudar a reduzir o espaço de nome imediatamente exposto de uma classe personalizada, mas tal propriedade não deve ser considerada "privada" no mesmo sentido que as definições de linguagem comum (CLR) definem esse nível de acesso, por razões descritas na próxima seção.  
  
<a name="PropertySystemExposure"></a>
## <a name="property-system-exposure-of-dependency-properties"></a>Exposição do sistema de propriedades das propriedades de dependência  
 Não é geralmente útil, e é potencialmente <xref:System.Windows.DependencyProperty> enganoso, declarar um como qualquer nível de acesso que não seja público. Essa configuração de nível de acesso só impede que alguém possa obter uma referência à instância da classe declarante. Mas há vários aspectos do sistema de <xref:System.Windows.DependencyProperty> propriedade que retornarão a como meio de identificar uma propriedade específica como ela existe em uma instância <xref:System.Windows.DependencyObject.SetValue%2A> de uma classe ou uma instância de classe derivada, e este identificador ainda é utilizável em uma chamada mesmo que o identificador estático original seja declarado como não público. Além <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> disso, os métodos virtuais recebem informações de qualquer propriedade de dependência existente que alterou o valor. Além disso, <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> o método retorna identificadores para qualquer propriedade em instâncias com um valor definido localmente.  
  
### <a name="validation-and-security"></a>Validação e segurança  
 Aplicar uma demanda <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> a um e esperar que a falha de validação em uma falha de demanda para impedir que uma propriedade seja definida não é um mecanismo de segurança adequado. A invalidação de valor <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> definido aplicada também pode ser suprimida por chamadores mal-intencionados, se esses chamadores estiverem operando dentro do domínio do aplicativo.  
  
## <a name="see-also"></a>Confira também

- [Propriedades de dependência personalizada](custom-dependency-properties.md)
