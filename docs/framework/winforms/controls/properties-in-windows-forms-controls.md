---
title: Propriedades em controles dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525627"
---
# <a name="properties-in-windows-forms-controls"></a><span data-ttu-id="501b3-102">Propriedades em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="501b3-102">Properties in Windows Forms Controls</span></span>
<span data-ttu-id="501b3-103">Um controle dos Windows Forms herda muitas propriedades da classe base <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="501b3-103">A Windows Forms control inherits many properties form the base class <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="501b3-104">Estas incluem propriedades como <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>e muitos outros.</span><span class="sxs-lookup"><span data-stu-id="501b3-104">These include properties such as <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>, and many others.</span></span> <span data-ttu-id="501b3-105">Para obter detalhes sobre as propriedades herdadas, consulte <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="501b3-105">For details about inherited properties, see <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="501b3-106">Você pode substituir as propriedades herdadas em seu controle, bem como definir novas propriedades.</span><span class="sxs-lookup"><span data-stu-id="501b3-106">You can override inherited properties in your control as well as define new properties.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="501b3-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="501b3-107">In This Section</span></span>  
 [<span data-ttu-id="501b3-108">Definindo uma propriedade</span><span class="sxs-lookup"><span data-stu-id="501b3-108">Defining a Property</span></span>](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 <span data-ttu-id="501b3-109">Mostra como implementar uma propriedade para um controle personalizado ou componente e mostra como integrar a propriedade ambiente no de design.</span><span class="sxs-lookup"><span data-stu-id="501b3-109">Shows how to implement a property for a custom control or component and shows how to integrate the property into the design environment.</span></span>  
  
 [<span data-ttu-id="501b3-110">Definindo valores padrão com os métodos ShouldSerialize e Reset</span><span class="sxs-lookup"><span data-stu-id="501b3-110">Defining Default Values with the ShouldSerialize and Reset Methods</span></span>](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 <span data-ttu-id="501b3-111">Mostra como definir valores de propriedade padrão para um controle ou componente personalizado.</span><span class="sxs-lookup"><span data-stu-id="501b3-111">Shows how to define default property values for a custom control or component.</span></span>  
  
 [<span data-ttu-id="501b3-112">Eventos alterados por propriedade</span><span class="sxs-lookup"><span data-stu-id="501b3-112">Property-Changed Events</span></span>](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 <span data-ttu-id="501b3-113">Descreve como habilitar as notificações de alteração de propriedade quando um valor da propriedade for alterado.</span><span class="sxs-lookup"><span data-stu-id="501b3-113">Describes how to enable property-change notifications when a property value changes.</span></span>  
  
 [<span data-ttu-id="501b3-114">Como expor as propriedades de controles constituintes</span><span class="sxs-lookup"><span data-stu-id="501b3-114">How to: Expose Properties of Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 <span data-ttu-id="501b3-115">Mostra como expor as propriedades de controles constituintes em um controle de composição o personalizado.</span><span class="sxs-lookup"><span data-stu-id="501b3-115">Shows how to expose properties of constituent controls in a custom composite control.</span></span>  
  
 [<span data-ttu-id="501b3-116">Implementação do método em controles personalizados</span><span class="sxs-lookup"><span data-stu-id="501b3-116">Method Implementation in Custom Controls</span></span>](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 <span data-ttu-id="501b3-117">Descreve como implementar métodos de componentes e controles personalizados.</span><span class="sxs-lookup"><span data-stu-id="501b3-117">Describes how to implement methods in custom controls and components.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="501b3-118">Referência</span><span class="sxs-lookup"><span data-stu-id="501b3-118">Reference</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="501b3-119">Documenta a classe base para implementar controles de composição.</span><span class="sxs-lookup"><span data-stu-id="501b3-119">Documents the base class for implementing composite controls.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 <span data-ttu-id="501b3-120">Documenta o atributo que especifica o <xref:System.ComponentModel.TypeConverter> a ser usado para um tipo de propriedade personalizada.</span><span class="sxs-lookup"><span data-stu-id="501b3-120">Documents the attribute that specifies the <xref:System.ComponentModel.TypeConverter> to use for a custom property type.</span></span>  
  
 <xref:System.ComponentModel.EditorAttribute>  
 <span data-ttu-id="501b3-121">Documenta o atributo que especifica o <xref:System.Drawing.Design.UITypeEditor> a ser usado para uma propriedade personalizada.</span><span class="sxs-lookup"><span data-stu-id="501b3-121">Documents the attribute that specifies the <xref:System.Drawing.Design.UITypeEditor> to use for a custom property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="501b3-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="501b3-122">Related Sections</span></span>  
 [<span data-ttu-id="501b3-123">Atributos em controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="501b3-123">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 <span data-ttu-id="501b3-124">Descreve os atributos que você pode aplicar a propriedades ou outros membros de seus componentes e controles personalizados.</span><span class="sxs-lookup"><span data-stu-id="501b3-124">Describes the attributes you can apply to properties or other members of your custom controls and components.</span></span>  
  
 [<span data-ttu-id="501b3-125">Atributos de tempo de design para componentes</span><span class="sxs-lookup"><span data-stu-id="501b3-125">Design-Time Attributes for Components</span></span>](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 <span data-ttu-id="501b3-126">Lista atributos de metadados para aplicar a componentes e controles para que eles sejam exibidos corretamente em tempo de design em designers visuais.</span><span class="sxs-lookup"><span data-stu-id="501b3-126">Lists metadata attributes to apply to components and controls so that they are displayed correctly at design time in visual designers.</span></span>  
  
 [<span data-ttu-id="501b3-127">Estendendo o suporte ao tempo de design</span><span class="sxs-lookup"><span data-stu-id="501b3-127">Extending Design-Time Support</span></span>](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 <span data-ttu-id="501b3-128">Descreve como implementar classes como editores e designers que fornecem suporte ao tempo de design.</span><span class="sxs-lookup"><span data-stu-id="501b3-128">Describes how to implement classes such as editors and designers that provide design-time support.</span></span>
