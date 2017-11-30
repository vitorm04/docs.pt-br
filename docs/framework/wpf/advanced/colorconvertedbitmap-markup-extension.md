---
title: "Extensão de marcação ColorConvertedBitmap"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], ColorConvertedBitmap markup extension
- ColorConvertedBitmap markup extension [WPF]
ms.assetid: 18321c18-c898-4470-93fa-a702b47770c1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f1946ec2a5b607d9fce350da0676092d6e0407a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="colorconvertedbitmap-markup-extension"></a><span data-ttu-id="1caac-102">Extensão de marcação ColorConvertedBitmap</span><span class="sxs-lookup"><span data-stu-id="1caac-102">ColorConvertedBitmap Markup Extension</span></span>
<span data-ttu-id="1caac-103">Fornece uma maneira de especificar uma fonte de bitmap que não tenha um perfil inserido.</span><span class="sxs-lookup"><span data-stu-id="1caac-103">Provides a way to specify a bitmap source that does not have an embedded profile.</span></span> <span data-ttu-id="1caac-104">Contextos de cores / perfis são especificados por [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], pois é a origem da imagem [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1caac-104">Color contexts / profiles are specified by [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], as is the image source [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1caac-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="1caac-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{ColorConvertedBitmap imageSource sourceIIC destinationIIC}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1caac-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="1caac-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`imageSource`|<span data-ttu-id="1caac-107">O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] de bitmap sem perfil.</span><span class="sxs-lookup"><span data-stu-id="1caac-107">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the nonprofiled bitmap.</span></span>|  
|`sourceIIC`|<span data-ttu-id="1caac-108">O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] da configuração de perfil do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="1caac-108">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the source profile configuration.</span></span>|  
|`destinationIIC`|<span data-ttu-id="1caac-109">O [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] da configuração de perfil de destino</span><span class="sxs-lookup"><span data-stu-id="1caac-109">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] of the destination profile configuration</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1caac-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1caac-110">Remarks</span></span>  
 <span data-ttu-id="1caac-111">Esta extensão de marcação destina-se para preencher um conjunto relacionado de valores de propriedade de origem da imagem, como <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="1caac-111">This markup extension is intended to fill a related set of image-source property values such as <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>.</span></span>  
  
 <span data-ttu-id="1caac-112">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="1caac-112">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="1caac-113">`ColorConvertedBitmap`(ou `ColorConvertedBitmapExtension`) não pode ser usado na sintaxe de elemento de propriedade, porque os valores só podem ser definidos como valores no construtor inicial, que é a cadeia de caracteres após o identificador da extensão.</span><span class="sxs-lookup"><span data-stu-id="1caac-113">`ColorConvertedBitmap` (or `ColorConvertedBitmapExtension`) cannot be used in property element syntax, because the values can only be set as values on the initial constructor, which is the string following the extension identifier.</span></span>  
  
 <span data-ttu-id="1caac-114">`ColorConvertedBitmap` é uma extensão da marcação.</span><span class="sxs-lookup"><span data-stu-id="1caac-114">`ColorConvertedBitmap` is a markup extension.</span></span> <span data-ttu-id="1caac-115">Extensões de marcação são tipicamente implementadas quando existe um requisito que permite que valores de atributo sejam diferentes de valores literais ou nomes de manipuladores, e o requisito é mais global do que simplesmente colocar conversores de tipo em certos tipos ou propriedades.</span><span class="sxs-lookup"><span data-stu-id="1caac-115">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="1caac-116">Todas as extensões de marcação em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] usam os caracteres { e } na sintaxe de atributo, que é a convenção pela qual um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconhece que uma extensão de marcação deve processar o atributo.</span><span class="sxs-lookup"><span data-stu-id="1caac-116">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="1caac-117">Para obter mais informações, consulte [Extensões de marcação e XAML do WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1caac-117">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caac-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1caac-118">See Also</span></span>  
 <xref:System.Windows.Media.Imaging.BitmapImage.UriSource%2A>  
 [<span data-ttu-id="1caac-119">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="1caac-119">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="1caac-120">Visão geral da geração de imagens</span><span class="sxs-lookup"><span data-stu-id="1caac-120">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
