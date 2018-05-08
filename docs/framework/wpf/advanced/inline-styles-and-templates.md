---
title: Estilos e modelos embutidos
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: 9c06f61bce1e17770fa0a9b9ed7a0e20625a79ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="inline-styles-and-templates"></a>Estilos e modelos embutidos
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Fornece <xref:System.Windows.Style> objetos e objetos de modelo (<xref:System.Windows.FrameworkTemplate> subclasses) como uma maneira de definir a aparência visual de um elemento em recursos, para que elas podem ser usadas várias vezes. Por esse motivo, atributos no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que levam os tipos <xref:System.Windows.Style> e <xref:System.Windows.FrameworkTemplate> quase sempre fazem referências de recurso para modelos e estilos existentes em vez de definir novos in-line.  
  
## <a name="limitations-of-inline-styles-and-templates"></a>Limitações de estilos e modelos embutidos  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], as propriedades de estilo e modelo podem ser definidas tecnicamente de uma de duas maneiras. Você pode usar a sintaxe de atributo para fazer referência a um estilo que foi definido dentro de um recurso, por exemplo `<`*objeto*`Style="{StaticResource`*myResourceKey*`}" .../>`. Ou então, você pode usar a sintaxe de elemento da propriedade para definir um estilo embutido, por exemplo:  
  
 `<` *objeto* `>`  
  
 `<` *objeto* `.Style>`  
  
 `<` `Style`  `.../>`  
  
 `</` *objeto* `.Style>`  
  
 `</` *objeto* `>`  
  
 É muito mais comum usar o atributo. Um estilo que é definido embutido e não definido em recursos terá necessariamente escopos somente para o elemento que o contém, e não poderá ser reutilizado com tanta facilidade, pois não tem nenhuma chave de recurso. Em geral, um estilo definido por recurso é mais versátil e útil, e está mais alinhado com o princípio de modelo de programação [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] geral de lógica de programa no código de design na marcação.  
  
 Geralmente não haverá nenhum motivo para definir um estilo ou modelo embutido, mesmo se você pretender usar esse estilo ou modelo nesse local. A maioria dos elementos que podem assumir um estilo ou modelo também dão suporte a uma propriedade e um modelo de conteúdo. Se você estivesse usando uma árvore lógica criada por meio de estilos ou modelagem, seria ainda mais fácil preencher somente essa propriedade de conteúdo com os elementos filho equivalentes na marcação direta. Isso ignoraria totalmente os mecanismos de estilo e modelo.  
  
 Outras sintaxes habilitadas por extensões de marcação que retornam um objeto também são possíveis para os estilos e modelos. Essas extensões que têm possíveis cenários incluem [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) e <xref:System.Windows.Data.Binding>.  
  
## <a name="see-also"></a>Consulte também  
 [Estilo e modelagem](../../../../docs/framework/wpf/controls/styling-and-templating.md)
