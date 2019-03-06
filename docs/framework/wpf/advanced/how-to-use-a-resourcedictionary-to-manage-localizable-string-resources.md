---
title: 'Como: Usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis'
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
ms.openlocfilehash: e28086d8c97070b854ebdea35fe347c64c5cd7ac
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377931"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="ca3cb-102">Como: Usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis</span><span class="sxs-lookup"><span data-stu-id="ca3cb-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="ca3cb-103">Este exemplo mostra como usar um <xref:System.Windows.ResourceDictionary> para recursos de cadeia de caracteres localizáveis do pacote para aplicativos do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ca3cb-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for Windows Presentation Foundation (WPF) applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="ca3cb-104">Para usar um ResourceDictionary para gerenciar recursos de cadeia de caracteres localizáveis</span><span class="sxs-lookup"><span data-stu-id="ca3cb-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="ca3cb-105">Criar um <xref:System.Windows.ResourceDictionary> que contém as cadeias de caracteres que você deseja localizar.</span><span class="sxs-lookup"><span data-stu-id="ca3cb-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="ca3cb-106">O código a seguir mostra um exemplo.</span><span class="sxs-lookup"><span data-stu-id="ca3cb-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="ca3cb-107">Esse código define um recurso de cadeia de caracteres `localizedMessage`, do tipo <xref:System.String>, da <xref:System> namespace em mscorlib. dll.</span><span class="sxs-lookup"><span data-stu-id="ca3cb-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="ca3cb-108">Adicionar o <xref:System.Windows.ResourceDictionary> ao seu aplicativo, usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca3cb-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="ca3cb-109">Usar o recurso de cadeia de caracteres de marcação, usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="ca3cb-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="ca3cb-110">Use o recurso de cadeia de caracteres de code-behind, usando código semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="ca3cb-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="ca3cb-111">Localize o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ca3cb-111">Localize the application.</span></span> <span data-ttu-id="ca3cb-112">Para obter mais informações, consulte [localizar um aplicativo](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="ca3cb-112">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>
