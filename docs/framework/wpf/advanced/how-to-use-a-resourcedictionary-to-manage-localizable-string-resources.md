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
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Como usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis
Este exemplo mostra como usar um <xref:System.Windows.ResourceDictionary> para recursos do pacote de cadeia de caracteres localizáveis para aplicativos do Windows Presentation Foundation (WPF).  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Para usar um ResourceDictionary para gerenciar recursos de cadeia de caracteres localizáveis  
  
1.  Criar um <xref:System.Windows.ResourceDictionary> que contém as cadeias de caracteres que você deseja localizar. O código a seguir mostra um exemplo.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Esse código define um recurso de cadeia de caracteres, `localizedMessage`, do tipo <xref:System.String>, do <xref:System> namespace em mscorlib.dll.  
  
2.  Adicionar o <xref:System.Windows.ResourceDictionary> para seu aplicativo, usando o código a seguir.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  Usar o recurso de cadeia de caracteres de marcação, usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] como a seguir.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  Use o recurso de cadeia de caracteres de code-behind, usando código semelhante ao seguinte.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  Localize o aplicativo. Para obter mais informações, consulte [localizar um aplicativo](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).
