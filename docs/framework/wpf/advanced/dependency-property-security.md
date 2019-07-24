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
ms.openlocfilehash: 2f9de32eb8637e58c17aba2309eed33dcfdd42a7
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400762"
---
# <a name="dependency-property-security"></a>Segurança de propriedade da dependência
As propriedades da dependência geralmente devem ser consideradas como propriedades públicas. A natureza do sistema de propriedades [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] impede que a capacidade de dar garantias de segurança sobre um valor da propriedade de dependência.  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>Acesso e segurança de Wrappers e propriedades de dependência  
 Normalmente, as propriedades de dependência são implementadas junto com as propriedades de "wrapper" Common Language Runtime (CLR) que simplificam a obtenção ou a definição da propriedade de uma instância. Mas os wrappers são, na verdade, métodos de conveniência que <xref:System.Windows.DependencyObject.GetValue%2A> implementam as chamadas subjacentes e <xref:System.Windows.DependencyObject.SetValue%2A> estáticas que são usadas ao interagir com propriedades de dependência. Pensando nisso de outra forma, as propriedades são expostas como propriedades Common Language Runtime (CLR) que, por sua vez, são apoiadas por uma propriedade de dependência, e não por um campo privado. Mecanismos de segurança aplicados aos wrappers não são paralelo ao comportamento do sistema de propriedade e acesso da propriedade de dependência subjacente. Colocar uma demanda de segurança no wrapper só impedirá o uso do método de conveniência, mas não impedirá <xref:System.Windows.DependencyObject.SetValue%2A>chamadas para <xref:System.Windows.DependencyObject.GetValue%2A> ou. Da mesma forma, impor um nível de acesso protegido ou privado aos wrappers não oferece nenhuma segurança efetiva.  
  
 Se você estiver escrevendo suas próprias propriedades de dependência, deverá declarar os wrappers e o <xref:System.Windows.DependencyProperty> campo identificador como membros públicos, para que os chamadores não obtenham informações enganosas sobre o nível de acesso verdadeiro dessa propriedade (devido à sua loja estar sendo implementado como uma propriedade de dependência).  
  
 Para uma propriedade de dependência personalizada, você pode registrar sua propriedade como uma propriedade de dependência somente leitura, e isso fornece um meio efetivo de impedir que uma propriedade seja definida por qualquer pessoa que não tenha uma referência ao <xref:System.Windows.DependencyPropertyKey> para essa propriedade. Para obter mais informações, consulte [Propriedades de dependência somente leitura](read-only-dependency-properties.md).  
  
> [!NOTE]
>  Declarar um <xref:System.Windows.DependencyProperty> campo de identificador privado não é proibido e pode ser usado de forma razoável para ajudar a reduzir o namespace exposto imediatamente de uma classe personalizada, mas essa propriedade não deve ser considerada "privada" no mesmo sentido que a linguagem comum as definições de linguagem de tempo de execução (CLR) definem esse nível de acesso, por motivos descritos na próxima seção.  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>Exposição do sistema de propriedades das propriedades de dependência  
 Ele não é geralmente útil e é potencialmente enganoso, para declarar um <xref:System.Windows.DependencyProperty> como qualquer nível de acesso diferente do público. Essa configuração de nível de acesso só impede que alguém possa obter uma referência à instância da classe declarante. Mas há vários aspectos do sistema de propriedades que retornarão um <xref:System.Windows.DependencyProperty> como o meio de identificar uma determinada propriedade como ela existe em uma instância de uma classe ou instância de classe derivada, e esse identificador ainda pode ser usado em uma <xref:System.Windows.DependencyObject.SetValue%2A> chamada mesmo Se o identificador estático original for declarado como não público. Além disso <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> , os métodos virtuais recebem informações de qualquer propriedade de dependência existente que alterou o valor. Além disso, o <xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> método retorna identificadores para qualquer propriedade em instâncias com um valor definido localmente.  
  
### <a name="validation-and-security"></a>Validação e segurança  
 Aplicar uma demanda a um <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> e esperar a falha de validação em uma falha de demanda para impedir que uma propriedade seja definida não é um mecanismo de segurança adequado. A invalidação do set-value imposta por meio <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> de também pode ser suprimida por chamadores mal-intencionados, se esses chamadores estiverem operando no domínio do aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Propriedades de dependência personalizada](custom-dependency-properties.md)
