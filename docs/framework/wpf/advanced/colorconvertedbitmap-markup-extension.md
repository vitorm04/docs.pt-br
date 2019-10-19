---
title: Extensão de marcação ColorConvertedBitmap
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
ms.openlocfilehash: 7d14ddc6276b9dd7baee12e267e8af1250bc11ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582775"
---
# <a name="colorconvertedbitmap-markup-extension"></a>Extensão de marcação ColorConvertedBitmap
Fornece uma maneira de especificar uma origem de bitmap que não tem um perfil inserido. Os perfis/contextos de cor são especificados por URI, assim como o URI de origem da imagem.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`imageSource`|O URI do bitmap não perfilado.|  
|`sourceIIC`|O URI da configuração do perfil de origem.|  
|`destinationIIC`|O URI da configuração do perfil de destino|  
  
## <a name="remarks"></a>Comentários  
 Essa extensão de marcação destina-se a preencher um conjunto relacionado de valores de propriedade de origem de imagem, como <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.  
  
 A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação. `ColorConvertedBitmap` (ou `ColorConvertedBitmapExtension`) não pode ser usada na sintaxe do elemento de propriedade, porque os valores só podem ser definidos como valores no construtor inicial, que é a cadeia de caracteres após o identificador de extensão.  
  
 `ColorConvertedBitmap` é uma extensão da marcação. Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades. Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo. Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>
- [Extensões de marcação e XAML do WPF](markup-extensions-and-wpf-xaml.md)
- [Visão geral da geração de imagens](../graphics-multimedia/imaging-overview.md)
