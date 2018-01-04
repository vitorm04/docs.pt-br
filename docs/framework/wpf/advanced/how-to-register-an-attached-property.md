---
title: Como registrar uma propriedade anexada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c727eee7b56473808fec06ea42044fc742f7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-an-attached-property"></a>Como registrar uma propriedade anexada
Este exemplo mostra como registrar uma propriedade anexada e fornecer acessadores públicos para que você possa usar a propriedade no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e no código. Propriedades anexadas são um conceito de sintaxe definido pelo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. A maioria das propriedades anexadas para tipos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também são implementadas como propriedades de dependência. Você pode usar propriedades de dependência em qualquer <xref:System.Windows.DependencyObject> tipos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como registrar uma propriedade anexada como uma propriedade de dependência, usando o <xref:System.Windows.DependencyProperty.RegisterAttached%2A> método. A classe de provedor tem a opção de fornecer metadados padrão para a propriedade é aplicável quando a propriedade é usada em outra classe, a menos que essa classe substitua os metadados. Neste exemplo, o valor padrão da propriedade `IsBubbleSource` está definido como `false`.  
  
 A classe de provedor para uma propriedade anexada (mesmo se não estiver registrada como uma propriedade de dependência) deve fornecer acessadores get e set estáticos que sigam a convenção de nomenclatura `Set` *[AttachedPropertyName]* e `Get` *[AttachedPropertyName]*. Esses acessadores são necessários para que o leitor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em execução possa reconhecer a propriedade como um atributo em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e resolver os tipos apropriados.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.DependencyProperty>  
 [Visão geral das propriedades da dependência](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Propriedades de dependência personalizada](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
