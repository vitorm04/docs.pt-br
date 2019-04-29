---
title: 'Como: Registrar uma propriedade anexada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 4c678a64b62b8f4db24cf39ffbafac52e56c9982
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768674"
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="96f38-102">Como: Registrar uma propriedade anexada</span><span class="sxs-lookup"><span data-stu-id="96f38-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="96f38-103">Este exemplo mostra como registrar uma propriedade anexada e fornecer acessadores públicos para que você possa usar a propriedade no [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e no código.</span><span class="sxs-lookup"><span data-stu-id="96f38-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="96f38-104">Propriedades anexadas são um conceito de sintaxe definido pelo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96f38-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="96f38-105">A maioria das propriedades anexadas para tipos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também são implementadas como propriedades de dependência.</span><span class="sxs-lookup"><span data-stu-id="96f38-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="96f38-106">Você pode usar as propriedades de dependência em qualquer <xref:System.Windows.DependencyObject> tipos.</span><span class="sxs-lookup"><span data-stu-id="96f38-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96f38-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96f38-107">Example</span></span>  
 <span data-ttu-id="96f38-108">O exemplo a seguir mostra como registrar uma propriedade anexada como uma propriedade de dependência, usando o <xref:System.Windows.DependencyProperty.RegisterAttached%2A> método.</span><span class="sxs-lookup"><span data-stu-id="96f38-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="96f38-109">A classe de provedor tem a opção de fornecer metadados padrão para a propriedade é aplicável quando a propriedade é usada em outra classe, a menos que essa classe substitua os metadados.</span><span class="sxs-lookup"><span data-stu-id="96f38-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="96f38-110">Neste exemplo, o valor padrão da propriedade `IsBubbleSource` está definido como `false`.</span><span class="sxs-lookup"><span data-stu-id="96f38-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="96f38-111">A classe de provedor para uma propriedade anexada (mesmo se não estiver registrada como uma propriedade de dependência) deve fornecer acessadores get e set estáticos que sigam a convenção de nomenclatura `Set` *[AttachedPropertyName]* e `Get` *[AttachedPropertyName]*.</span><span class="sxs-lookup"><span data-stu-id="96f38-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="96f38-112">Esses acessadores são necessários para que o leitor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] em execução possa reconhecer a propriedade como um atributo em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e resolver os tipos apropriados.</span><span class="sxs-lookup"><span data-stu-id="96f38-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="96f38-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96f38-113">See also</span></span>

- <xref:System.Windows.DependencyProperty>
- [<span data-ttu-id="96f38-114">Visão geral das propriedades da dependência</span><span class="sxs-lookup"><span data-stu-id="96f38-114">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="96f38-115">Propriedades de dependência personalizada</span><span class="sxs-lookup"><span data-stu-id="96f38-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="96f38-116">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="96f38-116">How-to Topics</span></span>](properties-how-to-topics.md)
