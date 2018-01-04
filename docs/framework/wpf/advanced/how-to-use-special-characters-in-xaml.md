---
title: Como usar caracteres especiais em XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79df87d716224cb8681c1688d94fe56077452c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="48687-102">Como usar caracteres especiais em XAML</span><span class="sxs-lookup"><span data-stu-id="48687-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="48687-103">Arquivos de marcação que são criados no [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] são salvas automaticamente no [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formato de arquivo UTF-8, o que significa que a maioria dos caracteres especiais, como marcas de ênfase são codificados corretamente.</span><span class="sxs-lookup"><span data-stu-id="48687-103">Markup files that are created in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] are automatically saved in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="48687-104">No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="48687-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="48687-105">Esses caracteres especiais seguem o [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] padrão de codificação.</span><span class="sxs-lookup"><span data-stu-id="48687-105">These special characters follow the [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)][!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="48687-106">A tabela a seguir mostra a sintaxe para a codificação deste conjunto de caracteres especiais:</span><span class="sxs-lookup"><span data-stu-id="48687-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="48687-107">Caractere</span><span class="sxs-lookup"><span data-stu-id="48687-107">Character</span></span>|<span data-ttu-id="48687-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48687-108">Syntax</span></span>|<span data-ttu-id="48687-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="48687-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`<`|<span data-ttu-id="48687-110">Menor que o símbolo.</span><span class="sxs-lookup"><span data-stu-id="48687-110">Less than symbol.</span></span>|  
|>|`>`|<span data-ttu-id="48687-111">Sinal de maior que.</span><span class="sxs-lookup"><span data-stu-id="48687-111">Greater than sign.</span></span>|  
|&|`&`|<span data-ttu-id="48687-112">Símbolo de e comercial.</span><span class="sxs-lookup"><span data-stu-id="48687-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="48687-113">"</span><span class="sxs-lookup"><span data-stu-id="48687-113">"</span></span>|`"`|<span data-ttu-id="48687-114">Símbolo de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="48687-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="48687-115">Se você criar um arquivo de marcação usando um texto de editor, como [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] bloco de notas, você deve salvar o arquivo no [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] codificado de formato de arquivo UTF-8 para preservar os caracteres especiais.</span><span class="sxs-lookup"><span data-stu-id="48687-115">If you create a markup file using a text editor, such as [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Notepad, you must save the file in the [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="48687-116">O exemplo a seguir mostra como você pode usar caracteres especiais em texto quando criar a marcação.</span><span class="sxs-lookup"><span data-stu-id="48687-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48687-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48687-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
