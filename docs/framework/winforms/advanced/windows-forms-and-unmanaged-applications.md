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
ms.openlocfilehash: bc0c848d1c92871dacab93497c674645f3ac83fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463933"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="26d4c-102">Windows Forms e aplicativos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="26d4c-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="26d4c-103">Aplicativos do Windows Forms e controles podem interoperar com aplicativos não gerenciados, com algumas restrições.</span><span class="sxs-lookup"><span data-stu-id="26d4c-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="26d4c-104">As seções a seguir descrevem os cenários e as configurações com suporte em controles e aplicativos do Windows Forms e aqueles que não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="26d4c-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26d4c-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="26d4c-105">In This Section</span></span>  
 [<span data-ttu-id="26d4c-106">Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados</span><span class="sxs-lookup"><span data-stu-id="26d4c-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="26d4c-107">Oferece informações gerais sobre como usar e implementar controles de formulários do Windows que funcionam com aplicativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="26d4c-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="26d4c-108">Como dar suporte à interoperabilidade COM exibindo um Windows Form com o método ShowDialog</span><span class="sxs-lookup"><span data-stu-id="26d4c-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="26d4c-109">Fornece um exemplo de código que mostra como usar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para executar um formulário do Windows em um aplicativo não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="26d4c-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="26d4c-110">Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado</span><span class="sxs-lookup"><span data-stu-id="26d4c-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="26d4c-111">Fornece um exemplo de código que mostra como executar um formulário do Windows em seu próprio thread.</span><span class="sxs-lookup"><span data-stu-id="26d4c-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="26d4c-112">Consulte também [Instruções passo a passo: dando suporte à interoperabilidade COM exibindo cada Windows Form no próprio thread](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="26d4c-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="26d4c-113">Referência</span><span class="sxs-lookup"><span data-stu-id="26d4c-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="26d4c-114">Usado para criar um thread separado para um formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="26d4c-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="26d4c-115">Inicia um loop de mensagem para um thread.</span><span class="sxs-lookup"><span data-stu-id="26d4c-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="26d4c-116">Realiza marshaling de chamadas de um aplicativo não gerenciado a um formulário.</span><span class="sxs-lookup"><span data-stu-id="26d4c-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="26d4c-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="26d4c-117">Related Sections</span></span>  
 [<span data-ttu-id="26d4c-118">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="26d4c-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="26d4c-119">Oferece informações gerais sobre como usar tipos do .NET Framework em aplicativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="26d4c-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
