---
title: Passando um URI para o Windows Runtime
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c489ec893ea335c8fafc904cf2a12162580ec266
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025429"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="03e90-102">Passando um URI para o Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="03e90-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="03e90-103">Os métodos de Tempo de Execução do Windows só aceitam URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="03e90-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="03e90-104">Se você passar um URI relativo a um método de tempo de execução do Windows, um <xref:System.ArgumentException> exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="03e90-104">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="03e90-105">Eis o porquê: Quando você usa o tempo de execução do Windows no código do .NET Framework, o <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe aparece como <xref:System.Uri?displayProperty=nameWithType> no Intellisense.</span><span class="sxs-lookup"><span data-stu-id="03e90-105">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="03e90-106">O <xref:System.Uri?displayProperty=nameWithType> classe permite que os URIs relativos, mas o <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe não faz.</span><span class="sxs-lookup"><span data-stu-id="03e90-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="03e90-107">Isso também é verdadeiro para métodos expostos nos componentes de tempo de execução do Windows.</span><span class="sxs-lookup"><span data-stu-id="03e90-107">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="03e90-108">Se seu componente expõe um método que usa um URI, a assinatura presente no código inclui <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="03e90-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="03e90-109">No entanto, para os usuários do seu componente, a assinatura inclui <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="03e90-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="03e90-110">Os URIs enviados aos seus componentes devem ser absolutos.</span><span class="sxs-lookup"><span data-stu-id="03e90-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="03e90-111">Este tópico mostra como detectar URIs absolutos e como criar um URI desse tipo ao fazer referência a um recurso do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="03e90-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="03e90-112">Detectando e usando um URI absoluto</span><span class="sxs-lookup"><span data-stu-id="03e90-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="03e90-113">Use o <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> propriedade para garantir que o URI é absoluto antes de passá-lo para o tempo de execução do Windows.</span><span class="sxs-lookup"><span data-stu-id="03e90-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="03e90-114">Usar essa propriedade é mais eficiente do que identificar e tratar a exceção <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="03e90-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="03e90-115">Usando um URI absoluto para um recurso no pacote do aplicativo</span><span class="sxs-lookup"><span data-stu-id="03e90-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="03e90-116">Se quiser especificar um URI para um recurso presente no pacote do aplicativo, você pode usar o esquema `ms-appx` ou `ms-appx-web` para criar um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="03e90-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="03e90-117">O exemplo a seguir mostra como definir a <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> propriedade para um <xref:Windows.UI.Xaml.Controls.WebView> controle e o <xref:Windows.UI.Xaml.Controls.Image.Source%2A> propriedade para um <xref:Windows.UI.Xaml.Controls.Image> controle aos recursos que estão contidos em uma pasta chamada páginas usando XAML e código.</span><span class="sxs-lookup"><span data-stu-id="03e90-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="03e90-118">Para obter mais informações sobre esses esquemas, consulte [esquemas URI](/windows/uwp/app-resources/uri-schemes) no Centro de desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="03e90-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e90-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03e90-119">See also</span></span>

- [<span data-ttu-id="03e90-120">Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="03e90-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
