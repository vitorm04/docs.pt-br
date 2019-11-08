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
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740832"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="ffdde-102">Como usar caracteres especiais em XAML</span><span class="sxs-lookup"><span data-stu-id="ffdde-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="ffdde-103">Os arquivos de marcação criados no Visual Studio são salvos automaticamente no formato de arquivo UTF-8 Unicode, o que significa que a maioria dos caracteres especiais, como as marcas de acentuação, são codificados corretamente.</span><span class="sxs-lookup"><span data-stu-id="ffdde-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="ffdde-104">No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de forma diferente.</span><span class="sxs-lookup"><span data-stu-id="ffdde-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="ffdde-105">Esses caracteres especiais seguem o padrão XML de World Wide Web Consortium (W3C) para codificação.</span><span class="sxs-lookup"><span data-stu-id="ffdde-105">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="ffdde-106">A tabela a seguir mostra a sintaxe para codificar esse conjunto de caracteres especiais:</span><span class="sxs-lookup"><span data-stu-id="ffdde-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="ffdde-107">Caractere</span><span class="sxs-lookup"><span data-stu-id="ffdde-107">Character</span></span>|<span data-ttu-id="ffdde-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ffdde-108">Syntax</span></span>|<span data-ttu-id="ffdde-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffdde-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="ffdde-110">Menor que símbolo.</span><span class="sxs-lookup"><span data-stu-id="ffdde-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="ffdde-111">Sinal de maior que.</span><span class="sxs-lookup"><span data-stu-id="ffdde-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="ffdde-112">Símbolo de e comercial.</span><span class="sxs-lookup"><span data-stu-id="ffdde-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="ffdde-113">"</span><span class="sxs-lookup"><span data-stu-id="ffdde-113">"</span></span>|`&quot;`|<span data-ttu-id="ffdde-114">Símbolo de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="ffdde-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ffdde-115">Se você criar um arquivo de marcação usando um editor de texto, como o bloco de notas do Windows, deverá salvar o arquivo no formato de arquivo Unicode UTF-8 para preservar os caracteres especiais codificados.</span><span class="sxs-lookup"><span data-stu-id="ffdde-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="ffdde-116">O exemplo a seguir mostra como você pode usar caracteres especiais no texto ao criar marcação.</span><span class="sxs-lookup"><span data-stu-id="ffdde-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffdde-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ffdde-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
