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
# <a name="how-to-use-special-characters-in-xaml"></a>Como usar caracteres especiais em XAML
Os arquivos de marcação criados no Visual Studio são salvos automaticamente no formato de arquivo UTF-8 Unicode, o que significa que a maioria dos caracteres especiais, como as marcas de acentuação, são codificados corretamente. No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de forma diferente. Esses caracteres especiais seguem o padrão XML de World Wide Web Consortium (W3C) para codificação.  
  
 A tabela a seguir mostra a sintaxe para codificar esse conjunto de caracteres especiais:  
  
|Caractere|Sintaxe|Descrição|  
|---------------|------------|-----------------|  
|<|`&lt;`|Menor que símbolo.|  
|>|`&gt;`|Sinal de maior que.|  
|&|`&amp;`|Símbolo de e comercial.|  
|"|`&quot;`|Símbolo de aspas duplas.|  
  
> [!NOTE]
> Se você criar um arquivo de marcação usando um editor de texto, como o bloco de notas do Windows, deverá salvar o arquivo no formato de arquivo Unicode UTF-8 para preservar os caracteres especiais codificados.  
  
 O exemplo a seguir mostra como você pode usar caracteres especiais no texto ao criar marcação.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
