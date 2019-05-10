---
title: 'Como: Criar um controle do Windows Forms que mostre o progresso'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 877df5139fd0e626cd2242e3790bc7100f6233aa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599335"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="ebc4b-102">Como: Criar um controle do Windows Forms que mostre o progresso</span><span class="sxs-lookup"><span data-stu-id="ebc4b-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="ebc4b-103">O exemplo de código a seguir mostra um controle personalizado chamado `FlashTrackBar` que pode ser usado para mostrar ao usuário o nível ou o andamento de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="ebc4b-104">Ele usa um gradiente para representar visualmente o progresso.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="ebc4b-105">O controle `FlashTrackBar` ilustra os seguintes conceitos:</span><span class="sxs-lookup"><span data-stu-id="ebc4b-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
- <span data-ttu-id="ebc4b-106">Definindo propriedades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-106">Defining custom properties.</span></span>  
  
- <span data-ttu-id="ebc4b-107">Definindo eventos personalizados.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-107">Defining custom events.</span></span> <span data-ttu-id="ebc4b-108">(`FlashTrackBar` define o evento `ValueChanged`.)</span><span class="sxs-lookup"><span data-stu-id="ebc4b-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
- <span data-ttu-id="ebc4b-109">Substituindo o <xref:System.Windows.Forms.Control.OnPaint%2A> método para fornecer a lógica para desenhar o controle.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
- <span data-ttu-id="ebc4b-110">Calculando a área disponível para desenhar o controle usando seu <xref:System.Windows.Forms.Control.ClientRectangle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="ebc4b-111">`FlashTrackBar` faz isso no seu método `OptimizedInvalidate`.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
- <span data-ttu-id="ebc4b-112">Implementação de serialização ou persistência em uma propriedade quando ela for alterada no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="ebc4b-113">`FlashTrackBar` define os métodos `ShouldSerializeStartColor` e `ShouldSerializeEndColor` para serializar suas propriedades `StartColor` e `EndColor`.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="ebc4b-114">A tabela a seguir mostra as propriedades personalizadas definidas por `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="ebc4b-115">Propriedade</span><span class="sxs-lookup"><span data-stu-id="ebc4b-115">Property</span></span>|<span data-ttu-id="ebc4b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebc4b-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="ebc4b-117">Indica se o usuário pode alterar o valor da barra de acompanhamento dinâmica clicando nela e arrastando-a.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="ebc4b-118">Especifica a cor final da barra de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="ebc4b-119">Especifica quanto a tela de fundo é escurecida em relação ao gradiente em primeiro plano.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="ebc4b-120">Especifica o valor máximo da barra de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="ebc4b-121">Especifica o valor mínimo da barra de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="ebc4b-122">Especifica a cor inicial do gradiente.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="ebc4b-123">Indica se um percentual deve ser exibido com relação ao gradiente.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="ebc4b-124">Indica se o valor atual deve ser exibido com relação ao gradiente.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="ebc4b-125">Indica se a barra de acompanhamento deve exibir um gradiente de cores mostrando o valor atual.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="ebc4b-126">Especifica o valor atual da barra de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="ebc4b-127">A tabela a seguir mostra os membros adicionais definidos pelo `FlashTrackBar:` o evento de propriedade alterada e o método que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="ebc4b-128">Membro</span><span class="sxs-lookup"><span data-stu-id="ebc4b-128">Member</span></span>|<span data-ttu-id="ebc4b-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="ebc4b-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="ebc4b-130">O evento que é gerado quando a propriedade `Value` da barra de acompanhamento é alterada.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="ebc4b-131">O método que gera o evento `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="ebc4b-132">`FlashTrackBar` usa o <xref:System.EventArgs> classe para dados de evento e <xref:System.EventHandler> para o delegado do evento.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="ebc4b-133">Para lidar com a correspondente *EventName* eventos, `FlashTrackBar` substitui os seguintes métodos herdados de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="ebc4b-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="ebc4b-134">Para manipular os eventos correspondentes da propriedade alterada, `FlashTrackBar` substitui os seguintes métodos herdados de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="ebc4b-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="ebc4b-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebc4b-135">Example</span></span>  
 <span data-ttu-id="ebc4b-136">O controle `FlashTrackBar` define dois editores de tipo de interface do usuário, `FlashTrackBarValueEditor` e `FlashTrackBarDarkenByEditor`, que são mostrados nas listagens de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="ebc4b-137">A classe `HostApp` usa o controle `FlashTrackBar` em um Windows Form.</span><span class="sxs-lookup"><span data-stu-id="ebc4b-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="ebc4b-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebc4b-138">See also</span></span>

- <span data-ttu-id="ebc4b-139">[Estendendo o suporte ao tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="ebc4b-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="ebc4b-140">Noções básicas sobre o desenvolvimento de controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ebc4b-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
