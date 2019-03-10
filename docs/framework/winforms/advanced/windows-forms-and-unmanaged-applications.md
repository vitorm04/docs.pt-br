---
title: Windows Forms e aplicativos não gerenciados
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 65465f22b1806d385523c894cce2103afe33c2f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702653"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="db26b-102">Windows Forms e aplicativos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="db26b-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="db26b-103">Aplicativos do Windows Forms e controles podem interoperar com aplicativos não gerenciados, com algumas restrições.</span><span class="sxs-lookup"><span data-stu-id="db26b-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="db26b-104">As seções a seguir descrevem os cenários e as configurações com suporte em controles e aplicativos do Windows Forms e aqueles que não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="db26b-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db26b-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="db26b-105">In This Section</span></span>  
 [<span data-ttu-id="db26b-106">Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados</span><span class="sxs-lookup"><span data-stu-id="db26b-106">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="db26b-107">Oferece informações gerais sobre como usar e implementar controles de formulários do Windows que funcionam com aplicativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="db26b-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="db26b-108">Como: Dar suporte à interoperabilidade com exibindo um formulário do Windows com o método ShowDialog</span><span class="sxs-lookup"><span data-stu-id="db26b-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="db26b-109">Fornece um exemplo de código que mostra como usar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para executar um formulário do Windows em um aplicativo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="db26b-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="db26b-110">Como: Dar suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread</span><span class="sxs-lookup"><span data-stu-id="db26b-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="db26b-111">Fornece um exemplo de código que mostra como executar um formulário do Windows em seu próprio thread.</span><span class="sxs-lookup"><span data-stu-id="db26b-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="db26b-112">Consulte também [passo a passo: Dando suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="db26b-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="db26b-113">Referência</span><span class="sxs-lookup"><span data-stu-id="db26b-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="db26b-114">Usado para criar um thread separado para um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="db26b-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="db26b-115">Inicia um loop de mensagem para um thread.</span><span class="sxs-lookup"><span data-stu-id="db26b-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="db26b-116">Realiza marshaling de chamadas de um aplicativo não gerenciado a um formulário.</span><span class="sxs-lookup"><span data-stu-id="db26b-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="db26b-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="db26b-117">Related Sections</span></span>  
 [<span data-ttu-id="db26b-118">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="db26b-118">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="db26b-119">Oferece informações gerais sobre como usar tipos do .NET Framework em aplicativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="db26b-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
