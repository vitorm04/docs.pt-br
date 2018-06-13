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
# <a name="presentationoptionsfreeze-attribute"></a><span data-ttu-id="4dc7e-102">Atributo PresentationOptions:Freeze</span><span class="sxs-lookup"><span data-stu-id="4dc7e-102">PresentationOptions:Freeze Attribute</span></span>
<span data-ttu-id="4dc7e-103">Conjuntos de <xref:System.Windows.Freezable.IsFrozen%2A> estado para `true` em que o contém <xref:System.Windows.Freezable> elemento.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-103">Sets the <xref:System.Windows.Freezable.IsFrozen%2A> state to `true` on the containing <xref:System.Windows.Freezable> element.</span></span> <span data-ttu-id="4dc7e-104">Comportamento padrão para um <xref:System.Windows.Freezable> sem o `PresentationOptions:Freeze` atributo especificado é que <xref:System.Windows.Freezable.IsFrozen%2A> é `false` em tempo de carregamento e dependente geral <xref:System.Windows.Freezable> comportamento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-104">Default behavior for a <xref:System.Windows.Freezable> without the `PresentationOptions:Freeze` attribute specified is that <xref:System.Windows.Freezable.IsFrozen%2A> is `false` at load time, and dependent on general <xref:System.Windows.Freezable> behavior at runtime.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4dc7e-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="4dc7e-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4dc7e-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="4dc7e-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`PresentationOptions`|<span data-ttu-id="4dc7e-107">Um prefixo de namespace de XML, que pode ser qualquer cadeia de caracteres de prefixo válida, conforme a especificação XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-107">An XML namespace prefix, which can be any valid prefix string, per the XML 1.0 specification.</span></span> <span data-ttu-id="4dc7e-108">O prefixo `PresentationOptions` é usado para fins de identificação nesta documentação.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-108">The prefix `PresentationOptions` is used for identification purposes in this documentation.</span></span>|  
|`freezableElement`|<span data-ttu-id="4dc7e-109">Um elemento que instancia qualquer classe derivada de <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-109">An element that instantiates any derived class of <xref:System.Windows.Freezable>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dc7e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4dc7e-110">Remarks</span></span>  
 <span data-ttu-id="4dc7e-111">O atributo `Freeze` é o único atributo ou elemento de programação definido no namespace de XML de `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-111">The `Freeze` attribute is the only attribute or other programming element defined in the `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML namespace.</span></span> <span data-ttu-id="4dc7e-112">O atributo `Freeze` existe nesse namespace especial especificamente para que ele possa ser designado como ignorável, usando [Atributo mc:Ignorable](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) como parte das declarações do elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-112">The `Freeze` attribute exists in this special namespace specifically so that it can be designated as ignorable, using [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) as part of the root element declarations.</span></span> <span data-ttu-id="4dc7e-113">O motivo que `Freeze` deve poder ser ignorável é que nem todos os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementações de processador são capazes de congelar uma <xref:System.Windows.Freezable> no tempo de carregamento; esse recurso não é parte do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] especificação.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-113">The reason that `Freeze` must be able to be ignorable is because not all [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementations are able to freeze a <xref:System.Windows.Freezable> at load time; this capability is not part of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] specification.</span></span>  
  
 <span data-ttu-id="4dc7e-114">A capacidade de processar o atributo `Freeze` é especificamente interna ao processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que processa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para aplicativos compilados.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-114">The ability to process the `Freeze` attribute is specifically built in to the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that processes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for compiled applications.</span></span> <span data-ttu-id="4dc7e-115">O atributo não tem suporte em nenhuma classe e a sintaxe de atributo não é extensível ou modificável.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-115">The attribute is not supported by any class, and the attribute syntax is not extensible or modifiable.</span></span> <span data-ttu-id="4dc7e-116">Se você estiver implementando seu próprio [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador que você pode optar por paralelo o comportamento de congelamento do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador ao processar o `Freeze` atributo no <xref:System.Windows.Freezable> elementos no tempo de carregamento.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-116">If you are implementing your own [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor you can choose to parallel the freezing behavior of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor when processing the `Freeze` attribute on <xref:System.Windows.Freezable> elements at load time.</span></span>  
  
 <span data-ttu-id="4dc7e-117">Qualquer valor para o atributo `Freeze` diferente de `true` (não diferencia maiúsculas e minúsculas) gera um erro de tempo de carga.</span><span class="sxs-lookup"><span data-stu-id="4dc7e-117">Any value for the `Freeze` attribute other than `true` (not case sensitive) generates a load time error.</span></span> <span data-ttu-id="4dc7e-118">(Especificar o atributo `Freeze` como `false` não é um erro, porém esse já é o padrão, por isso a configuração para `false` não faz nada).</span><span class="sxs-lookup"><span data-stu-id="4dc7e-118">(Specifying the `Freeze` attribute as `false` is not an error, but that is already the default, so setting to `false` does nothing).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc7e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dc7e-119">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 [<span data-ttu-id="4dc7e-120">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="4dc7e-120">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="4dc7e-121">Atributo mc:Ignorable</span><span class="sxs-lookup"><span data-stu-id="4dc7e-121">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
