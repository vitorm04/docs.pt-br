---
title: Passando um URI para o Windows Runtime
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 78ba02fa227bd5c10337da0ef8b65ceab476c1ed
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="fe810-102">Passando um URI para o Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="fe810-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="fe810-103">Os métodos de Tempo de Execução do Windows só aceitam URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="fe810-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="fe810-104">Se você apresentar um URI relativo a um método [!INCLUDE[wrt](../../../includes/wrt-md.md)], será lançada uma exceção <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="fe810-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="fe810-105">Eis o porquê: quando você usa o [!INCLUDE[wrt](../../../includes/wrt-md.md)] no código do .NET Framework, o [Windows](http://go.microsoft.com/fwlink/p/?LinkId=238376) classe aparece como <xref:System.Uri?displayProperty=nameWithType> no Intellisense.</span><span class="sxs-lookup"><span data-stu-id="fe810-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="fe810-106">O <xref:System.Uri?displayProperty=nameWithType> classe permite que os URIs relativos, mas o [Windows](http://go.microsoft.com/fwlink/p/?LinkId=238376) classe não.</span><span class="sxs-lookup"><span data-stu-id="fe810-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class does not.</span></span> <span data-ttu-id="fe810-107">Isso também vale para métodos expostos nos componentes do [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe810-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="fe810-108">Se seu componente expõe um método que usa um URI, a assinatura presente no código inclui <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe810-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fe810-109">No entanto, para os usuários do seu componente, a assinatura inclui [Windows](http://go.microsoft.com/fwlink/p/?LinkId=238376).</span><span class="sxs-lookup"><span data-stu-id="fe810-109">However, to users of your component, the signature includes [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376).</span></span> <span data-ttu-id="fe810-110">Os URIs enviados aos seus componentes devem ser absolutos.</span><span class="sxs-lookup"><span data-stu-id="fe810-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
 <span data-ttu-id="fe810-111">Este tópico mostra como detectar URIs absolutos e como criar um URI desse tipo ao fazer referência a um recurso do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fe810-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="fe810-112">Detectando e usando um URI absoluto</span><span class="sxs-lookup"><span data-stu-id="fe810-112">Detecting and using an absolute URI</span></span>  
 <span data-ttu-id="fe810-113">Use a propriedade <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> para verificar se o URI é absoluto antes de apresentá-lo a [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe810-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="fe810-114">Usar essa propriedade é mais eficiente do que identificar e tratar a exceção <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="fe810-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="fe810-115">Usando um URI absoluto para um recurso no pacote do aplicativo</span><span class="sxs-lookup"><span data-stu-id="fe810-115">Using an absolute URI for a resource in the app package</span></span>  
 <span data-ttu-id="fe810-116">Se quiser especificar um URI para um recurso presente no pacote do aplicativo, você pode usar o esquema `ms-appx` ou `ms-appx-web` para criar um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="fe810-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
 <span data-ttu-id="fe810-117">O exemplo a seguir mostra como definir o [fonte](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) propriedade para um [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) controle e o [fonte](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) propriedade para um [imagem](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) controle para recursos que estão contidos em uma pasta denominada páginas usando XAML e código.</span><span class="sxs-lookup"><span data-stu-id="fe810-117">The following example shows how to set the [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) property for a [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) control and the [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) property for an [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 <span data-ttu-id="fe810-118">Para obter mais informações sobre esses esquemas, consulte [esquemas URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) no Centro de desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="fe810-118">For more information about these schemes, see [URI schemes](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe810-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe810-119">See Also</span></span>  
 [<span data-ttu-id="fe810-120">Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="fe810-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
