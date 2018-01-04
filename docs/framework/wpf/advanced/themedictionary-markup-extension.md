---
title: "Extensão de marcação ThemeDictionary"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2372961cdc889528f13e13dd1f1760608030275e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="themedictionary-markup-extension"></a>Extensão de marcação ThemeDictionary
Fornece uma maneira para autores de controles personalizados ou aplicativos que integram controles de terceiros de carregar os dicionários de recursos específicos de temas para uso ao aplicar estilo ao controle.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`assemblyUri`|O [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] do assembly que contém informações de tema. Normalmente, esse é um URI "pack://" que referencia um assembly no pacote maior. Recursos de assembly e URIs "pack://" simplificam os problemas de implantação. Para obter mais informações, consulte [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).|  
  
## <a name="remarks"></a>Comentários  
 Essa extensão destina-se a preencher apenas uma valor de propriedade específico: um valor para <xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>.  
  
 Usando essa extensão, você pode especificar um único assembly apenas de recursos que contém alguns estilos a serem usados somente quando o tema [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] é aplicado ao sistema do usuário, outros estilos quando o tema Luna estiver ativo, e assim por diante. Usando essa extensão, o conteúdo de um dicionário de recursos específico do controle pode ser invalidado e recarregado automaticamente para ser específico para outro tema quando necessário.  
  
 O `assemblyUri` cadeia de caracteres (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> valor da propriedade) constitui a base de uma convenção de nomenclatura que identifica qual dicionário aplica-se a um tema específico. O <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> lógica para `ThemeDictionary` conclui a convenção por gerar um [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] que aponta para uma variante do dicionário de tema específico, como contido em um assembly de recursos pré-compilado. A descrição dessa convenção, ou as interações dos temas com estilos gerais de controle e estilos de nível de página/aplicativo como um conceito não é abordado completamente aqui. O cenário básico para uso `ThemeDictionary` é especificar o <xref:System.Windows.ResourceDictionary.Source%2A> propriedade de um `ResourceDictionary` declarado no nível do aplicativo. Quando você fornece um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] para o assembly por meio de uma extensão `ThemeDictionary` em vez de um [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] direto, a lógica da extensão fornecerá lógica de invalidação que se aplica sempre que o tema do sistema for alterado.  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `ThemeDictionary` é atribuído como o valor <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> da classe de extensão subjacente <xref:System.Windows.ThemeDictionaryExtension>.  
  
 `ThemeDictionary` também pode ser usado na sintaxe de elemento de objeto. Nesse caso, especificando o valor de <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> propriedade é necessária.  
  
 `ThemeDictionary` também pode ser usado em um atributo detalhado que especifica a propriedade <xref:System.Windows.Markup.StaticExtension.Member%2A> como sendo o par propriedade=valor:  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 O uso detalhado geralmente é útil para as extensões que têm mais de uma propriedade configurável, ou caso algumas propriedades sejam opcionais. Como `ThemeDictionary` tem apenas uma propriedade configurável, que é necessária, esse uso detalhado não é típico.  
  
 No [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementação do processador, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.ThemeDictionaryExtension> classe.  
  
 `ThemeDictionary` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
