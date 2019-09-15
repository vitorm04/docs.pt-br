---
title: Atributo PresentationOptions:Freeze
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991424"
---
# <a name="presentationoptionsfreeze-attribute"></a>Atributo PresentationOptions:Freeze
Define o <xref:System.Windows.Freezable.IsFrozen%2A> estado como `true` no elemento que <xref:System.Windows.Freezable> o contém. O comportamento padrão para <xref:System.Windows.Freezable> um sem `PresentationOptions:Freeze` o atributo especificado é <xref:System.Windows.Freezable.IsFrozen%2A> que `false` está no tempo de carregamento e depende do <xref:System.Windows.Freezable> comportamento geral em tempo de execução.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
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
 O atributo `Freeze` é o único atributo ou elemento de programação definido no namespace de XML de `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`. O atributo `Freeze` existe nesse namespace especial especificamente para que ele possa ser designado como ignorável, usando [Atributo mc:Ignorable](mc-ignorable-attribute.md) como parte das declarações do elemento raiz. O motivo pelo `Freeze` qual deve ser possível ignorá-lo é porque nem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] todas as implementações do processador podem <xref:System.Windows.Freezable> congelar um em tempo de carregamento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; esse recurso não faz parte da especificação.  
  
 A capacidade de processar o atributo `Freeze` é especificamente interna ao processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que processa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para aplicativos compilados. O atributo não tem suporte em nenhuma classe e a sintaxe de atributo não é extensível ou modificável. Se você estiver implementando seu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] próprio processador, poderá optar por paralelizar o comportamento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de congelamento do processador ao `Freeze` processar o <xref:System.Windows.Freezable> atributo em elementos em tempo de carregamento.  
  
 Qualquer valor para o atributo `Freeze` diferente de `true` (não diferencia maiúsculas e minúsculas) gera um erro de tempo de carga. (Especificar o atributo `Freeze` como `false` não é um erro, porém esse já é o padrão, por isso a configuração para `false` não faz nada).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Freezable>
- [Visão geral de objetos congeláveis](freezable-objects-overview.md)
- [Atributo mc:Ignorable](mc-ignorable-attribute.md)
