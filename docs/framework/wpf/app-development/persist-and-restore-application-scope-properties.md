---
title: 'Como: Persistir e restaurar propriedades de escopo do aplicativo em sessões de aplicativo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: d9c2dda2745e7528902b6b1c4f46d17264d1a8d8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666722"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>Como: Persistir e restaurar propriedades de escopo do aplicativo em sessões de aplicativo
Este exemplo mostra como persistir Propriedades de escopo de aplicativo quando um aplicativo é desligado e como restaurar Propriedades de escopo de aplicativo quando um aplicativo é iniciado na próxima vez.  
  
## <a name="example"></a>Exemplo  
 O aplicativo persiste Propriedades de escopo de aplicativo para e as restaura do armazenamento isolado. O armazenamento isolado é uma área de armazenamento protegida que pode ser usada com segurança por aplicativos sem permissão de acesso ao arquivo.  O arquivo *app. XAML* define o `App_Startup` método como o manipulador para o <xref:System.Windows.Application.Startup?displayProperty=nameWithType> evento e o `App_Exit` método como o manipulador para o <xref:System.Windows.Application.Exit?displayProperty=nameWithType> evento, conforme mostrado nas linhas realçadas do primeiro exemplo. O segundo exemplo mostra uma parte dos arquivos *app.XAML.cs* e *app. XAML. vb* que realça o código para o `App_Startup` método, que restaura as propriedades do escopo do aplicativo e o `App_Exit` método, que salva o escopo do aplicativo Properties.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
