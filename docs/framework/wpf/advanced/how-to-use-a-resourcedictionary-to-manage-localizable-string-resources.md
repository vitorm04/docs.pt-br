---
title: "Como usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fba115ea8c954da177afcacbf679f41474e2b68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Como usar um ResourceDictionary para gerenciar recursos da cadeia de caracteres localizáveis
Este exemplo mostra como usar um <xref:System.Windows.ResourceDictionary> para recursos de cadeia de caracteres localizáveis do pacote para [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplicativos.  
  
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
