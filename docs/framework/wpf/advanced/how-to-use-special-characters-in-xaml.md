---
title: Como usar caracteres especiais em XAML
description: Saiba mais sobre a sintaxe para codificar caracteres especiais no formato de arquivo UTF-8 Unicode no Visual Studio para uso em arquivos XAML no Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: ac2388fd96aa26ddd99408ac9f847ce517958568
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168359"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="916cb-103">Como usar caracteres especiais em XAML</span><span class="sxs-lookup"><span data-stu-id="916cb-103">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="916cb-104">Os arquivos de marcação criados no Visual Studio são salvos automaticamente no formato de arquivo UTF-8 Unicode, o que significa que a maioria dos caracteres especiais, como as marcas de acentuação, são codificados corretamente.</span><span class="sxs-lookup"><span data-stu-id="916cb-104">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="916cb-105">No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de forma diferente.</span><span class="sxs-lookup"><span data-stu-id="916cb-105">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="916cb-106">Esses caracteres especiais seguem o padrão XML de World Wide Web Consortium (W3C) para codificação.</span><span class="sxs-lookup"><span data-stu-id="916cb-106">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="916cb-107">A tabela a seguir mostra a sintaxe para codificar esse conjunto de caracteres especiais:</span><span class="sxs-lookup"><span data-stu-id="916cb-107">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="916cb-108">Caractere</span><span class="sxs-lookup"><span data-stu-id="916cb-108">Character</span></span>|<span data-ttu-id="916cb-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="916cb-109">Syntax</span></span>|<span data-ttu-id="916cb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="916cb-110">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="916cb-111">Menor que símbolo.</span><span class="sxs-lookup"><span data-stu-id="916cb-111">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="916cb-112">Sinal de maior que.</span><span class="sxs-lookup"><span data-stu-id="916cb-112">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="916cb-113">Símbolo de e comercial.</span><span class="sxs-lookup"><span data-stu-id="916cb-113">Ampersand symbol.</span></span>|  
|<span data-ttu-id="916cb-114">"</span><span class="sxs-lookup"><span data-stu-id="916cb-114">"</span></span>|`&quot;`|<span data-ttu-id="916cb-115">Símbolo de aspas duplas.</span><span class="sxs-lookup"><span data-stu-id="916cb-115">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="916cb-116">Se você criar um arquivo de marcação usando um editor de texto, como o bloco de notas do Windows, deverá salvar o arquivo no formato de arquivo Unicode UTF-8 para preservar os caracteres especiais codificados.</span><span class="sxs-lookup"><span data-stu-id="916cb-116">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="916cb-117">O exemplo a seguir mostra como você pode usar caracteres especiais no texto ao criar marcação.</span><span class="sxs-lookup"><span data-stu-id="916cb-117">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="916cb-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="916cb-118">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
