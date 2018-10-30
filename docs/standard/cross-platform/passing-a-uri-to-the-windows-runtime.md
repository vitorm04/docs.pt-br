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
ms.openlocfilehash: c5ce0d4ac2b95dc4d51e785e3a00026f56c13d2c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220701"
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Passando um URI para o Windows Runtime
Os métodos de Tempo de Execução do Windows só aceitam URIs absolutos. Se você apresentar um URI relativo a um método [!INCLUDE[wrt](../../../includes/wrt-md.md)], será lançada uma exceção <xref:System.ArgumentException>. Eis o porquê: quando você usa o [!INCLUDE[wrt](../../../includes/wrt-md.md)] no código do .NET Framework, o <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe aparece como <xref:System.Uri?displayProperty=nameWithType> no Intellisense. O <xref:System.Uri?displayProperty=nameWithType> classe permite que os URIs relativos, mas o <xref:Windows.Foundation.Uri?displayProperty=nameWithType> classe não faz. Isso também vale para métodos expostos nos componentes do [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Se seu componente expõe um método que usa um URI, a assinatura presente no código inclui <xref:System.Uri?displayProperty=nameWithType>. No entanto, para os usuários do seu componente, a assinatura inclui <xref:Windows.Foundation.Uri?displayProperty=nameWithType>. Os URIs enviados aos seus componentes devem ser absolutos.  
  
Este tópico mostra como detectar URIs absolutos e como criar um URI desse tipo ao fazer referência a um recurso do pacote do aplicativo.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Detectando e usando um URI absoluto  
Use a propriedade <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> para verificar se o URI é absoluto antes de apresentá-lo a [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Usar essa propriedade é mais eficiente do que identificar e tratar a exceção <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Usando um URI absoluto para um recurso no pacote do aplicativo  
Se quiser especificar um URI para um recurso presente no pacote do aplicativo, você pode usar o esquema `ms-appx` ou `ms-appx-web` para criar um URI absoluto.  
  
O exemplo a seguir mostra como definir a <xref:Windows.UI.Xaml.Controls.WebView.Source%2A> propriedade para um <xref:Windows.UI.Xaml.Controls.WebView> controle e o <xref:Windows.UI.Xaml.Controls.Image.Source%2A> propriedade para um <xref:Windows.UI.Xaml.Controls.Image> controle aos recursos que estão contidos em uma pasta chamada páginas usando XAML e código.  
  
[!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
Para obter mais informações sobre esses esquemas, consulte [esquemas URI](/windows/uwp/app-resources/uri-schemes) no Centro de desenvolvimento do Windows.  
  
## <a name="see-also"></a>Consulte também

- [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
