---
title: Passando um URI para o Windows Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
ms.openlocfilehash: d48c257941b8e40ce2670e08fc0ff23cb21e3e1c
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687795"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="4a358-102">Passando um URI para o Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="4a358-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="4a358-103">Os métodos de Windows Runtime só aceitam URIs absolutos.</span><span class="sxs-lookup"><span data-stu-id="4a358-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="4a358-104">Se você passar um URI relativo para um método Windows Runtime, uma <xref:System.ArgumentException> exceção será lançada.</span><span class="sxs-lookup"><span data-stu-id="4a358-104">If you pass a relative URI to a Windows Runtime method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="4a358-105">Aqui está o porquê: quando você usa o Windows Runtime no código .NET Framework, a <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe aparece como <xref:System.Uri?displayProperty=nameWithType> no IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4a358-105">Here's why: When you use the Windows Runtime in .NET Framework code, the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="4a358-106">A <xref:System.Uri?displayProperty=nameWithType> classe permite URIs relativos, mas a <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe não.</span><span class="sxs-lookup"><span data-stu-id="4a358-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the <xref:Windows.Foundation.Uri?displayProperty=nameWithType> class does not.</span></span> <span data-ttu-id="4a358-107">Isso também é verdadeiro para métodos que você expõe em componentes Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="4a358-107">This is also true for methods you expose in Windows Runtime Components.</span></span> <span data-ttu-id="4a358-108">Se seu componente expõe um método que usa um URI, a assinatura presente no código inclui <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a358-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4a358-109">No entanto, para os usuários do seu componente, a assinatura inclui <xref:Windows.Foundation.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4a358-109">However, to users of your component, the signature includes <xref:Windows.Foundation.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4a358-110">Os URIs enviados aos seus componentes devem ser absolutos.</span><span class="sxs-lookup"><span data-stu-id="4a358-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
<span data-ttu-id="4a358-111">Este tópico mostra como detectar URIs absolutos e como criar um URI desse tipo ao fazer referência a um recurso do pacote do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4a358-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="4a358-112">Detectando e usando um URI absoluto</span><span class="sxs-lookup"><span data-stu-id="4a358-112">Detecting and using an absolute URI</span></span>  
<span data-ttu-id="4a358-113">Use a <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> propriedade para garantir que um URI seja absoluto antes de passá-lo para o Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="4a358-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the Windows Runtime.</span></span> <span data-ttu-id="4a358-114">Usar essa propriedade é mais eficiente do que identificar e tratar a exceção <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="4a358-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="4a358-115">Usando um URI absoluto para um recurso no pacote do aplicativo</span><span class="sxs-lookup"><span data-stu-id="4a358-115">Using an absolute URI for a resource in the app package</span></span>  
<span data-ttu-id="4a358-116">Se quiser especificar um URI para um recurso presente no pacote do aplicativo, você pode usar o esquema `ms-appx` ou `ms-appx-web` para criar um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="4a358-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
<span data-ttu-id="4a358-117">O exemplo a seguir mostra como definir a <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> propriedade para um <xref:Windows.UI.Xaml.Controls.WebView> controle e a <xref:Windows.UI.Xaml.Controls.Image.Source%2A> propriedade de um <xref:Windows.UI.Xaml.Controls.Image> controle para recursos contidos em uma pasta chamada pages, usando XAML e código.</span><span class="sxs-lookup"><span data-stu-id="4a358-117">The following example shows how to set the <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> property for a <xref:Windows.UI.Xaml.Controls.WebView> control and the <xref:Windows.UI.Xaml.Controls.Image.Source%2A> property for an <xref:Windows.UI.Xaml.Controls.Image> control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
<span data-ttu-id="4a358-118">Para obter mais informações sobre esses esquemas, consulte [esquemas de URI](/windows/uwp/app-resources/uri-schemes) no centro de desenvolvimento do Windows.</span><span class="sxs-lookup"><span data-stu-id="4a358-118">For more information about these schemes, see [URI schemes](/windows/uwp/app-resources/uri-schemes) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a358-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="4a358-119">See also</span></span>

- [<span data-ttu-id="4a358-120">Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="4a358-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
