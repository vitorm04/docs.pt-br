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
ms.openlocfilehash: 2ba3a31d1fe8efde436fd76f88ccfab2853df5ee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377131"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a><span data-ttu-id="d48a2-102">Como: Persistir e restaurar propriedades de escopo do aplicativo em sessões de aplicativo</span><span class="sxs-lookup"><span data-stu-id="d48a2-102">How to: Persist and Restore Application-Scope Properties Across Application Sessions</span></span>
<span data-ttu-id="d48a2-103">Este exemplo mostra como persistir as propriedades de escopo do aplicativo quando um aplicativo é desligado, e como restaurar propriedades de escopo do aplicativo quando um aplicativo é próxima iniciar.</span><span class="sxs-lookup"><span data-stu-id="d48a2-103">This example shows how to persist application-scope properties when an application shuts down, and how to restore application-scope properties when an application is next launch.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d48a2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d48a2-104">Example</span></span>  
 <span data-ttu-id="d48a2-105">O aplicativo persiste as propriedades do escopo do aplicativo e restaura-los do armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="d48a2-105">The application persists application-scope properties to, and restores them from, isolated storage.</span></span> <span data-ttu-id="d48a2-106">Armazenamento isolado é uma área de armazenamento protegido que pode ser usada com segurança por aplicativos sem permissão de acesso de arquivo.</span><span class="sxs-lookup"><span data-stu-id="d48a2-106">Isolated storage is a protected storage area that can safely be used by applications without file access permission.</span></span>  <span data-ttu-id="d48a2-107">O *App. XAML* arquivo define a `App_Startup` método como o manipulador para o <xref:System.Windows.Application.Startup?displayProperty=nameWithType> evento e o `App_Exit` método como o manipulador para o <xref:System.Windows.Application.Exit?displayProperty=nameWithType> evento, conforme mostrado nas linhas realçadas do primeiro exemplo.</span><span class="sxs-lookup"><span data-stu-id="d48a2-107">The *App.xaml* file defines the `App_Startup` method as the handler for the <xref:System.Windows.Application.Startup?displayProperty=nameWithType> event, and the `App_Exit` method as the handler for the  <xref:System.Windows.Application.Exit?displayProperty=nameWithType> event, as shown in the highlighted lines of the first example.</span></span> <span data-ttu-id="d48a2-108">O segundo exemplo mostra uma parte do *App.xaml.cs* e *VB* arquivos que destaca o código para o `App_Startup` método, que restaura as propriedades de escopo do aplicativo e o `App_Exit` método, que salva as propriedades de escopo do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d48a2-108">The second example shows a portion of the *App.xaml.cs* and *App.xaml.vb* files that highlights the code for the `App_Startup` method, which restores application-scope properties, and the `App_Exit` method, which saves application-scope properties.</span></span>
 
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
 
