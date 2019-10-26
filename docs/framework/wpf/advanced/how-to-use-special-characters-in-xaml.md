---
title: Como usar caracteres especiais em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 713428adc2e1576d1b95984b492fe84c042c0a09
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919637"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="3def3-102">Como usar caracteres especiais em XAML</span><span class="sxs-lookup"><span data-stu-id="3def3-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="3def3-103">Os arquivos de marcação criados no Visual Studio são salvos automaticamente no formato de arquivo UTF-8 Unicode, o que significa que a maioria dos caracteres especiais, como as marcas de acentuação, são codificados corretamente.</span><span class="sxs-lookup"><span data-stu-id="3def3-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="3def3-104">No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de forma diferente.</span><span class="sxs-lookup"><span data-stu-id="3def3-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="3def3-105">Esses caracteres especiais seguem o World Wide Web Consortium (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] Standard para codificação.</span><span class="sxs-lookup"><span data-stu-id="3def3-105">These special characters follow the World Wide Web Consortium (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="3def3-106">A tabela a seguir mostra a sintaxe para codificar esse conjunto de caracteres especiais:</span><span class="sxs-lookup"><span data-stu-id="3def3-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="3def3-107">Caractere</span><span class="sxs-lookup"><span data-stu-id="3def3-107">Character</span></span>|<span data-ttu-id="3def3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3def3-108">Syntax</span></span>|<span data-ttu-id="3def3-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3def3-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="3def3-110">Menor que símbolo.</span><span class="sxs-lookup"><span data-stu-id="3def3-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="3def3-111">Sinal de maior que.</span><span class="sxs-lookup"><span data-stu-id="3def3-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="3def3-112">Símbolo de e comercial.</span><span class="sxs-lookup"><span data-stu-id="3def3-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="3def3-113">"</span><span class="sxs-lookup"><span data-stu-id="3def3-113">"</span></span>|`&quot;`|<span data-ttu-id="3def3-114">Símbolo de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="3def3-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="3def3-115">Se você criar um arquivo de marcação usando um editor de texto, como o bloco de notas do Windows, deverá salvar o arquivo no formato de arquivo Unicode UTF-8 para preservar os caracteres especiais codificados.</span><span class="sxs-lookup"><span data-stu-id="3def3-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="3def3-116">O exemplo a seguir mostra como você pode usar caracteres especiais no texto ao criar marcação.</span><span class="sxs-lookup"><span data-stu-id="3def3-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3def3-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3def3-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
