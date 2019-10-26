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
# <a name="how-to-use-special-characters-in-xaml"></a>Como usar caracteres especiais em XAML
Os arquivos de marcação criados no Visual Studio são salvos automaticamente no formato de arquivo UTF-8 Unicode, o que significa que a maioria dos caracteres especiais, como as marcas de acentuação, são codificados corretamente. No entanto, há um conjunto de caracteres especiais comumente usados que são tratados de forma diferente. Esses caracteres especiais seguem o World Wide Web Consortium (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] Standard para codificação.  
  
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
