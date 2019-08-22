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
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="42bb0-102">Como: Persistir e restaurar propriedades de escopo do aplicativo em sessões de aplicativo</span><span class="sxs-lookup"><span data-stu-id="42bb0-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="42bb0-103">Este exemplo mostra como persistir Propriedades de escopo de aplicativo quando um aplicativo é desligado e como restaurar Propriedades de escopo de aplicativo quando um aplicativo é iniciado na próxima vez.</span><span class="sxs-lookup"><span data-stu-id="42bb0-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42bb0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="42bb0-104">Example</span></span>  
 <span data-ttu-id="42bb0-105">O aplicativo persiste Propriedades de escopo de aplicativo para e as restaura do armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="42bb0-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="42bb0-106">O armazenamento isolado é uma área de armazenamento protegida que pode ser usada com segurança por aplicativos sem permissão de acesso ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="42bb0-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="42bb0-107">O arquivo *app. XAML* define o `App_Startup` método como o manipulador para o <xref:System.Windows.Application.Startup?displayProperty=nameWithType> evento e o `App_Exit` método como o manipulador para o <xref:System.Windows.Application.Exit?displayProperty=nameWithType> evento, conforme mostrado nas linhas realçadas do primeiro exemplo.</span><span class="sxs-lookup"><span data-stu-id="42bb0-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="42bb0-108">O segundo exemplo mostra uma parte dos arquivos *app.XAML.cs* e *app. XAML. vb* que realça o código para o `App_Startup` método, que restaura as propriedades do escopo do aplicativo e o `App_Exit` método, que salva o escopo do aplicativo Properties.</span><span class="sxs-lookup"><span data-stu-id="42bb0-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb?highlight=14-45)]
