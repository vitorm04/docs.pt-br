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
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Como: Usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis
Este exemplo mostra como usar um <xref:System.Windows.ResourceDictionary> para recursos de cadeia de caracteres localizáveis do pacote para aplicativos do Windows Presentation Foundation (WPF).  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Para usar um ResourceDictionary para gerenciar recursos de cadeia de caracteres localizáveis  
  
1.  Criar um <xref:System.Windows.ResourceDictionary> que contém as cadeias de caracteres que você deseja localizar. O código a seguir mostra um exemplo.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Esse código define um recurso de cadeia de caracteres `localizedMessage`, do tipo <xref:System.String>, da <xref:System> namespace em mscorlib. dll.  
  
2.  Adicionar o <xref:System.Windows.ResourceDictionary> ao seu aplicativo, usando o código a seguir.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  Usar o recurso de cadeia de caracteres de marcação, usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] semelhante ao seguinte.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  Use o recurso de cadeia de caracteres de code-behind, usando código semelhante ao seguinte.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  Localize o aplicativo. Para obter mais informações, consulte [localizar um aplicativo](how-to-localize-an-application.md).
