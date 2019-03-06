---
title: 'Como: Usar caracteres especiais em XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 18934e06f45ca4b88f48bce8a310a07b460a5f53
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377957"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Como: Usar caracteres especiais em XAML
Arquivos de marcação que são criados no [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] são salvas automaticamente no [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] formato de arquivo UTF-8, o que significa que a maioria dos caracteres especiais, como marcas de ênfase, são codificados corretamente. No entanto, há um conjunto de caracteres especiais usados que são tratados de maneira diferente. Esses caracteres especiais seguem a [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] padrão de codificação.  
  
 A tabela a seguir mostra a sintaxe para a codificação deste conjunto de caracteres especiais:  
  
|Caractere|Sintaxe|Descrição|  
|---------------|------------|-----------------|  
|<|`&lt;`|Menor que o símbolo.|  
|>|`&gt;`|Sinal de maior que.|  
|&|`&amp;`|Símbolo de e comercial.|  
|"|`&quot;`|Símbolo de aspas duplas.|  
  
> [!NOTE]
>  Se você criar um arquivo de marcação usando um texto de editor, como [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] bloco de notas, você deve salvar o arquivo no [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] codificado de formato de arquivo UTF-8 para preservar os caracteres especiais.  
  
 O exemplo a seguir mostra como você pode usar caracteres especiais no texto durante a criação de marcação.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
