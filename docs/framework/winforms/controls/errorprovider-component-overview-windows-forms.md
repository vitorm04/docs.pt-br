---
title: "Visão geral do componente ErrorProvider (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 589735156ad4d6d639c2449d6bd693e2b3a32d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="errorprovider-component-overview-windows-forms"></a><span data-ttu-id="252d0-102">Visão geral do componente ErrorProvider (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="252d0-102">ErrorProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="252d0-103">O componente [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) dos Windows Forms é usado para validar a entrada do usuário em um formulário ou controle.</span><span class="sxs-lookup"><span data-stu-id="252d0-103">The Windows Forms [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) component is used to validate user input on a form or control.</span></span> <span data-ttu-id="252d0-104">Ele é normalmente usado junto com a validação de entrada do usuário em um formulário ou para exibir erros dentro de um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="252d0-104">It is typically used in conjunction with validating user input on a form, or displaying errors within a dataset.</span></span> <span data-ttu-id="252d0-105">Um provedor de erro é uma alternativa melhor que exibir uma mensagem de erro em uma caixa de mensagem, pois depois que uma caixa de mensagem for descartada, a mensagem de erro não estará mais visível.</span><span class="sxs-lookup"><span data-stu-id="252d0-105">An error provider is a better alternative than displaying an error message in a message box, because once a message box is dismissed, the error message is no longer visible.</span></span> <span data-ttu-id="252d0-106">O <xref:System.Windows.Forms.ErrorProvider> componente exibe um ícone de erro (![ErrorProvider ícone](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) próximas ao controle relevante, como uma caixa de texto quando o usuário posiciona o ponteiro do mouse sobre o ícone de erro, uma dica de ferramenta aparecerá, mostrando a cadeia de caracteres de mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="252d0-106">The <xref:System.Windows.Forms.ErrorProvider> component displays an error icon (![ErrorProvider icon](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) next to the relevant control, such as a text box; when the user positions the mouse pointer over the error icon, a ToolTip appears, showing the error message string.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="252d0-107">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="252d0-107">Key Properties</span></span>  
 <span data-ttu-id="252d0-108">O <xref:System.Windows.Forms.ErrorProvider> são propriedades de chave do componente <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, e <xref:System.Windows.Forms.ErrorProvider.Icon%2A>.</span><span class="sxs-lookup"><span data-stu-id="252d0-108">The <xref:System.Windows.Forms.ErrorProvider> component's key properties are <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, and <xref:System.Windows.Forms.ErrorProvider.Icon%2A>.</span></span> <span data-ttu-id="252d0-109">Ao usar <xref:System.Windows.Forms.ErrorProvider> componente com controles de associação de dados, o <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriedade deve ser definida para o recipiente apropriado (geralmente o formulário do Windows) para o componente Exibir um ícone de erro no formulário.</span><span class="sxs-lookup"><span data-stu-id="252d0-109">When using <xref:System.Windows.Forms.ErrorProvider> component with data-bound controls, the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property must be set to the appropriate container (usually the Windows Form) in order for the component to display an error icon on the form.</span></span> <span data-ttu-id="252d0-110">Quando o componente é adicionado no designer, o <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> propriedade é definida como o formulário contém; se você adicionar o controle no código, você deve configurá-lo por conta própria.</span><span class="sxs-lookup"><span data-stu-id="252d0-110">When the component is added in the designer, the <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> property is set to the containing form; if you add the control in code, you must set it yourself.</span></span>  
  
 <span data-ttu-id="252d0-111">O <xref:System.Windows.Forms.ErrorProvider.Icon%2A> propriedade pode ser definida para um ícone de erro personalizada em vez do padrão.</span><span class="sxs-lookup"><span data-stu-id="252d0-111">The <xref:System.Windows.Forms.ErrorProvider.Icon%2A> property can be set to a custom error icon instead of the default.</span></span> <span data-ttu-id="252d0-112">Quando o <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> propriedade for definida, o <xref:System.Windows.Forms.ErrorProvider> componente pode exibir mensagens de erro para um conjunto de dados.</span><span class="sxs-lookup"><span data-stu-id="252d0-112">When the <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> property is set, the <xref:System.Windows.Forms.ErrorProvider> component can display error messages for a dataset.</span></span> <span data-ttu-id="252d0-113">O método de chave de <xref:System.Windows.Forms.ErrorProvider> componente é o <xref:System.Windows.Forms.ErrorProvider.SetError%2A> método, que especifica a cadeia de caracteres de mensagem de erro e onde o ícone de erro deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="252d0-113">The key method of the <xref:System.Windows.Forms.ErrorProvider> component is the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method, which specifies the error message string and where the error icon should appear.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="252d0-114">O <xref:System.Windows.Forms.ErrorProvider> componente não fornece suporte interno para clientes de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="252d0-114">The <xref:System.Windows.Forms.ErrorProvider> component does not provide built-in support for accessibility clients.</span></span> <span data-ttu-id="252d0-115">Para tornar seu aplicativo acessível ao usar esse componente, você deve fornecer um mecanismo de comentários acessível adicional.</span><span class="sxs-lookup"><span data-stu-id="252d0-115">To make your application accessible when using this component, you must provide an additional, accessible feedback mechanism.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="252d0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="252d0-116">See Also</span></span>  
 <xref:System.Windows.Forms.ErrorProvider>  
 [<span data-ttu-id="252d0-117">Como exibir erros dentro de um DataSet com o componente ErrorProvider dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="252d0-117">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [<span data-ttu-id="252d0-118">Como exibir ícones de erro para validação do formulário com o componente ErrorProvider dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="252d0-118">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
