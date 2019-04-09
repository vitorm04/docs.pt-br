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
ms.openlocfilehash: 99b04060d4e7c14313655010dc4fbd5ce1c90487
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134947"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>Como: Persistir e restaurar propriedades de escopo do aplicativo em sessões de aplicativo
Este exemplo mostra como persistir as propriedades de escopo do aplicativo quando um aplicativo é desligado, e como restaurar propriedades de escopo do aplicativo quando um aplicativo é próxima iniciar.  
  
## <a name="example"></a>Exemplo  
 O aplicativo persiste as propriedades do escopo do aplicativo e restaura-los do armazenamento isolado. Armazenamento isolado é uma área de armazenamento protegido que pode ser usada com segurança por aplicativos sem permissão de acesso de arquivo.  O *App. XAML* arquivo define a `App_Startup` método como o manipulador para o <xref:System.Windows.Application.Startup?displayProperty=nameWithType> evento e o `App_Exit` método como o manipulador para o <xref:System.Windows.Application.Exit?displayProperty=nameWithType> evento, conforme mostrado nas linhas realçadas do primeiro exemplo. O segundo exemplo mostra uma parte do *App.xaml.cs* e *VB* arquivos que destaca o código para o `App_Startup` método, que restaura as propriedades de escopo do aplicativo e o `App_Exit` método, que salva as propriedades de escopo do aplicativo.

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
