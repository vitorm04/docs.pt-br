---
title: Como usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: 76ff3f688b5d3e7122254990076edb21fe6ae119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544492"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="0e722-102">Como usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis</span><span class="sxs-lookup"><span data-stu-id="0e722-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="0e722-103">Este exemplo mostra como usar um <xref:System.Windows.ResourceDictionary> para recursos do pacote de cadeia de caracteres localizáveis para aplicativos do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="0e722-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="0e722-104">Para usar um ResourceDictionary para gerenciar recursos de cadeia de caracteres localizáveis</span><span class="sxs-lookup"><span data-stu-id="0e722-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="0e722-105">Criar um <xref:System.Windows.ResourceDictionary> que contém as cadeias de caracteres que você deseja localizar.</span><span class="sxs-lookup"><span data-stu-id="0e722-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="0e722-106">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="0e722-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="0e722-107">Esse código define um recurso de cadeia de caracteres, `localizedMessage`, do tipo <xref:System.String>, do <xref:System> namespace em mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="0e722-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="0e722-108">Adicionar o <xref:System.Windows.ResourceDictionary> para seu aplicativo, usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="0e722-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="0e722-109">Usar o recurso de cadeia de caracteres de marcação, usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como a seguir.</span><span class="sxs-lookup"><span data-stu-id="0e722-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="0e722-110">Use o recurso de cadeia de caracteres de code-behind, usando código semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="0e722-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="0e722-111">Localize o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0e722-111">Localize the application.</span></span> <span data-ttu-id="0e722-112">Para obter mais informações, consulte [localizar um aplicativo](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="0e722-112">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>
