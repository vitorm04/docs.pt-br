---
title: Atributo PresentationOptions:Freeze
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: 896f7b24599b68f178d2a006e5ddc07278564bde
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546065"
---
# <a name="presentationoptionsfreeze-attribute"></a>Atributo PresentationOptions:Freeze
Conjuntos de <xref:System.Windows.Freezable.IsFrozen%2A> estado para `true` em que o contém <xref:System.Windows.Freezable> elemento. Comportamento padrão para um <xref:System.Windows.Freezable> sem o `PresentationOptions:Freeze` atributo especificado é que <xref:System.Windows.Freezable.IsFrozen%2A> é `false` em tempo de carregamento e dependente geral <xref:System.Windows.Freezable> comportamento em tempo de execução.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`PresentationOptions`|Um prefixo de namespace de XML, que pode ser qualquer cadeia de caracteres de prefixo válida, conforme a especificação XML 1.0. O prefixo `PresentationOptions` é usado para fins de identificação nesta documentação.|  
|`freezableElement`|Um elemento que instancia qualquer classe derivada de <xref:System.Windows.Freezable>.|  
  
## <a name="remarks"></a>Comentários  
 O atributo `Freeze` é o único atributo ou elemento de programação definido no namespace de XML de `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. O atributo `Freeze` existe nesse namespace especial especificamente para que ele possa ser designado como ignorável, usando [Atributo mc:Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) como parte das declarações do elemento raiz. O motivo que `Freeze` deve poder ser ignorável é que nem todos os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementações de processador são capazes de congelar uma <xref:System.Windows.Freezable> no tempo de carregamento; esse recurso não é parte do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] especificação.  
  
 A capacidade de processar o atributo `Freeze` é especificamente interna ao processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que processa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para aplicativos compilados. O atributo não tem suporte em nenhuma classe e a sintaxe de atributo não é extensível ou modificável. Se você estiver implementando seu próprio [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador que você pode optar por paralelo o comportamento de congelamento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador ao processar o `Freeze` atributo no <xref:System.Windows.Freezable> elementos no tempo de carregamento.  
  
 Qualquer valor para o atributo `Freeze` diferente de `true` (não diferencia maiúsculas e minúsculas) gera um erro de tempo de carga. (Especificar o atributo `Freeze` como `false` não é um erro, porém esse já é o padrão, por isso a configuração para `false` não faz nada).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Freezable>  
 [Visão geral de objetos congeláveis](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Atributo mc:Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
